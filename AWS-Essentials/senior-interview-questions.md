# Senior AWS Interview Guide — 8 Architecture Questions

> **Purpose:** an *interviewer's* guide. For each question you get the signal to listen for, a model
> answer at senior level, follow-up probes that separate "read the docs" from "ran it in production",
> and red flags.
>
> **Relationship to the other docs in this folder:**
> [transcripts-formatted.md](transcripts-formatted.md) and [interview-questions.md](interview-questions.md)
> cover the *foundational* layer (what each service is). This file covers the *design* layer (how you
> combine them, and what breaks). Where the transcripts do cover a service, the answer links back to it.
>
> **Accuracy note:** items marked **(verify)** are numbers, prices, quotas, or recent service changes
> that you should confirm against current AWS documentation before quoting them in an interview. AWS
> changes defaults and pricing frequently, and some of these are near or past my knowledge cutoff.
> They are collected in [Appendix B](#appendix-b--claims-to-verify-before-quoting).

---

## How to run the interview

**Do not ask all eight.** Each of these is a 10–15 minute conversation if answered properly. Pick 3–4
based on the role, and go deep with the follow-ups rather than broad across the list.

| Role shape | Ask these |
|---|---|
| Full-stack / front-end leaning cloud | Q3, Q4, Q6, Q5 |
| Platform / infra / SRE | Q1, Q2, Q4, Q8 |
| FinOps-sensitive / cost mandate | Q7, Q1, Q3 |
| Security-sensitive (regulated, PII) | Q2, Q5, Q8 |

**Technique that works:** ask the question, let them answer uninterrupted, then pick the *weakest*
concrete claim they made and probe it. Seniority shows in the second and third layer, not the first.
A candidate who says "multi-AZ for high availability" and a candidate who says "multi-AZ, and I size
each AZ to carry 50% so losing one doesn't brown out the other two" sound similar for ten seconds.

**Scoring rubric (applies to every question):**

| Level | What it sounds like |
|---|---|
| **Junior** | Names services correctly. "Use ALB and Auto Scaling." No trade-offs, no numbers, no failure modes. |
| **Mid** | Correct architecture, knows the config knobs, can draw it. Trade-offs appear when prompted. |
| **Senior** | Starts from requirements (RTO/RPO, SLO, budget), names the failure mode each control addresses, volunteers trade-offs and what they'd *not* do, and says how they verified it in production. |
| **Staff+** | All of the above plus organizational mechanics: how the control is enforced for teams other than their own, how it's tested continuously, what it costs, and what they got wrong last time. |

**The single strongest signal across all eight questions:** does the candidate ask *you* a clarifying
question before answering? "What's the RTO?" / "Is this multi-tenant?" / "Regulated data?" A senior
engineer knows these questions have no context-free answer.

---

## Q1 — Highly available and fault-tolerant architecture

**Question as asked:**
> How do you design a highly available and fault-tolerant architecture on AWS? Discuss your approach
> to using services like EC2, Load Balancers, Auto Scaling, and Route 53 for high availability.

### What you're listening for

- Do they distinguish **high availability** (survive component loss) from **fault tolerance**
  (survive it with no user-visible impact) from **disaster recovery** (survive losing a region)?
  Many candidates use the three interchangeably.
- Do they reason in **failure domains** — instance → AZ → region → control plane — or just list services?
- Do they mention **capacity headroom math**? This is the single most-skipped point.
- Do they know that **HA of the compute tier is the easy half**; state and dependencies are the hard half.
- Do they mention **static stability** — the failover path must not depend on making new API calls.
- Do they say how they *tested* it? An untested failover is a hypothesis.

### Model answer

**1. Start from the requirement, not the architecture.**

"Highly available" is not a design input; a number is. I want: target availability (99.9% ≈ 43 min
downtime/month, 99.99% ≈ 4.3 min/month), RTO, RPO, and whether degraded service counts as up. Those
numbers decide whether I need multi-AZ, multi-region, or just good backups — and they decide the
budget, because each nine roughly multiplies cost.

**2. Failure domains, from smallest to largest.**

| Domain | Blast radius | Control |
|---|---|---|
| Process / instance | One host | ASG health checks + replacement, ≥2 instances, stateless app tier |
| Availability Zone | One datacenter cluster | Resources spread across ≥3 AZs, multi-AZ data tier |
| Region | Everything in the region | Cross-region DR — see [Q8](#q8--disaster-recovery-and-backup) |
| Control plane | Can't *launch* new things | Static stability — pre-provisioned capacity |
| Dependency | Third-party API, DNS, auth | Timeouts, circuit breakers, cached fallbacks, graceful degradation |

**3. The compute tier.**

Stateless EC2 in an **Auto Scaling group spanning 3 AZs** behind an **Application Load Balancer**.
Specifics that matter:

- ALB is a regional service and requires subnets in **at least two AZs**; it scales itself, but scales
  *gradually* — for a known traffic spike (a launch, a sale) you pre-warm via a support request or
  front it with CloudFront. **(verify — current pre-warming guidance)**
- **Cross-zone load balancing**: on by default for ALB, off by default for NLB. If you leave it off on
  an NLB with uneven instance counts per AZ, you get uneven load. Turning it on for NLB incurs
  cross-AZ data transfer charges. **(verify — defaults have shifted; ALB can now disable it per target group)**
- ASG **health check type = ELB**, not just EC2. EC2 status checks only catch a dead hypervisor or
  kernel; ELB checks catch a wedged application that still answers ping. Set a **health check grace
  period** longer than boot+warmup, or the ASG kills instances mid-bootstrap in a loop.
- **Deregistration delay** (connection draining, default 300s) so in-flight requests finish on scale-in.
- **Instance refresh** with a minimum-healthy-percentage for rolling AMI/config rollouts; **lifecycle
  hooks** to drain gracefully; **warm pools** if boot time is long enough to hurt scale-out latency.

**4. Capacity math — the part most candidates skip.**

If I run 3 AZs and size each to exactly 33% of peak, losing one AZ means the remaining two are at
150% of their capacity — I've just converted an AZ failure into a full outage. So each AZ is sized to
carry **50%** of peak (3 AZs × 50% = 150% total, lose one → 100% available). That's the "N+1 across
AZs" rule. With only 2 AZs it's 2N — each AZ carries 100%, which is why 3 AZs is usually cheaper than
2 for the same resilience.

**5. Static stability.**

The failover path must not depend on the AWS control plane succeeding, because control planes are
exactly what degrades in a large event. Concretely: I *pre-provision* the replacement capacity rather
than relying on the ASG to launch new instances during the event. Scaling out during an AZ failure is
a best-effort optimization, not the plan. Same reasoning applies to relying on a fresh
`AssumeRole`/`DescribeX` call inside the recovery path.

**6. Scaling policy choice.**

Target tracking on the metric that actually reflects user pain — `RequestCountPerTarget` or ALB
latency, usually better than raw CPU for web tiers. Step scaling for known-shape bursts, scheduled
scaling for predictable business cycles, predictive scaling if the pattern is weekly and stable. And
a scale-*in* policy conservative enough not to thrash — cooldowns and a longer evaluation window on
scale-in than scale-out.

**7. The data tier is where HA actually lives.**

- **RDS Multi-AZ**: synchronous standby, automatic failover via DNS CNAME swap — typically on the
  order of 60–120 seconds **(verify)**. Multi-AZ *cluster* deployments (two readable standbys) offer
  faster failover than the classic single-standby setup **(verify)**.
- **Aurora**: storage layer replicates 6 ways across 3 AZs; failover promotes a replica, typically
  much faster than RDS Multi-AZ **(verify current numbers)**. Applications must use the **cluster
  endpoint** and the reader endpoint, never a hardcoded instance endpoint.
- **RDS Proxy** in front of either, especially with Lambda: it pools connections and holds them across
  a failover, which shortens the client-visible outage and prevents a connection storm on recovery.
- Client-side: JDBC/driver-level **connection validation and short DNS TTL respect**. A Java app that
  caches the DNS resolution forever will stay pointed at the dead primary long after AWS finished
  failing over. That's a real and very common incident cause.
- **DynamoDB** is multi-AZ by design — no HA work needed inside a region.

**8. Route 53's actual role.**

Inside one region, Route 53 is not doing HA work — the ALB is. Route 53 matters for:

- **Failover routing** with health checks, for region-level or origin-level failover.
- **Latency-based** or **geoproximity** routing for multi-region active/active.
- **Weighted** routing for canary traffic shifting and for gradual migration.
- **Multivalue answer** routing when you want several healthy IPs returned.
- Health checks poll from multiple global locations (standard 30s interval, 10s fast) **(verify)**.
  Important limitation: Route 53 health checks come from the public internet, so they **can't check a
  private endpoint** — for that you attach a **CloudWatch alarm–based** health check instead.
- **TTL discipline**: failover is only as fast as the TTL plus client caching. 60s TTL on failover
  records. And be honest in the interview that DNS failover is *never* instant — some clients and
  resolvers ignore TTLs. If you need sub-DNS failover, **Global Accelerator** gives you static anycast
  IPs and shifts traffic at the network layer without waiting on DNS.

**9. Application-level fault tolerance** (the part that isn't AWS config):

Timeouts on every remote call with a per-request budget; retries with **exponential backoff and
jitter** (retries without jitter cause synchronized retry storms); **idempotency keys** so retries are
safe; circuit breakers; bulkheads so one slow dependency can't exhaust the whole thread/connection
pool; and designed **graceful degradation** — e.g., serve stale cache and hide the recommendations
widget rather than 500 the whole page. As a front-end architect I'd add: the UI should have a defined
degraded state per dependency, not a generic error boundary.

**10. How I prove it works.**

- **Game days**: deliberately evacuate an AZ in a pre-prod environment that mirrors prod, on a schedule.
- **AWS Fault Injection Service** (FIS) for repeatable experiments — instance termination, API error
  injection, and an AZ power-interruption scenario **(verify — FIS was renamed from Fault Injection
  Simulator, and scenario availability changes)**.
- Force an **RDS failover** (`reboot with failover`) in a load test and *measure* the client-visible
  gap. This is how you discover the DNS caching bug above.
- **Synthetic canaries** (CloudWatch Synthetics) running the critical user journey from outside, so
  availability is measured the way users experience it, not by whether instances are `running`.
- Alarm on **healthy host count per AZ** — the leading indicator that you're one AZ from an outage.

### Follow-up probes

| Probe | What a good answer says |
|---|---|
| "You have 2 AZs, 4 instances, each at 60% CPU. An AZ fails. What happens?" | The 2 survivors go to ~120% — they're saturated. Either overprovision or accept degradation. Tests whether the capacity math is real to them. |
| "Multi-AZ RDS — is the standby serving reads?" | Not in the classic Multi-AZ single-standby setup; it's a passive synchronous replica for HA only. Read scaling needs read replicas (async, so replica lag matters for read-after-write). Multi-AZ cluster deployments do have readable standbys **(verify)**. |
| "Your ALB is healthy, ASG is healthy, but users get errors. Where do you look?" | Downstream: DB connection pool exhaustion, dependency latency, target group health check path being too shallow (a `/health` that returns 200 without checking the DB is a classic). |
| "Does an ASG protect you from a bad deploy?" | No — it will happily maintain N broken instances. Deploy safety comes from canary/blue-green plus rollback on alarm, not from the ASG. Strong differentiator question. |
| "Why 3 AZs and not 2?" | Cheaper headroom (50% vs 100% per AZ), and quorum-based systems need 3 to survive one loss. |
| "What's the availability of a system with 3 dependencies at 99.9% each?" | Roughly 99.7% if all are hard dependencies — availability multiplies. Leads to the insight that reducing hard dependencies buys more than adding redundancy. |

### Red flags

- "Auto Scaling gives you high availability." Auto Scaling gives you *capacity*; it can leave you at
  N unhealthy instances.
- Treating Route 53 as the in-region HA mechanism.
- Never mentioning the database or state.
- No number anywhere in the answer.
- Claiming zero downtime without mentioning DNS TTL, connection draining, or client retries.

### Docs coverage

Foundational only: [§3.6 Auto Scaling](transcripts-formatted.md#36-auto-scaling) ·
[§3.9 Elastic Load Balancer (ELB)](transcripts-formatted.md#39-elastic-load-balancer-elb) ·
[§5.1 Regions & Availability Zones](transcripts-formatted.md#51-aws-global-services--regions--availability-zones) ·
[§5.7 Availability Zones Inside a VPC](transcripts-formatted.md#57-availability-zones-inside-a-vpc) ·
[§5.8 Route 53](transcripts-formatted.md#58-route-53)

**Gap:** capacity headroom math, static stability, health-check semantics, failover measurement,
Global Accelerator, FIS. None of this is in the transcripts.

---

## Q2 — Security across multiple AWS services

**Question as asked:**
> How do you ensure security across multiple AWS services? Explain your use of IAM roles and policies,
> VPC security groups, NACLs, AWS KMS, and encryption strategies.

### What you're listening for

- **Layers**, in order: identity → network → data → detection. A candidate who jumps straight to
  security groups is thinking like a sysadmin; identity is the primary perimeter in cloud.
- Do they know **IAM policy evaluation logic** (the intersection, and explicit-deny precedence)?
- Do they use **roles and short-lived credentials** everywhere, and can they say *why* long-lived
  access keys are the top real-world breach vector?
- **KMS**: do they understand envelope encryption and that the **key policy** is the root of trust?
- Do they mention **detection and continuous verification**, not just preventive config?
- Organizational scale: SCPs, permission boundaries, guardrails for teams they don't control.

### Model answer

**Layer 1 — Identity (the real perimeter).**

- **No IAM users with long-lived access keys** for humans or workloads. Humans get federated SSO (IAM
  Identity Center / your IdP) which vends short-lived STS credentials. Workloads get **IAM roles**:
  instance profiles on EC2, execution roles on Lambda, task roles on ECS, IRSA or **EKS Pod Identity**
  on EKS, **IAM Roles Anywhere** for on-prem, and **OIDC federation** for CI (GitHub Actions assumes a
  role — no stored AWS keys in the CI system). Leaked static keys in a git repo are still one of the
  most common causes of real AWS compromise.
- **Least privilege built empirically, not aspirationally**: start broad in dev, then use **IAM Access
  Analyzer policy generation from CloudTrail** and **Access Advisor** (last-accessed data) to cut it
  down. Writing least privilege from scratch produces either broken apps or `Action: *` with a
  comment promising to fix it later.
- **Know the evaluation logic.** Effective permission = the intersection of: SCP (org guardrail) ∩
  identity policy ∩ permission boundary ∩ session policy ∩ (for cross-account, also the resource
  policy) — and **any explicit `Deny` anywhere wins**. Resource Control Policies (RCPs) add an
  org-wide guardrail on the resource side **(verify — relatively recent addition, ~late 2024)**.
- **Conditions are where real security lives**, not in the action list:
  - `aws:PrincipalOrgID` — only principals from my org can touch this resource.
  - `aws:SourceVpce` / `aws:SourceVpc` — only via my VPC endpoint.
  - `aws:SecureTransport: false` → Deny — no plaintext HTTP to S3.
  - `aws:SourceArn` / `aws:SourceAccount` — **confused-deputy** protection on any policy trusting an
    AWS service principal.
  - `sts:ExternalId` — mandatory when granting a third party (vendor, SaaS monitoring) access.
  - `kms:ViaService` — this key may only be used *through* S3, not by a human calling `Decrypt`.
  - This bundle is what AWS calls a **data perimeter**: my identities can only reach my resources,
    from my networks.
- **Permission boundaries** so a team can create roles (needed for velocity) without being able to
  escalate past a ceiling. **SCPs** at the org level for absolutes: deny leaving the org, deny
  disabling CloudTrail/GuardDuty, deny unapproved regions, deny root usage.
- **Root account**: MFA'd hardware key, no access keys, alarmed on any use.

**Layer 2 — Network.**

- **Security groups** are stateful and allow-only. The senior habit is **SG-to-SG references** rather
  than CIDRs: the app tier SG allows 5432 *from the web tier SG*, so the rule stays correct as
  instances come and go. CIDR-based rules rot.
- **NACLs** are stateless, ordered, and support explicit `Deny`. Because they're stateless you must
  allow the **ephemeral port range** (1024–65535) for return traffic — the single most common NACL
  mistake. I use NACLs for coarse subnet-level blocks (block a hostile CIDR, hard-separate tiers), not
  for day-to-day access control. SGs are the primary tool; NACLs are the backstop.
- Private subnets by default; egress via **NAT Gateway** only where genuinely needed; **VPC
  endpoints** (gateway endpoints for S3/DynamoDB, interface endpoints for the rest) so traffic to AWS
  APIs never traverses the internet — this is both a security control and a significant NAT cost
  saving, see [Q7](#q7--cost-optimization).
- **Endpoint policies** on those endpoints, so even a compromised instance can only reach *my* buckets
  through them — this is what blocks exfiltration to an attacker's S3 bucket.
- Edge: **CloudFront + AWS WAF** (managed rule groups, rate-based rules), **Shield Advanced** if the
  threat model warrants it, **ALB mTLS** for machine-to-machine **(verify)**. TLS terminated with
  **ACM** certs (auto-renewing).
- **IMDSv2 enforced** (`HttpTokens: required`). IMDSv1 is SSRF-exploitable to steal instance role
  credentials — this was the mechanism in several well-known breaches, and it's a one-line fix that
  many organizations still haven't applied.

**Layer 3 — Data / KMS.**

- **Envelope encryption**: KMS holds the key-encryption key (CMK); the service generates a data key,
  encrypts your data with it, and stores the KMS-encrypted data key alongside. This is why KMS scales
  — it never sees your data.
- **Key policy is authoritative.** Unlike almost everything else in AWS, an IAM policy alone does not
  grant KMS access — the key policy must delegate to IAM (`Principal: <account root>` +
  `kms:*` scoped, then IAM grants specifics) or grant directly. Candidates who don't know this
  produce the classic "I have `kms:Decrypt` in my role but still get AccessDenied".
- **AWS-managed vs customer-managed keys**: customer-managed when I need my own key policy, my own
  rotation schedule, cross-account sharing, or an audit story ("who can decrypt this data" must be
  answerable from one document). AWS-managed keys are free but you can't control their policy.
- **Rotation**: annual automatic rotation for customer-managed keys, with configurable periods
  **(verify — custom rotation periods are a newer capability)**. Important nuance: rotation creates
  new key *material* and keeps old material for decrypting old data — it does not re-encrypt anything,
  so rotation alone is not remediation for a suspected key compromise.
- **Grants** for temporary, programmatic delegation; **multi-Region keys** when a DR region must
  decrypt the same ciphertext without a round trip — relevant to [Q8](#q8--disaster-recovery-and-backup),
  because a cross-region snapshot copy re-encrypts with a key that must exist in the target region.
- **Encryption at rest, everywhere, by default:** S3 (SSE-S3 is applied to new objects by default now;
  SSE-KMS where I need auditable per-key control, with **S3 Bucket Keys** enabled to cut KMS request
  volume and cost dramatically **(verify the exact reduction claim)**), EBS (account-level "encrypt by
  default" so nobody can forget), RDS/Aurora (must be set at creation — you cannot encrypt an existing
  unencrypted instance in place; you snapshot, copy-with-encryption, restore), DynamoDB (encrypted
  always), and CloudWatch Logs / SNS / SQS / Kinesis with CMKs where the data is sensitive.
- **In transit**: TLS 1.2+ enforced; deny `aws:SecureTransport: false`; internal service-to-service TLS
  too, not just at the edge.
- **S3 specifically**: Block Public Access at the *account* level, bucket policies with
  `aws:PrincipalOrgID`, **OAC** for CloudFront (OAI is legacy), versioning + Object Lock for anything
  that must be tamper-evident.

**Layer 4 — Detection and continuous verification.** Preventive controls drift; detection is what
tells you they did.

- **CloudTrail** — organization trail, multi-region, log file validation on, delivered to a
  **separate, locked-down log-archive account** so an attacker with prod admin still can't erase the
  evidence. That account separation is the whole point.
- **GuardDuty** (threat detection from CloudTrail/VPC Flow/DNS logs), **Security Hub** (aggregated
  findings + CIS/AWS Foundational Security Best Practices scoring), **AWS Config** (resource
  configuration history + rules like "no unencrypted EBS", with auto-remediation), **IAM Access
  Analyzer** (finds resources reachable from outside the org — the "public S3 bucket" detector — plus
  unused-access findings), **Macie** for discovering PII that ended up somewhere it shouldn't.
- **Shift left**: policy-as-code in CI (Checkov / tfsec / cfn-guard / CDK Aspects), Access Analyzer
  **custom policy checks** in the pipeline to fail a PR that broadens permissions, secret scanning
  pre-commit and in CI.

**How I verify it.**

IAM policy unit tests via the **policy simulator** and Access Analyzer custom policy checks in CI;
red-team/pen-test the SSRF and public-exposure paths; deliberately create a violating resource and
confirm Config/Security Hub alerts fire (testing the *detector*, not just the control); track
"time-to-detect" as a metric; regular access reviews driven by Access Advisor's unused-permission data.

### Follow-up probes

| Probe | What a good answer says |
|---|---|
| "My role has `s3:GetObject` on the bucket. I get AccessDenied. Why?" | Bucket policy explicit deny, SCP, permission boundary, missing `kms:Decrypt` for the bucket's CMK, VPC endpoint policy, or Block Public Access. Watch them enumerate the evaluation chain — that's the whole question. |
| "SG allows it, NACL denies it. Result?" | Blocked. NACL is evaluated at the subnet boundary; both must permit. Basic, but a fast filter. |
| "Why prefer SG-to-SG over CIDR rules?" | Rules stay correct as IPs churn; expresses intent (tier-to-tier) rather than topology. |
| "Difference between an IAM policy and a KMS key policy?" | Key policy is the root of trust for the key and must delegate to IAM; IAM alone is insufficient. |
| "Key rotation happened. Is old data re-encrypted?" | No. Old material is retained for decryption. Rotation ≠ remediation of a compromise. |
| "How do you stop a developer from creating an admin role?" | Permission boundary + SCP; not code review. |
| "How does CI get AWS credentials?" | OIDC role assumption, no stored keys. If they say "store the access key in CI secrets", that's a mid-level answer in 2026. |
| "You suspect an instance role was used from outside. What do you do?" | CloudTrail query on the role's session, revoke sessions (`AWSRevokeOlderSessions` policy / attach a deny with `aws:TokenIssueTime`), rotate, snapshot for forensics, check GuardDuty findings, then fix IMDSv2. |

### Red flags

- Security groups as the whole answer.
- Long-lived IAM access keys for applications or CI.
- "We encrypt everything with KMS" with no idea what a key policy is.
- No detection layer — all preventive, no verification.
- Can't state the explicit-deny precedence rule.

### Docs coverage

Partial: [§2.3 Users, Groups, Policies](transcripts-formatted.md#23-creating-users-groups-and-policies) ·
[§2.4 IAM Roles](transcripts-formatted.md#24-establishing-iam-roles) ·
[§3.5 Security Groups](transcripts-formatted.md#35-security-groups) ·
[§5.5 NACLs](transcripts-formatted.md#55-network-access-control-lists-nacls) ·
[§4.4 S3 Permissions](transcripts-formatted.md#44-s3-permissions) ·
[§8.5 CloudTrail](transcripts-formatted.md#85-cloudtrail) ·
[§9.2 GuardDuty](transcripts-formatted.md#92-guardduty) ·
[§9.3 Security Hub](transcripts-formatted.md#93-aws-security-hub)

**Gap: KMS is entirely absent from the transcripts.** Also missing: policy evaluation logic, SCPs,
permission boundaries, condition keys, IMDSv2, VPC endpoint policies, Access Analyzer, Config rules.

---

## Q3 — Scalable and cost-efficient serverless architecture

**Question as asked:**
> How do you architect a scalable and cost-efficient application on AWS? Talk about using services
> like AWS Lambda, API Gateway, S3, RDS/Aurora, and DynamoDB to create serverless architectures.

### What you're listening for

- Do they know **when *not* to go serverless**? Unconditional serverless enthusiasm is a mid-level tell.
- **Lambda + relational DB** is the classic trap. Do they raise connection exhaustion unprompted?
- **DynamoDB data modeling from access patterns** — the single biggest differentiator on this question.
- Cold starts: do they know what actually causes them and the real mitigations?
- Do they attach **numbers** — request volume, p99 latency target, cost per million?

### Model answer

**1. Serverless is a cost *shape*, not a cost *level*.**

Lambda is pay-per-invocation with zero idle cost, so it wins decisively for spiky, low-duty-cycle, or
unpredictable workloads. For steady, high-throughput traffic, a right-sized Fargate or EC2 fleet is
usually cheaper per request. The honest engineering answer: serverless buys me *operational* leverage
(no patching, no capacity planning, per-request scaling) and I'll pay a compute premium for it at high
steady volume. I'd model the crossover rather than pick by ideology. Also worth saying out loud:
serverless usually wins hardest on **cost of engineering time**, not cost of compute.

**2. The shape I'd default to.**

```
Route 53 → CloudFront (+ WAF) ──► S3 (SPA static assets, OAC)
                              └─► API Gateway (HTTP API) → Lambda → DynamoDB
                                                              │
                                                              ├─► EventBridge / SQS  (async fan-out)
                                                              └─► RDS Proxy → Aurora (relational needs)
```

Static front-end on S3 behind CloudFront — that's the cheapest, most scalable tier in AWS and, as a
front-end architect, where I'd start: hashed asset filenames with `Cache-Control: immutable`, short
TTL on `index.html`, so deploys never require a full invalidation.

**3. API Gateway choices.**

- **HTTP API vs REST API**: HTTP API is substantially cheaper and lower latency; REST API has the
  extra features — request/response transformation, API keys and usage plans, response caching,
  WAF attachment, private endpoints. Pick HTTP API unless you need one of those **(verify the current
  feature matrix — AWS keeps closing the gap)**.
- REST APIs historically cap integration timeout at **29 seconds** (raisable via quota in more recent
  versions) **(verify)** — so long jobs go async: return `202` with a job ID, do the work in
  Step Functions or SQS+Lambda, and let the client poll or receive a WebSocket/webhook push.
- **Direct service integrations** where possible — API Gateway straight to DynamoDB/SQS/Step Functions
  with no Lambda in between. Less code, less latency, no cold start, cheaper. Senior candidates
  volunteer this; juniors put Lambda everywhere.
- Throttling and usage plans as a **cost control**, not just an abuse control: an unthrottled
  pay-per-request API is an unbounded bill.
- Authn/authz at the edge: JWT authorizer (Cognito/OIDC) on HTTP API, or a Lambda authorizer with
  caching. Never inside the business-logic function.
- Alternative worth naming: **ALB → Lambda**, or **Lambda function URLs** + CloudFront, when you don't
  need API Gateway's features — noticeably cheaper at volume.

**4. Lambda, the parts that matter.**

- **Concurrency model**: one execution environment handles exactly one event at a time; scale = more
  environments. So your concurrency is `RPS × avg duration`. This is the calculation to do *before*
  deploying, because it also tells you your downstream connection count.
- **Memory is the CPU dial** — vCPU scales with configured memory (~1,769 MB ≈ 1 vCPU **(verify)**).
  A CPU-bound function at 512 MB can be *cheaper* at 1,024 MB because it finishes in less than half
  the time. Use **Lambda Power Tuning** to find the cost/latency optimum rather than guessing —
  concrete, measurable, and a strong signal when a candidate names it.
- **arm64/Graviton** — better price-performance for most workloads at a lower per-GB-second price
  **(verify current percentages)**. Nearly free win for interpreted runtimes.
- **Cold starts**: driven by package size, runtime, VPC-attached ENI setup (much improved since the
  2019 networking change), and heavy module-init work. Mitigations in order of preference: shrink the
  bundle and lazy-load, move init out of the handler path (but *do* reuse clients across invocations
  via module scope), **SnapStart** for JVM and now some other runtimes **(verify)**, and
  **provisioned concurrency** only when a latency SLO genuinely requires it — it reintroduces a fixed
  cost, so it's the last resort, and it pairs with Application Auto Scaling on a schedule.
- **Reserved concurrency** does double duty: caps a function's blast radius on the database *and*
  guarantees it capacity against noisy neighbours in the same account.
- Payload limits (6 MB synchronous, 256 KB async **(verify)**) and 15-minute max duration are
  architectural constraints — large payloads go via S3 presigned URLs with the pointer in the event.
- **Idempotency is mandatory**, not optional: async invocations retry, SQS redelivers, EventBridge
  retries. At-least-once delivery is the contract. Powertools' idempotency utility + a DynamoDB table
  is the standard implementation.

**5. Data tier — the actual architecture decision.**

**DynamoDB when** the access patterns are known and bounded. Then:
- Model **from access patterns backwards**, single-table where it fits, composite sort keys, GSIs for
  secondary patterns (GSIs are eventually consistent and separately provisioned — a GSI throttle
  throttles writes to the base table, which surprises people).
- **Partition key must spread**. Per-partition limits (~3,000 RCU / 1,000 WCU **(verify)**) mean a hot
  key throttles you no matter what the table-level capacity is. Write sharding or a
  higher-cardinality key for hot tenants.
- **On-demand vs provisioned + auto scaling**: on-demand for unpredictable/new workloads and dev;
  provisioned with auto scaling is cheaper once utilization is sustained and predictable. Model the
  crossover for your actual traffic shape rather than quoting a rule of thumb.
- **DAX** for read-heavy microsecond needs; **TTL** to expire data for free (deletes don't consume
  WCU); **Streams** for change-data-capture into search, analytics, or cache invalidation.
- Cost traps: transactions cost roughly double, `Scan` is the enemy, and storing large blobs in items
  (400 KB max) instead of S3.

**Aurora / RDS when** you need joins, ad-hoc queries, transactions across entities, or a schema that
will change in ways you can't predict — which is most line-of-business software, honestly.
- **Aurora Serverless v2** for spiky or dev/test workloads: scales ACUs in place, fine-grained,
  and can scale to a very low floor (with auto-pause options in newer versions) **(verify)**.
- **RDS Proxy is non-negotiable with Lambda.** 1,000 concurrent Lambdas will open 1,000 connections
  and kill a Postgres instance. The proxy pools and multiplexes, and also smooths failover. If a
  candidate designs Lambda→RDS without mentioning this, probe it — it's the most common real-world
  serverless outage in my experience.
- **Aurora I/O-Optimized** vs standard: worth switching when I/O charges dominate the cluster bill
  **(verify the documented breakeven)**.

**Polyglot is the right answer.** DynamoDB for the high-volume session/event path, Aurora for
relational reporting, S3 + Athena for cold analytics, ElastiCache for hot lookups. Choosing one
database for everything is the mid-level answer.

**6. Async and decoupling** — where serverless earns its keep. EventBridge for event routing and
fan-out with schema discovery; SQS for load-leveling and back-pressure (plus a **DLQ**, always, and
`maxReceiveCount` tuned to the real retry semantics); Step Functions for orchestration with
**Express** workflows for high-volume short flows and **Standard** for long-running auditable ones.
Batch size and `maxConcurrency` on SQS event sources are the knobs that protect a downstream database.

**7. How I'd test and prove it.**

- Contract tests against real AWS resources in **ephemeral per-PR environments** (CDK/SAM deploy of a
  full stack) — local emulators (SAM local, LocalStack) are useful for iteration speed but they lie
  about IAM, throttling, and latency, so they can't be the last gate.
- **Load test to the failure point**, not to the expected load — then look for what broke first
  (usually the database connection count or a partition hot key).
- Distributed tracing (**X-Ray** or OTel via ADOT) with Powertools; **structured logs** with
  correlation IDs.
- **Cost per request** as a tracked metric in the dashboard next to latency. That's what makes
  "cost-efficient" a claim rather than an aspiration.

### Follow-up probes

| Probe | What a good answer says |
|---|---|
| "5,000 Lambdas concurrently hitting Aurora. What happens?" | Connection exhaustion → errors → retry storm. Fix: RDS Proxy, reserved concurrency, SQS buffering, or don't put a relational DB there. **The best single probe in this question.** |
| "When is serverless the wrong choice?" | Steady high throughput; latency SLOs below cold-start tolerance; long-running or CPU-saturating jobs; heavy vendor-lock concerns; workloads needing >15 min or specialized hardware. Refusal to name any case is a red flag. |
| "You need a query the DynamoDB keys don't support." | GSI if it's a real ongoing pattern; Streams → OpenSearch/Athena for ad-hoc; accept that "I modelled the wrong access pattern" sometimes means a migration. Honest answer beats a clever one. |
| "Function is at 512 MB and slow. Cheaper to lower memory?" | Usually the opposite — raising memory raises CPU and can lower total cost. Power Tuning answers it empirically. |
| "How do you keep the same Lambda from being invoked twice for one order?" | Idempotency key persisted in DynamoDB with a conditional write; at-least-once is the delivery guarantee. |
| "How do you cache?" | Layered: CloudFront at the edge, API Gateway response cache (REST), DAX/ElastiCache for data, and in-memory reuse across warm invocations. Plus a coherent invalidation story. |

### Red flags

- Lambda + RDS with no connection-pooling concern.
- "DynamoDB scales infinitely" with no partition-key discussion.
- Provisioned concurrency as the first answer to cold starts.
- Lambda as glue in front of every service where a direct integration exists.
- No cost model — "serverless is cheaper" as an article of faith.

### Docs coverage

Thin: [§8.9 Lambda Basics](transcripts-formatted.md#89-lambda-basics) ·
[§6.2 RDS Basics](transcripts-formatted.md#62-rds-basics) ·
[§6.3 DynamoDB Basics](transcripts-formatted.md#63-dynamodb-basics) ·
[§4.2 S3 Basics](transcripts-formatted.md#42-s3-basics) ·
[§9.1 CloudFront](transcripts-formatted.md#91-overview--secrets-manager--cloudfront)

**Gap: API Gateway and Aurora do not appear in the transcripts at all.** Also missing: concurrency
model, cold starts, DynamoDB modeling, RDS Proxy, EventBridge/SQS/Step Functions.

---

## Q4 — Monitoring, logging, and alerting in a distributed environment

**Question as asked:**
> How do you handle monitoring, logging, and alerting in a distributed AWS environment? Explain your
> use of CloudWatch, CloudTrail, and third-party tools like Datadog, along with monitoring EC2
> instances, Lambda functions, and containers.

### What you're listening for

- **Alert on symptoms, not causes.** Do they connect alerting to SLOs and user impact, or do they
  alert on CPU? This is the crispest senior/mid divide in the whole list.
- Do they treat **observability cost** as a design constraint? Observability bills routinely reach
  10–30% of infra spend, and unbounded log ingestion is how.
- Do they know **CloudWatch's actual gaps** (memory and disk on EC2 need the agent) rather than
  assuming it's all there?
- **Correlation**: traces + logs + metrics tied by a request ID across service boundaries.
- Do they mention **runbooks and on-call ergonomics**, not just alarm creation? Alert fatigue is an
  availability problem.
- Front-end/real-user monitoring — often missing entirely, and it's where the user's actual
  experience lives.

### Model answer

**1. Start from what I owe the user: SLIs and SLOs.**

For each critical journey I define an SLI (availability = fraction of successful requests; latency =
fraction under p99 target) and an SLO. Then **page only on SLO burn rate** — multi-window, e.g. a fast
burn (2% of budget in an hour) pages, a slow burn (10% in a day) opens a ticket. Everything else is a
dashboard or a ticket, not a page. This is what stops the 3 a.m. "CPU is 85%" page for a system that
is serving users perfectly.

Three tiers, deliberately: **page** (user impact now, human action required, runbook attached),
**ticket** (degradation, fix in business hours), **dashboard/log** (diagnostic context, no
notification). If everything is a page, nothing is.

**2. Metrics.**

- CloudWatch as the substrate. **Embedded Metric Format (EMF)** from Lambda and containers — you write
  structured JSON to logs and CloudWatch extracts metrics, which avoids a synchronous
  `PutMetricData` call on the request path and gives you high-cardinality dimensions cheaply.
- **What's missing by default**: EC2 does **not** report memory or disk utilization — those are guest
  metrics requiring the **CloudWatch Agent** (unified agent, config in SSM Parameter Store, deployed
  by Systems Manager). Candidates who don't know this have not actually operated EC2.
- **Composite alarms** to collapse a cascade into one page; **anomaly detection** for metrics with
  daily/weekly seasonality where a static threshold is wrong; **metric math** for derived SLIs
  (error rate = 5xx / requests, not raw 5xx count — raw counts break at every traffic change).
- Alarm hygiene: `M out of N` datapoints to survive a single blip, and an explicit
  **missing-data policy** (`notBreaching` vs `breaching`) — the default silently hides dead-service
  cases, which is exactly when you want to know.
- **Per-service golden signals** (RED: rate, errors, duration for services; USE: utilization,
  saturation, errors for resources) instead of ad-hoc metrics per team.

**3. Logs.**

- Structured JSON everywhere, with a **correlation ID** propagated across every hop (Powertools does
  this for Lambda; trace header propagation for services).
- **Retention is set explicitly on every log group.** CloudWatch Logs defaults to never-expire, and
  that default alone accounts for a surprising share of wasted spend. Short retention hot (14–30 days
  for interactive debugging), then subscription filter → Firehose → **S3** in Parquet for long-term,
  queried with Athena at a fraction of the cost. **Infrequent Access log class** for
  high-volume/low-query logs **(verify)**.
- **CloudWatch Logs Insights** for interactive investigation; saved queries as part of runbooks.
- **Ingestion is the cost driver** — debug logging left on in production is the classic bill spike.
  Sample high-volume success paths, log failures in full.

**4. Traces.**

X-Ray or OpenTelemetry via **ADOT**. My preference is OTel instrumentation for portability (you can
change backends without re-instrumenting) with X-Ray or Datadog as the backend. Traces are what turn
"the checkout is slow" into "the tax-service call is 800 ms at p99 because of a missing index" in one
step instead of an hour of log grepping. Sampling: keep all errors and slow traces, sample the
successful ones.

**5. Per-workload specifics.**

| Workload | What I add |
|---|---|
| **EC2** | CloudWatch Agent (memory, disk, custom app metrics), SSM for fleet-wide config, ASG group metrics enabled, alarm on **healthy host count per AZ** and per-target-group 5xx |
| **Lambda** | Errors, Throttles, Duration (p99 not average), **ConcurrentExecutions vs account limit**, IteratorAge for stream sources, **DLQ depth** — an unmonitored DLQ is silent data loss. Lambda Insights or the Datadog extension for enhanced metrics |
| **Containers (ECS/EKS)** | Container Insights, or Prometheus/AMP + Grafana on EKS; task/pod-level CPU-memory *and* the ECS service events log; alarm on task restart loops and pending-task counts, which cluster-level CPU hides |
| **ALB** | `TargetResponseTime`, `HTTPCode_ELB_5XX` (the LB's own errors) *separately* from `HTTPCode_Target_5XX`, `RejectedConnectionCount`, `UnHealthyHostCount` |
| **RDS/Aurora** | Enhanced Monitoring + **Performance Insights** (top SQL by wait), `DatabaseConnections` against `max_connections`, replica lag, `FreeableMemory`, burst balance on gp2 |
| **Front-end** | **CloudWatch RUM** or Datadog RUM: Core Web Vitals (LCP/INP/CLS), JS error rate with uploaded source maps, API latency *as the browser sees it* — which is the only number that matches the user's experience |
| **Synthetic** | CloudWatch Synthetics canaries running the critical journey from multiple regions, alarmed. Catches "healthy infrastructure, broken user journey" |

**6. CloudTrail — audit, not monitoring.** Different purpose from CloudWatch and worth saying so
explicitly: CloudTrail answers "who did what to the AWS API", CloudWatch answers "how is the system
behaving". Organization trail, multi-region, to a locked separate account, log file validation on.
**Data events** (S3 object-level, Lambda invoke) are off by default and can be very expensive at
volume — enable selectively on sensitive buckets. **CloudTrail Lake** or Athena for querying. Alarm on
security-relevant events: root login, IAM policy changes, security-group changes, CloudTrail itself
being stopped, KMS key deletion scheduled.

**7. Where a third-party tool like Datadog earns its cost.**

CloudWatch is deep per-service but weak at cross-service correlation, cross-account/cross-region
dashboards, long retention, and hybrid or multi-cloud. Datadog (or New Relic/Grafana Cloud/Honeycomb)
gives one pane, unified tagging, APM tied to infra metrics and logs, and much better incident
workflow. Integration mechanics worth knowing:

- Read-only **IAM role with an ExternalId** for the AWS integration (not access keys).
- **CloudWatch Metric Streams → Firehose → Datadog** rather than API polling: lower latency
  (near-real-time vs polling interval) and it avoids `GetMetricData` API charges, which at scale is a
  genuine line item.
- Datadog **Lambda extension/layer** for traces and custom metrics without a CloudWatch round trip.
- **Cost governance is the main risk**: Datadog bills on hosts, custom metrics (cardinality!), indexed
  logs, and APM spans. So: log **exclusion filters** with archive-to-S3 (keep everything, index a
  fraction), aggressive control over high-cardinality tags, and someone owning that bill. I've seen
  observability spend exceed the compute it was watching.
- Non-negotiable prerequisite either way: a **standard tag taxonomy** (`service`, `env`, `team`,
  `version`) applied by IaC and enforced by tag policies. Without it, no tool can correlate anything —
  and the same taxonomy is what makes cost allocation work in [Q7](#q7--cost-optimization).

**8. How I test the monitoring itself.** Alarms are code — they get reviewed and deployed via IaC.
Then: inject a fault (FIS, or just break a canary dependency in staging) and confirm the page fires
and reaches the on-call; run **game days** where the responder must use only the dashboards and
runbook; track **MTTD/MTTA/MTTR** and use post-incident reviews to add the *one* signal that would
have shortened detection. An alarm that has never fired in anger is untested.

### Follow-up probes

| Probe | What a good answer says |
|---|---|
| "What do you page a human for at 3 a.m.?" | User-impacting SLO burn with a runbook. Not CPU, not disk (that's a ticket), not a single failed request. **Best probe in this question.** |
| "Does CloudWatch give you EC2 memory?" | No — CloudWatch Agent required. Instant experience check. |
| "One request touches ALB → 3 Lambdas → DynamoDB → SQS → worker. It's slow. How do you find where?" | Distributed tracing with propagated context; without it you're correlating timestamps across five log groups by hand. |
| "Your observability bill is 25% of infra spend. What do you cut?" | Log ingestion/indexing first (sample, exclusion filters, archive to S3), then custom-metric cardinality, then retention tiering, then trace sampling. Notably *not* alarms. |
| "How do you avoid 40 pages from one root cause?" | Composite alarms, dependency-aware suppression, alert on the top-level SLI and let the rest be dashboard context. |
| "CloudWatch vs CloudTrail?" | Behaviour vs audit. If they blur these, seniority is questionable. |
| "How do you know the front-end is healthy if every backend metric is green?" | RUM + synthetics. Very commonly missed. |

### Red flags

- Alerting on resource utilization as the primary mechanism.
- No structured logging or correlation IDs.
- Log retention never mentioned.
- "We use Datadog" with no idea how it ingests or what it costs.
- No RUM/synthetics — measuring servers, not users.

### Docs coverage

Partial: [§8.2 CloudWatch Basics](transcripts-formatted.md#82-cloudwatch-basics) ·
[§8.3 CloudWatch Metrics and Alarms](transcripts-formatted.md#83-cloudwatch-metrics-and-alarms) ·
[§8.4 SNS](transcripts-formatted.md#84-sns--simple-notification-service) ·
[§8.5 CloudTrail](transcripts-formatted.md#85-cloudtrail) ·
[Q17 alarm states](interview-questions.md)

**Gap:** no X-Ray/tracing, no CloudWatch Agent, no container observability, no Datadog/third-party
integration, no SLO-based alerting, no RUM, no cost-of-observability discussion.

---

## Q5 — Secrets and sensitive information

**Question as asked:**
> How do you manage secrets and sensitive information on AWS? Describe your experience using AWS
> Secrets Manager, Parameter Store, and encryption practices.

### What you're listening for

- Can they articulate the **Secrets Manager vs Parameter Store** decision on cost, rotation, and size
  — not just "both store secrets"?
- **Rotation without downtime** — do they know why naive rotation breaks running apps?
- Do they treat **environment variables** with appropriate suspicion?
- Do they mention **caching**, i.e. that fetching a secret on every invocation costs money and latency?
- **Detection**: what happens when a secret leaks anyway?
- Front-end awareness: anything in a browser bundle is public, full stop.

### Model answer

**1. The decision table.**

| | **Secrets Manager** | **SSM Parameter Store** |
|---|---|---|
| Built-in rotation | Yes, managed Lambda rotation with native RDS/Redshift/DocumentDB support | No — you build it |
| Cost | Per secret per month + per API call (~$0.40/secret/month order of magnitude) **(verify)** | Standard tier free; Advanced tier priced per parameter, needed for >4 KB and higher throughput **(verify)** |
| Size limit | Larger (tens of KB) **(verify)** | 4 KB standard / 8 KB advanced **(verify)** |
| Cross-account access | Native resource policy | Possible but clunkier |
| Cross-region replication | Built-in | Not natively |
| Hierarchy / config data | Not its purpose | Path hierarchies, great for config |
| Right use | Database credentials, third-party API keys, anything needing rotation | Non-secret config, feature flags, ARNs, and low-sensitivity secrets (SecureString + KMS) |

My rule: **rotation or cross-account → Secrets Manager; otherwise Parameter Store**, which is free at
standard tier and where cost matters at scale (thousands of parameters × several environments adds up
in Secrets Manager). Both encrypt with KMS; Parameter Store `SecureString` with a **customer-managed
key** gives you the same audit and key-policy control as Secrets Manager. Worth noting Parameter Store
can also *read* Secrets Manager secrets by path, so the two compose.

**2. Retrieval patterns — where the mistakes live.**

- **Never bake secrets into images, AMIs, or code.** Fetch at runtime with the workload's IAM role.
- **Cache them.** Fetching on every Lambda invocation adds latency, adds API cost, and can hit
  throttling limits under load. Use the **AWS Parameters and Secrets Lambda Extension** (local
  in-process cache with a configurable TTL) or the language caching clients; in containers, fetch at
  startup and refresh on a timer or on auth failure.
- **Environment variables are a trade-off, and I'd say which side I'm on:** convenient, but Lambda env
  vars are visible to anyone with `GetFunctionConfiguration`, ECS task definitions expose them in the
  console, and they leak into crash dumps, log lines, and child processes. For low-sensitivity config,
  fine. For database passwords, I fetch at runtime instead. ECS/EKS have a middle path — ECS task
  definition `secrets` (valueFrom a Secrets Manager/SSM ARN, injected by the agent at task start,
  not stored in the definition) and the **Secrets Store CSI driver** with the AWS provider on EKS to
  mount them as files. Files beat env vars because they're not inherited by child processes and can be
  refreshed in place.
- **Access is scoped to the specific secret ARN**, plus `kms:Decrypt` on the specific key with a
  `kms:ViaService` condition. Not `secretsmanager:GetSecretValue` on `*` — which is what you find in
  most real accounts, and it means one compromised function can read every secret in the account.

**3. Rotation done properly.**

The naive version breaks production: you rotate the password, and every running instance still holding
the old one starts failing until it happens to refetch. Two correct approaches:

- **Alternating-users strategy** (what Secrets Manager supports for RDS): two database users; rotation
  updates the *inactive* one and then flips which is current. There's always a valid credential during
  the transition, so no window of failure.
- **Dual-secret / grace-period pattern** for third-party keys: create the new key, publish it,
  let both be valid for a rotation window, then revoke the old one.

Either way, the app must **handle an auth failure by refetching the secret and retrying once** — that
retry is what makes rotation safe, and it's the piece teams forget. Rotation Lambdas for a private RDS
instance need VPC placement plus a VPC endpoint for Secrets Manager (otherwise they hang trying to
reach a public endpoint — a classic debugging session).

And: **rotation must be tested on a schedule**, in pre-prod, ideally continuously. An untested
rotation Lambda is a time bomb that goes off on its own cron.

**4. Prevention, detection, response.**

- **Prevention**: pre-commit hooks (`git-secrets`, `trufflehog`, `gitleaks`), the same scan as a
  blocking CI check, GitHub secret scanning with push protection, `.gitignore` discipline, and IaC that
  never has plaintext values (Terraform: pull from data sources; note that **secrets land in Terraform
  state**, so state must be encrypted, access-controlled, and never in a repo).
- **Detection**: CloudTrail on `GetSecretValue` — alarm on anomalous volume or an unexpected principal;
  GuardDuty for credential-exfiltration patterns; **Macie** to find secrets and PII sitting in S3.
- **Response runbook**, written in advance: rotate immediately, revoke active sessions, review
  CloudTrail for use of the leaked credential, assess data access, notify per policy. And a genuinely
  senior point: **a secret in git history is compromised even after you force-push it away** — assume
  it's public, rotate it, don't just delete it.

**5. Front-end reality** (worth stating since it comes up constantly): anything shipped to a browser
is public — build-time env vars in a bundle, "hidden" API keys in JS, config in a fetched JSON file.
The correct pattern is a backend-for-frontend or Cognito flow that exchanges a user session for
short-lived, narrowly-scoped credentials (STS via Cognito Identity Pools, or just keep AWS credentials
server-side and expose an API). Third-party keys that must be usable from the browser (analytics,
maps) should be origin-restricted at the vendor and treated as public identifiers, not secrets.

**6. Also in scope for "sensitive information"** — because the question is broader than credentials:
PII handling, field-level encryption for the most sensitive attributes (KMS or DynamoDB
client-side encryption so it's ciphertext even to a DB admin), tokenization, redaction in logs
(**CloudWatch Logs data protection policies** can mask PII patterns automatically **(verify)**), and
data-retention/deletion obligations. Candidates who only think "passwords" when asked about sensitive
data have a narrower view than the question invites.

### Follow-up probes

| Probe | What a good answer says |
|---|---|
| "You have 5,000 config values across 4 environments. Secrets Manager or Parameter Store?" | Parameter Store for the non-secret bulk (free tier, hierarchies), Secrets Manager for the rotating credentials. Cost-aware. |
| "You rotate the DB password. What breaks?" | Everything holding the old credential until it refetches — hence alternating users and refetch-on-auth-failure. |
| "Is a Lambda environment variable a safe place for a DB password?" | Encrypted at rest, but readable via `GetFunctionConfiguration` and prone to leaking into logs. Acceptable for low sensitivity; fetch-at-runtime for real secrets. |
| "How does a task in ECS get a secret without it appearing in the task definition?" | `secrets`/`valueFrom` with the secret ARN; the agent injects at launch. Or CSI driver on EKS. |
| "A secret was committed to a public repo 6 months ago and removed. Are you fine?" | No. Rotate. It's in clones, forks, caches, and scrapers. Non-negotiable answer. |
| "How do you stop one compromised Lambda reading every secret?" | Per-secret ARN scoping + KMS key separation per environment/domain. |
| "How do you know your rotation Lambda still works?" | Scheduled rotation in pre-prod with automated verification; alarm on rotation failure. |

### Red flags

- Secrets in environment variables set by CI, treated as a complete answer.
- No caching — fetching per request.
- `Resource: "*"` on secret access.
- No rotation, or rotation with no story for in-flight credentials.
- "We removed it from the repo" as remediation for a leak.

### Docs coverage

Very thin: [§9.1 Overview — Secrets Manager & CloudFront](transcripts-formatted.md#91-overview--secrets-manager--cloudfront)
(roughly one paragraph — benefits only, no mechanics).

**Gap:** Parameter Store, rotation strategies, retrieval/caching patterns, KMS integration, leak
response — none of it is in the docs.

---

## Q6 — CI/CD pipelines for full-stack applications

**Question as asked:**
> How do you set up CI/CD pipelines in AWS for full-stack applications? Walk through your experience
> with services like CodeCommit, CodeBuild, CodeDeploy, and CodePipeline to implement end-to-end
> automation.

> **Interviewer note — say this out loud if the candidate raises it, and give credit:** AWS stopped
> onboarding new customers to **CodeCommit** around mid-2024; existing customers continue to be
> served, and most teams use GitHub/GitLab with CodeBuild/CodePipeline or with GitHub Actions instead.
> **(verify current status — this is exactly the kind of thing that changes.)** A candidate who says
> "I'd use CodeCommit for greenfield today" is either behind or not paying attention; a candidate who
> flags the change is demonstrating that they track the platform. Don't penalize a candidate for
> knowing CodeCommit — penalize one who can't reason about the alternatives.

### What you're listening for

- **Build once, promote the same artifact.** Rebuilding per environment is the most common
  architectural flaw in real pipelines.
- **Deployment strategy and automated rollback** — do they connect deploys to alarms?
- **Cross-account** separation (tooling / dev / stage / prod) with role assumption, or is everything
  in one account?
- **Front-end deployment done properly** — cache headers, invalidation, atomic switch. This is where a
  front-end architect should shine, and where most backend candidates are vague.
- **Decoupling deploy from release** (feature flags) — a strong senior signal.
- Do they mention **DORA metrics** or any measure of whether the pipeline is actually good?

### Model answer

**1. Principles first.**

1. **Build once, deploy many.** One immutable artifact (container image by digest, or a versioned S3
   bundle) is promoted through environments. Rebuilding per environment means dev and prod ran
   different bits, and your test results no longer describe what's in production.
2. **Everything in version control** — app, IaC, pipeline definition, alarms, dashboards.
3. **The pipeline is the only path to production.** No console changes. Enforced by IAM: humans don't
   have deploy permissions in prod; the pipeline role does.
4. **Trunk-based with short-lived branches** and PR gates, so integration pain stays small.
5. **Fast feedback.** If the PR pipeline takes 40 minutes, engineers batch changes, and batching is
   what makes deploys risky.

**2. The pipeline, stage by stage.**

```
Source (GitHub/CodeCommit)
  └─► PR pipeline: lint · typecheck · unit tests · SAST · IaC scan · secret scan · build preview env
Merge to main
  └─► CodePipeline
       ├─ Build     (CodeBuild): build once → container image → ECR (by digest) / SPA bundle → S3
       ├─ Test      integration + contract tests against an ephemeral stack
       ├─ Deploy dev    (auto)      → smoke tests / synthetic canary
       ├─ Deploy stage  (auto)      → load + E2E tests
       ├─ Manual approval (only where a human judgement is genuinely required)
       └─ Deploy prod   → canary/blue-green with automatic rollback on CloudWatch alarm
```

**3. Source.** GitHub (or CodeCommit for existing users) connected via **CodeStar Connections /
CodeConnections** **(verify the current name — AWS renamed this)**. Branch protection, required
reviews, signed commits where compliance requires it. Webhook-triggered, not polled.

**4. CodeBuild.** `buildspec.yml` with explicit phases; dependency **caching** (local or S3) because
`npm ci` from cold is often the longest phase; **VPC configuration** when the build needs private
resources (note it then needs a NAT or endpoints for outbound); **privileged mode** for Docker builds;
**batch builds** for parallel matrix jobs; and **test reports** published so failures are readable in
the console rather than buried in logs. Build-time secrets come from Secrets Manager/Parameter Store
via the role — never as plaintext env vars in the project. Also worth knowing: CodeBuild can host
**GitHub Actions runners**, which is a good bridge if the org lives in GitHub but wants compute and
IAM inside AWS **(verify)**.

**5. Artifacts.** Container images in **ECR** with immutable tags, scan-on-push, and lifecycle policies
to expire old images (an unmanaged ECR repo quietly becomes a real cost line). Reference images by
**digest** in deployment manifests, not by mutable tag — otherwise `:latest` means "whatever was there
when the node pulled it", which destroys reproducibility. Front-end bundles versioned in S3.

**6. Cross-account deployment** (the structure that matters at senior level). A **tooling account**
holds the pipeline; it assumes a deployment role in each target account. Two details candidates get
wrong: the artifact bucket must be encrypted with a **customer-managed KMS key shared with the target
accounts** (the default AWS-managed key can't be shared cross-account), and the target-account role
must trust only the pipeline role, scoped tightly. Prod credentials never exist in the tooling
account's static config; it's all `AssumeRole`.

**7. Deployment strategies by workload.**

| Workload | Strategy |
|---|---|
| **EC2 / ASG** | CodeDeploy in-place (`OneAtATime`, `HalfAtATime`) or blue/green with a new ASG behind the ALB; `appspec.yml` lifecycle hooks (`BeforeInstall`, `AfterInstall`, `ApplicationStart`, `ValidateService`) where `ValidateService` runs a real smoke test, not `sleep 30` |
| **ECS** | CodeDeploy blue/green with a **test listener** — validate the green target group on a separate port before shifting the production listener; or rolling with circuit breaker + rollback |
| **Lambda** | Alias + **weighted routing**; CodeDeploy `Canary10Percent5Minutes` or `Linear10PercentEvery1Minute`; `BeforeAllowTraffic` / `AfterAllowTraffic` hooks for validation; rollback wired to a CloudWatch alarm on the alias's error metric |
| **SPA front-end** | Upload hashed assets to S3 **first** (`Cache-Control: max-age=31536000, immutable`), then flip `index.html` (`no-cache`) last so the switch is atomic and no user gets a new HTML referencing assets that aren't uploaded yet. Targeted CloudFront invalidation of `/index.html` only — invalidating `/*` is slow, costs money, and cold-starts your whole edge cache. Alternative: versioned path prefixes (`/v123/`) so you never invalidate at all |
| **IaC** | CDK/CloudFormation change sets or `terraform plan` reviewed as an artifact before apply; drift detection on a schedule |

**The rollback story is the answer to the real question.** Deployment gates on CloudWatch alarms: if
error rate or latency crosses the threshold during the canary window, CodeDeploy rolls back
automatically with no human in the loop. Rollback must be *faster and more boring* than fixing
forward. And rollback needs to be tested — including the case where a database migration already ran.

**8. Database migrations** — the part that breaks "just roll back". Migrations must be
**backwards-compatible for one version**: expand-then-contract (add nullable column → deploy code that
writes both → backfill → deploy code that reads new → drop old in a later release). That's what makes
code rollback safe. If a candidate doesn't raise migrations when asked about rollback, probe it — it's
where real deploy incidents come from.

**9. Decouple deploy from release.** Feature flags (**AppConfig**, LaunchDarkly, or your own) mean
code ships dark and is enabled progressively, so a bad feature is a config flip rather than a
redeploy. This is what lets you deploy many times a day safely. AppConfig also has validators and a
deployment strategy with automatic rollback on alarm, which makes config changes as safe as code
changes.

**10. How I'd measure the pipeline** — the pipeline is a product with SLOs: **deployment frequency,
lead time for change, change failure rate, MTTR** (DORA). If change failure rate is high, add gates;
if lead time is long, parallelize and cache; if MTTR is long, invest in rollback automation. That
framing — measuring the pipeline rather than just having one — is the staff-level marker here.

**Build vs buy:** I'd be honest that GitHub Actions or GitLab CI often gives better DX and ecosystem
than CodePipeline/CodeBuild, with AWS access via **OIDC role assumption** and no stored keys. The case
for the native services is when you want the build compute and IAM entirely inside your AWS
boundary, cross-account deploys with native roles, or your compliance story requires it. Either is
defensible; having a reason is what matters.

### Follow-up probes

| Probe | What a good answer says |
|---|---|
| "Do you rebuild the artifact for each environment?" | No — build once, promote. Config comes from the environment (Parameter Store/AppConfig), not from a rebuild. |
| "How does the pipeline get credentials for prod?" | Cross-account `AssumeRole` from the tooling account; no static keys; humans have no prod deploy rights. |
| "A deploy is bad. How long until users stop seeing errors, and who decides?" | Nobody decides — the alarm triggers automatic rollback within the canary window. Number attached. |
| "You need to roll back but the migration already ran." | Expand/contract; backwards-compatible migrations; forward-fix if the schema change is destructive. **Best probe here.** |
| "Deploying a React SPA — walk me through cache headers." | Immutable hashed assets, no-cache `index.html`, assets uploaded before HTML, targeted invalidation. Front-end depth check. |
| "How do you test IaC?" | Plan review, policy-as-code (cfn-guard/OPA/Checkov), deploy to ephemeral env, CDK assertions/snapshot tests, drift detection. |
| "How long does your pipeline take, and is that OK?" | Any real number plus reasoning about where the time goes. Vagueness suggests they didn't own it. |
| "Would you use CodeCommit for a new project today?" | Awareness of the new-customer onboarding change and a reasoned alternative. |

### Red flags

- Rebuilding per environment; environment-specific build artifacts.
- Manual approval before every deploy as the primary safety mechanism.
- No automated rollback.
- `:latest` tags in production.
- `aws s3 sync` + `CloudFront invalidate /*` as the whole front-end deploy story.
- Static AWS keys in CI secrets.
- No mention of migrations when discussing rollback.

### Docs coverage

**Absent.** The transcripts contain no CodeCommit, CodeBuild, CodeDeploy, or CodePipeline content.
The closest adjacent material is [§7.1 CloudFormation Basics](transcripts-formatted.md#71-cloudformation-basics)
and [§7.2 Using CloudFormation](transcripts-formatted.md#72-using-cloudformation).

**This is the largest gap between the docs and the question set.**

---

## Q7 — Cost optimization

**Question as asked:**
> How do you optimize AWS costs while maintaining performance and scalability? Discuss strategies for
> rightsizing EC2 instances, using reserved and spot instances, and leveraging auto-scaling, S3
> lifecycle policies, and RDS storage optimization.

### What you're listening for

- Does the answer start with **visibility and allocation** (tags, CUR) or jump straight to tactics?
  You can't optimize what you can't attribute.
- **Commitment strategy sophistication**: Savings Plans vs RIs, coverage targets, and the risk of
  over-committing.
- Do they name **data transfer / NAT Gateway** costs? This is the most commonly overlooked large line
  item and a strong senior signal.
- **Architectural** optimization (change the design) vs **tactical** (change the size). Senior
  engineers know the big wins are architectural.
- **Unit economics** — cost per request/tenant/order, not just total spend. Total spend *should* grow;
  unit cost shouldn't.
- Do they protect against **optimizing into an outage**? Cost work has a blast radius too.

### Model answer

**1. Visibility before action.**

- **Tagging taxonomy** enforced by IaC and tag policies (`service`, `env`, `team`, `cost-center`),
  activated as **cost allocation tags**. Untagged resources are unattributable and therefore
  unownable — I'd measure and drive down "% untagged spend" as a first-class metric.
- **CUR (Cost and Usage Report) → S3 → Athena/QuickSight** for real analysis. Cost Explorer is fine
  for trends and quick answers; CUR is where you find the anomaly at hourly, per-resource granularity.
- **AWS Budgets** with alerts, plus **Cost Anomaly Detection** for ML-based spike alerts — because the
  worst cost events are sudden and the monthly bill is far too late a feedback loop.
- **Unit cost metric**: $ per 1,000 requests, per tenant, per order. This is what makes cost a
  performance metric rather than a budget conversation, and it's what lets you tell "we grew" apart
  from "we regressed".
- Accountability: showback/chargeback per team, cost on the engineering dashboard next to latency, and
  cost review as part of architecture review.

**2. Compute (usually the largest slice).**

- **Rightsizing with data**: AWS **Compute Optimizer** (uses CloudWatch history; enable memory metrics
  via the agent or its recommendations are guessing on the dimension that matters most). Look at p95,
  not average, so you don't rightsize into throttling.
- **Graviton (arm64)** — typically better price-performance for most general workloads **(verify
  current figures)**. For interpreted languages it's often a rebuild-and-test change; for compiled or
  native-dependency code, budget real migration effort.
- **Commitment layering** — this is where sophistication shows:
  - **Compute Savings Plans**: flexible across instance family, size, region, OS, and also cover
    Fargate and Lambda. Lower discount, much lower lock-in risk.
  - **EC2 Instance Savings Plans / Standard RIs**: deeper discount, narrower flexibility.
  - **RIs still matter for RDS, ElastiCache, OpenSearch, Redshift** — Savings Plans don't cover those
    **(verify current coverage)**.
  - Strategy: commit to the **stable baseline only** (typically the trough of your usage curve), 1-year
    no-upfront to start, layered in tranches so expiry is staggered rather than a cliff. Target
    coverage around 70–80% of steady-state usage and leave the variable top on-demand/Spot. Over-
    committing during a growth forecast that doesn't materialize is a multi-year mistake — and the
    right answer here explicitly names that risk.
- **Spot** for anything interruption-tolerant: batch, CI runners, stateless web behind an ALB, EMR
  task nodes, Karpenter-managed Kubernetes capacity. Do it properly: **diversify across many instance
  types and AZs** with the `capacity-optimized`/`price-capacity-optimized` allocation strategy, handle
  the 2-minute interruption notice and rebalance recommendations (drain connections, checkpoint work),
  and use an ASG **mixed instances policy** with an on-demand base plus Spot on top. Discounts are
  substantial but variable — I'd avoid quoting a specific percentage.
- **Turn things off**: scheduled scale-to-zero for dev/test/staging outside business hours (a
  five-day-a-week eight-hour dev environment is roughly a 75% saving on that footprint — arithmetic,
  not a vendor claim), Instance Scheduler or an EventBridge+Lambda cron, and cleanup of the classic
  zombies: unattached EBS volumes, idle load balancers, unassociated Elastic IPs, old snapshots, idle
  RDS instances, over-provisioned NAT Gateways, forgotten Sagemaker/OpenSearch clusters.
- **Auto Scaling as a cost tool**, not just an availability tool: target tracking on the right metric
  so you're not paying for peak capacity 24/7; conservative scale-in to avoid thrash.
- **Architectural**: right *compute model*, not just right size — Lambda for spiky, Fargate for
  medium/steady, EC2+Spot for cheapest bulk. Consolidate underutilized microservices; the fixed
  overhead per service (ALB, NAT, minimum task size, observability) is real and it multiplies.

**3. Storage.**

- **S3**: **Intelligent-Tiering** as the default for unpredictable access — it automates the
  transitions and removes the guesswork. Explicit **lifecycle policies** when the access pattern is
  known, and know the constraints: minimum storage durations (Glacier Flexible Retrieval 90 days,
  Deep Archive 180 days, IA classes 30 days **(verify)**), per-object transition request charges that
  can exceed the savings for many small objects, and Intelligent-Tiering not tiering objects under
  128 KB **(verify)**. Retrieval cost and latency from Deep Archive is a real constraint — don't
  archive anything an auditor might need tomorrow.
- Cheap, high-yield S3 wins: lifecycle rule to **abort incomplete multipart uploads** (silent,
  invisible, sometimes enormous), expire **old noncurrent versions** on versioned buckets, and
  **S3 Storage Lens** to find where the bytes actually are. Compress before storing.
- **EBS**: migrate **gp2 → gp3** — gp3 decouples IOPS/throughput from size and is generally cheaper at
  equivalent baseline **(verify the percentage)**; it's one of the highest-ratio wins available.
  Right-size volumes (they can grow, so don't over-allocate up front), replace io1/io2 with gp3 unless
  the IOPS profile truly requires it, and lifecycle-manage snapshots (they're incremental, but they
  accumulate forever without a policy — **Data Lifecycle Manager** or AWS Backup).
- **CloudWatch Logs is storage too**, and its never-expire default is a recurring cost finding. Set
  retention on every log group; archive to S3 for the long tail. See [Q4](#q4--monitoring-logging-and-alerting-in-a-distributed-environment).

**4. Database.**

- Rightsize + Graviton instance classes; use **Performance Insights** to find the query causing the
  need for a bigger instance — a missing index is cheaper than an instance class bump, and this is the
  distinction between optimizing cost and just cutting it.
- **Storage autoscaling** on so you don't over-provision "just in case"; gp3 for RDS storage.
- **Aurora Serverless v2** for spiky or dev workloads instead of a permanently provisioned instance;
  **Aurora I/O-Optimized** when I/O dominates the bill **(verify the breakeven)**.
- **Stop/start non-prod** RDS (note the ~7-day auto-restart limit on stopped instances **(verify)**),
  or delete-and-restore-from-snapshot for rarely used environments.
- **Reserved instances for the steady baseline**; kill replica sprawl and unused read replicas.
- Architectural: move cold data out of the OLTP database to S3+Athena; add a cache (ElastiCache/DAX)
  so you're not paying for database reads that a cache could serve at a fraction of the cost.

**5. Data transfer — the line item everyone forgets.**

- **NAT Gateway** charges hourly *and* per GB processed. A private-subnet fleet pulling packages and
  talking to S3 through NAT can generate a startling bill. **Gateway VPC endpoints for S3 and
  DynamoDB are free** and remove that traffic from NAT entirely — this is usually the single best
  cost/effort ratio available in a VPC, and it's a security improvement too. Interface endpoints have
  an hourly cost, so compare against the NAT traffic they'd displace.
- **Cross-AZ traffic is charged**. Chatty service-to-service traffic spread across AZs for HA is a
  real trade-off: pay for cross-AZ, or use topology-aware routing and accept a slightly weaker
  failure story. Name the trade-off rather than pretending it's free.
- **Egress to internet** is the expensive direction: **CloudFront** in front of everything public
  (and data transfer from AWS origins into CloudFront is not charged as internet egress **(verify)**),
  compression on, cache-hit ratio treated as a cost metric.
- **VPC Flow Logs** to find out who's actually generating the traffic — measure, don't guess.

**6. Cost in the development loop.** `Infracost` (or equivalent) on IaC PRs so the cost of a change is
visible at review time; budget guardrails and SCPs preventing accidental expensive resource types in
non-prod; instance-type allow-lists per environment; tag enforcement blocking untagged creation.

**7. Guardrails — how I avoid optimizing into an outage.** Every cost change is a change: it gets
load-tested, rolled out gradually, and monitored on the performance SLO, not just the bill. I'd never
rightsize prod straight from a recommendation without validating against p95 load. And I'd say plainly
that some cost is buying resilience — the 3-AZ headroom from [Q1](#q1--highly-available-and-fault-tolerant-architecture)
looks like waste on a spreadsheet and isn't. The mature framing is
**cost-*aware*, not cost-minimal**: the goal is efficiency per unit of business value, and the honest
answer sometimes is "this spend is correct".

### Follow-up probes

| Probe | What a good answer says |
|---|---|
| "Bill jumped 30% this month. Walk me through finding it." | CUR/Cost Explorer grouped by service → linked account → resource/tag, compare against deploys and traffic; Cost Anomaly Detection should have flagged it earlier. Method, not guessing. |
| "Savings Plan or Reserved Instance?" | Compute SP for flexibility across EC2/Fargate/Lambda; RIs where SPs don't apply (RDS, ElastiCache, OpenSearch, Redshift). Commit to the trough, layer terms. |
| "Which non-obvious line item do you check first?" | NAT Gateway / data transfer, then CloudWatch Logs ingestion, then unattached storage and snapshots. Strong signal. |
| "gp2 vs gp3?" | gp3 decouples IOPS from capacity, generally cheaper at baseline; near-free migration. |
| "You're told to cut 20% this quarter. Order of operations?" | Zombies and retention first (zero risk), then non-prod scheduling, then commitments, then rightsizing with load validation, then architecture. Risk-ordered. |
| "S3 lifecycle to Deep Archive after 30 days — any problem?" | Minimum-duration charges, transition request cost on many small objects, and retrieval latency/cost — plus whether anyone actually needs that data quickly. |
| "When is spending *more* the right answer?" | Availability headroom, provisioned concurrency for a latency SLO, Multi-AZ, observability. Tests judgement over reflex. |

### Red flags

- Straight to tactics with no visibility/allocation story.
- "Reserve everything" — no awareness of commitment risk.
- Spot for stateful or non-interruptible workloads.
- Data transfer never mentioned.
- Rightsizing from recommendations with no performance validation.
- Treating all cost as waste.

### Docs coverage

Partial: [§8.7 Cost Explorer](transcripts-formatted.md#87-cost-explorer) ·
[§8.8 AWS Trusted Advisor](transcripts-formatted.md#88-aws-trusted-advisor) ·
[§3.2 EC2 Purchasing Categories](transcripts-formatted.md#32-ec2-basics--purchasing-categories--instance-types)
(on-demand/reserved/spot introduced) · [§3.4 EBS](transcripts-formatted.md#34-elastic-block-store-ebs) ·
[§1.4 Billing Alerts](transcripts-formatted.md#14-leveraging-billing-alerts)

**Gap:** Savings Plans, Compute Optimizer, CUR/Athena analysis, Graviton, data transfer and NAT costs,
Intelligent-Tiering, gp3 migration, Aurora Serverless, unit economics.

---

## Q8 — Disaster recovery and backup

**Question as asked:**
> How do you implement disaster recovery and backup strategies in AWS? Talk about your approach to
> creating cross-region backups with S3, RDS snapshots, and multi-region failover strategies using
> Route 53.

### What you're listening for

- Do they start with **RTO and RPO as business inputs**? Anyone who proposes an architecture before
  asking for those two numbers is guessing.
- Can they name the **four DR strategies** and place them on the cost/RTO curve?
- **"A backup you haven't restored is not a backup."** Do they test restores?
- **Ransomware / malicious-actor thinking**: immutability, separate accounts, MFA delete. Modern DR is
  as much about a compromised credential as a datacenter fire.
- The **hard parts of multi-region**: data replication direction, split-brain, service quotas in the
  DR region, global vs regional services.
- **Failback** — the step almost everyone omits.

### Model answer

**1. RTO and RPO drive everything.**

- **RPO** = acceptable data loss (how far back). **RTO** = acceptable time to recover.
- These are business decisions per workload, not one number for the company. The internal reporting
  dashboard can have RTO of a day; the payments path might need minutes. Tiering workloads is the
  first real DR deliverable, because uniform DR means either overspending everywhere or
  under-protecting the critical path.
- Also worth defining scope: DR is not just "region down". It covers accidental deletion, a bad
  migration, data corruption, and a compromised credential doing damage on purpose. Statistically
  those are far more likely than a region loss, and they need *different* controls — which is why
  immutable backups matter more than most multi-region plans.

**2. The four strategies** (AWS's own taxonomy — worth naming precisely):

| Strategy | RTO / RPO | Cost | What's running in the DR region |
|---|---|---|---|
| **Backup & Restore** | Hours → days | Lowest | Nothing. Backups replicated; infrastructure recreated from IaC |
| **Pilot Light** | Tens of minutes → hours | Low | Data replicating continuously; compute exists but is off/minimal |
| **Warm Standby** | Minutes | Medium | Full stack running at reduced capacity; scale up on failover |
| **Multi-site active/active** | Near-zero | Highest | Full capacity in both, serving traffic |

Choosing is a cost conversation: each step up multiplies infrastructure and — more importantly —
operational complexity. Active/active also imposes real application constraints (conflict resolution,
no single-region primary key generation, latency on cross-region consistency). I'd only recommend it
when the business genuinely needs sub-minute RTO, and I'd push back if the requirement is aspirational
rather than costed.

**3. Backups.**

- **AWS Backup** as the central plane: backup plans with schedules and lifecycle, **tag-based resource
  selection** (so new resources are protected automatically — protection by default rather than by
  remembering), across EBS/RDS/Aurora/DynamoDB/EFS/FSx/S3/EC2, with cross-region *and* cross-account
  copy.
- **Immutability against ransomware**: **Backup Vault Lock** in compliance mode makes backups WORM —
  not even the account root can delete them before expiry. Combined with copies into a **separate,
  isolated backup account** with no standing human access, that's the control that survives "attacker
  gained admin in the prod account". Modern DR design has to assume the attacker is inside.
- **Restore testing** — AWS Backup has automated restore testing **(verify)**, and either way I'd run
  scheduled restore drills that validate the restored data, not just that the API call succeeded. This
  is the point I'd emphasize hardest: untested backups fail at exactly the moment you need them, and
  the failure modes are mundane (missing KMS key in the target region, snapshot without the
  parameter group, restored DB with no network path).
- **The 3-2-1 idea, adapted**: multiple copies, at least one in a different region, at least one
  logically isolated (different account, immutable).

**4. S3.**

- **Versioning** on (protects against overwrite and delete), with **MFA delete** or a bucket policy
  denying `DeleteObjectVersion` for anything critical; lifecycle to expire noncurrent versions so it
  doesn't become a cost problem ([Q7](#q7--cost-optimization)).
- **Object Lock** (governance or compliance mode) for regulatory WORM requirements.
- **Cross-Region Replication**, with **Replication Time Control** if you need a bounded replication
  SLA (AWS documents 15 minutes for the large majority of objects **(verify)**), and **S3 Batch
  Replication** to backfill objects that existed before replication was enabled — a step people
  forget, then discover their DR bucket only has the last six months.
- Two nuances worth volunteering: replication **does not replicate delete markers by default**
  (configurable — and you often *want* it off, because then a delete in prod doesn't destroy the DR
  copy), and replication needs the destination KMS key configured or encrypted objects silently fail
  to replicate. Also: replication is not a substitute for versioning/backup — it faithfully replicates
  corruption too.

**5. RDS / Aurora.**

- **Automated backups** with retention (up to 35 days **(verify)**) giving **point-in-time recovery**
  at fine granularity — PITR is the tool for "a bad migration ran at 14:03", which is a more common
  disaster than a region loss.
- **Manual snapshots** persist beyond instance deletion (automated ones don't, in general — a nasty
  surprise if someone deletes an instance).
- **Cross-region automated backup replication** for RDS, and cross-region snapshot copies for a
  scheduled floor. Snapshots are incremental, but a cross-region copy re-encrypts: **the KMS key must
  exist in the target region**, or use a **multi-Region key** ([Q2](#q2--security-across-multiple-aws-services)).
  This is the most common cross-region DR failure I've seen.
- **Aurora Global Database** for low-RPO cross-region: continuous storage-level replication with
  typically sub-second lag and managed planned/unplanned failover **(verify current RPO/RTO figures)**.
  **Aurora Backtrack** (MySQL-compatible) for rewinding a cluster in place after a bad write —
  different tool from a restore, much faster.
- Don't forget what's *around* the database: parameter groups, option groups, subnet groups, security
  groups, and the credentials in Secrets Manager (**replicate the secret to the DR region** — an
  application that fails over to a database whose password it can't fetch is still down).

**6. DynamoDB.** **PITR** (35-day window **(verify)**) plus on-demand backups; **Global Tables** for
multi-active multi-region with last-writer-wins conflict resolution — and I'd say explicitly that
last-writer-wins is an application-visible semantic, not a detail: if your workload can't tolerate it,
Global Tables is the wrong answer and you need a single-writer-region design.

**7. Multi-region failover with Route 53 — and its limits.**

- **Failover routing** with health checks on the primary; low **TTL** (60s) on the failover records;
  health checks either HTTP against a public endpoint or **CloudWatch alarm–based** for private ones.
- Make the health check *meaningful*: a deep check that verifies the database is reachable, not a
  static 200. A shallow health check is how you fail over to a region that's equally broken — or fail
  to fail over when only the database is down.
- **Honest caveat**: DNS failover is not instantaneous and not fully in your control — resolvers and
  clients cache beyond TTL, browsers pin connections, and some JVM configurations cache forever. Plan
  for minutes, not seconds, and if that's too slow use **Global Accelerator** (static anycast IPs,
  network-layer failover, no DNS dependency).
- **Route 53 Application Recovery Controller** for serious multi-region: **readiness checks**
  continuously verify the DR region is actually capable (capacity, quotas, config parity) and
  **routing controls** give you a highly available manual on/off switch that doesn't depend on health
  checks guessing right. The insight ARC encodes: **the biggest multi-region risk is that your DR
  region was quietly broken for three months and nobody knew.**
- **Static stability again**: don't design a failover that requires launching thousands of new
  instances in a region that's currently absorbing everyone else's failover traffic. Pre-provision, or
  use **capacity reservations** for the critical baseline.

**8. The parts people forget** (this list is the senior differentiator):

- **Service quotas in the DR region** are separate and default-low. You fail over and hit a vCPU or
  Lambda concurrency limit. Raise them in advance and verify.
- **IaC deployed to both regions** and kept in sync — CI deploys to both, or the DR region drifts.
- **AMIs, container images (ECR replication), Lambda artifacts, secrets, parameters** all need to
  exist in the DR region.
- **Global vs regional services**: IAM, Route 53, CloudFront, and WAF (global scope) are global; S3
  bucket *names* are global but buckets are regional. Know which of your dependencies is
  single-region.
- **DNS delegation, certificates (ACM certs are regional — and CloudFront requires us-east-1)**, and
  third-party dependencies (payment provider, IdP) which may themselves be single-region.
- **Data egress cost** of continuous cross-region replication — a real, ongoing line item.
- **Failback**: how do you get back once the primary recovers, without losing the writes that happened
  in the DR region? This needs a documented, tested procedure with a reconciliation story. Asking
  about failback is my favourite probe on this question because it separates people who have actually
  done a DR event from people who have read about one.
- **Who decides to fail over**, on what signal, with what authority? A technically perfect DR plan
  with no declared decision-maker burns 40 minutes on a conference call.

**9. Testing — the whole answer, really.**

- **Scheduled restore drills** validating data integrity, with a measured **actual** RTO/RPO compared
  against target. Publish the measured numbers; a stated RTO nobody has measured is fiction.
- **Full region-failover game days**, at least annually for tier-1 workloads. Ideally a
  regularly-exercised failover, because a path you use is a path that works.
- **Runbooks** that a stressed on-call engineer who didn't build the system can follow at 3 a.m. —
  tested by having exactly that person run them.
- **FIS** for repeatable fault injection; **ARC readiness checks** for continuous verification.
- Post-drill: update the runbook with what surprised you. Every drill finds something; the value is in
  closing it.

### Follow-up probes

| Probe | What a good answer says |
|---|---|
| "RTO 4 hours, RPO 15 minutes — what do you build?" | Pilot light: continuous data replication (Aurora Global DB or cross-region backup replication) + IaC to bring up compute. Not active/active — that over-delivers and overspends. Tests requirements-to-architecture mapping. |
| "How do you know your backups work?" | Automated restore testing with data validation, measured RTO. If the answer is "the jobs show success", that's the gap. |
| "Ransomware encrypts prod and the attacker has admin. Your backups?" | Cross-account copies in an isolated account + Vault Lock compliance mode + S3 Object Lock. Same-account backups are gone. Increasingly the most important probe here. |
| "You fail over to us-west-2. What surprises you?" | Quotas, missing KMS keys, un-replicated secrets/AMIs/images, cold caches, capacity, stale IaC, DNS caching. Depth of real experience. |
| "Primary is back. Now what?" | Failback procedure, reconcile divergent writes, controlled traffic shift, no split-brain. Frequently omitted. |
| "Is cross-region replication a backup?" | No — it replicates corruption and deletion faithfully (unless delete markers are excluded). Backups need versioning/PITR/immutability. |
| "Route 53 failover configured, health check green, region is broken. Why?" | Shallow health check. Needs deep dependency validation. |
| "Which is more likely — region failure or someone deleting the wrong thing?" | The latter, by a wide margin, which is why PITR, versioning, and immutability outrank multi-region for most workloads. Good judgement signal. |

### Red flags

- Proposing an architecture before asking for RTO/RPO.
- Backups in the same account and region as production.
- No restore testing.
- Believing DNS failover is instant.
- No failback plan.
- Treating replication as backup.
- No awareness of DR-region quotas or config parity.

### Docs coverage

**Effectively absent.** Snapshots are mentioned in [§3.4 EBS](transcripts-formatted.md#34-elastic-block-store-ebs)
and [§6.2 RDS Basics](transcripts-formatted.md#62-rds-basics); versioning in
[§4.5 Object Versioning](transcripts-formatted.md#45-object-versioning); Route 53 record types in
[§5.8 Route 53](transcripts-formatted.md#58-route-53).

**Gap:** the entire DR discipline — strategy taxonomy, AWS Backup, Vault Lock, cross-region/cross-account
copies, CRR/RTC, Aurora Global Database, failover routing, ARC, failback, drills.

---

## Appendix A — Cross-cutting themes

If a candidate demonstrates these five, the specific service knowledge is learnable. If they don't,
service knowledge won't save them.

1. **Requirements before architecture.** Asks for the number (SLO, RTO, RPO, budget, scale) before
   proposing. Appears in all eight questions.
2. **Failure-mode thinking.** For each component: what happens when this fails, who notices, how fast,
   and what does the user see?
3. **Trade-offs volunteered, not extracted.** Says "I'd choose X, accepting Y" unprompted. Nothing in
   AWS is free of trade-offs, and pretending otherwise is the clearest inexperience tell.
4. **Verification.** Every claim has a "here's how I know" — a test, a drill, a metric, a load test, a
   measured number. Design without verification is a wish.
5. **Cost as a first-class design dimension**, alongside latency and availability, in *every* answer —
   not confined to Q7.

**A question worth asking regardless of the eight above:** *"Tell me about a production incident you
caused or owned on AWS, and what you changed afterwards."* The specificity of that answer will tell
you more than any architecture discussion. Candidates who have genuinely operated systems have a
detailed, slightly rueful story with a concrete follow-up action. Candidates who haven't tell you
about a time they optimized something.

---

## Appendix B — Claims to verify before quoting

Everything in this file marked **(verify)**, collected. These are correct to the best of my knowledge
but are the kind of detail AWS changes — confirm against current documentation, especially anything
about pricing, quotas, or recent service changes. Some of these sit near or beyond my knowledge
cutoff.

| Claim | Why to verify |
|---|---|
| ALB pre-warming guidance | AWS's stated position on this has shifted over time |
| Cross-zone LB defaults (ALB on / NLB off; per-target-group override) | Defaults and configurability have changed |
| RDS Multi-AZ failover 60–120s; Multi-AZ cluster faster; Aurora faster still | Documented figures change; the ordering is reliable, the numbers less so |
| Route 53 health check intervals (30s / 10s fast) | Confirm current options and pricing |
| FIS name change and AZ power-interruption scenario availability | Renamed from Fault Injection Simulator; scenario catalogue grows |
| Resource Control Policies (RCPs) | Relatively recent org feature (~late 2024) |
| ALB mutual TLS | Newer capability; confirm supported modes |
| KMS custom rotation periods (beyond annual) | Newer capability |
| S3 Bucket Keys KMS-request reduction ("up to 99%") | AWS marketing figure — cite as AWS's claim, not yours |
| API Gateway HTTP API vs REST API feature matrix | AWS keeps closing the gap |
| API Gateway REST 29s integration timeout / raisable quota | Changed relatively recently |
| Lambda ~1,769 MB ≈ 1 vCPU | Documented, but confirm |
| Lambda payload limits (6 MB sync / 256 KB async) | Confirm current |
| Lambda SnapStart runtime support beyond Java | Expanded recently |
| Graviton price-performance percentages (Lambda and EC2) | Vendor figures, workload-dependent |
| DynamoDB per-partition throughput (~3,000 RCU / 1,000 WCU) | Documented; adaptive capacity complicates the simple statement |
| Aurora Serverless v2 minimum ACU / scale-to-zero and auto-pause | Newer capability |
| Aurora I/O-Optimized breakeven (~25% of bill in I/O) | AWS guidance figure |
| CloudWatch Logs Infrequent Access class | Newer log class |
| CloudWatch Logs data protection policies (PII masking) | Confirm supported patterns |
| Secrets Manager pricing (~$0.40/secret/month) and size limits | Pricing changes; region-dependent |
| Parameter Store standard/advanced limits (4 KB / 8 KB) and advanced pricing | Confirm current |
| CodeCommit closed to new customers (~mid-2024) | **Verify carefully — this is the most consequential claim here** |
| CodeStar Connections → CodeConnections rename | AWS renamed this |
| CodeBuild-hosted GitHub Actions runners | Newer feature |
| S3 lifecycle minimum durations (Glacier 90d / Deep Archive 180d / IA 30d) | Confirm per storage class |
| S3 Intelligent-Tiering 128 KB minimum object size for tiering | Confirm current |
| gp3 vs gp2 cost difference (~20%) | Region- and configuration-dependent |
| Savings Plans coverage (EC2/Fargate/Lambda) vs RIs (RDS/ElastiCache/OpenSearch/Redshift) | Coverage has expanded over time |
| CloudFront: data transfer from AWS origins into CloudFront not charged as egress | Confirm current pricing terms |
| RDS stopped-instance ~7-day auto-restart | Confirm current |
| RDS automated backup retention max 35 days; DynamoDB PITR 35 days | Confirm current |
| S3 Replication Time Control 15-minute SLA | Confirm current SLA terms |
| AWS Backup automated restore testing | Newer feature (~late 2023) |
| Aurora Global Database RPO/RTO figures | Documented figures change |
| Route 53 ARC availability/SLA figures | Confirm before quoting a number |
