
# AWS Essentials — Easy-to-Miss Interview Questions

> Simple Q&A for new learners. Each answer links back to the relevant section in [transcripts-formatted.md](transcripts-formatted.md).

---

## IAM (Identity & Access Management)

**Q1: Should you use the root account for everyday AWS tasks?**

No. The root account has unrestricted access to everything and should only be used to create your first IAM user. After that, always use IAM users with only the permissions they need (least privilege).

> See: [§2.1 What IAM Is](transcripts-formatted.md#21-what-iam-is) · [§2.2 Provisioning IAM for the First Time](transcripts-formatted.md#22-provisioning-iam-for-the-first-time)

---

**Q2: Should you attach policies directly to a user or to a group?**

Attach policies to **groups**, not individual users. Inline policies on users are hard to track and easy to forget — they create security gaps. Put users in groups that already have the right policies attached.

> See: [§2.3 Creating Users, Groups, and Policies](transcripts-formatted.md#23-creating-users-groups-and-policies)

---

**Q3: What is the difference between an IAM policy and an IAM role?**

- A **policy** defines what is allowed (e.g., "EC2 read access").
- A **role** is similar to a policy but is designed to be given to **AWS services** (like Lambda or EC2) or to users who need **temporary access**. When the task ends, the access expires automatically — no manual cleanup needed.

> See: [§2.4 Establishing IAM Roles](transcripts-formatted.md#24-establishing-iam-roles)

---

## EC2 (Elastic Cloud Compute)

**Q4: What happens to a Spot Instance if the market price exceeds your bid?**

AWS **shuts the instance down automatically**. Spot instances are perfect for short, flexible, interruptible work — but never use them for anything that can't tolerate an unexpected stop.

> See: [§3.2 EC2 Basics — Purchasing Categories & Instance Types](transcripts-formatted.md#32-ec2-basics--purchasing-categories--instance-types)

---

**Q5: Can a Security Group explicitly deny traffic from a specific IP?**

No. Security groups are **allow-only** — you can only add rules to permit traffic, never to block it. To explicitly deny traffic from a specific IP or range, use a **NACL** instead.

> See: [§3.5 Security Groups](transcripts-formatted.md#35-security-groups) · [§5.5 Network Access Control Lists (NACLs)](transcripts-formatted.md#55-network-access-control-lists-nacls)

---

**Q6: If you stop an EC2 instance, what happens to its CloudWatch alarm?**

The alarm moves to the **Insufficient data** (grey) state because there is no metric data coming in. This is expected — it does not mean the alarm is broken or misconfigured.

> See: [§8.2 CloudWatch Basics](transcripts-formatted.md#82-cloudwatch-basics)

---

## S3 (Simple Storage Service)

**Q7: Can you turn off versioning once it's enabled on an S3 bucket?**

No. Once versioning is enabled it can only be **suspended**, not fully disabled. Every version of every object is stored (and billed), so think before enabling it.

> See: [§4.3 Creating Buckets and Objects](transcripts-formatted.md#43-creating-buckets-and-objects) · [§4.5 Object Versioning](transcripts-formatted.md#45-object-versioning)

---

**Q8: Does an S3 bucket name only need to be unique inside your own AWS account?**

No. Bucket names must be **globally unique across every AWS account worldwide**. If someone else already has `mybucket`, you cannot use that name — regardless of which account or region you're in.

> See: [§4.3 Creating Buckets and Objects](transcripts-formatted.md#43-creating-buckets-and-objects)

---

## VPC & Networking

**Q9: Do a bastion host (public subnet) and a private instance need to be in the same subnet to SSH between them?**

No — they only need to be in the **same VPC**. Every VPC has a built-in "local" route (e.g., `10.0.0.0/24 → local`) that automatically makes every subnet within the VPC reachable from every other subnet. You do NOT need the same subnet.

The two real requirements are:
1. Both instances are in the **same VPC**.
2. The **security group** on the private instance has an inbound SSH rule allowing the bastion's private IP (or its security group).

This is the classic "missing dot" — the transcript covers security groups in §3.5 and VPC routing in §5.2, but the connection between them is easy to miss.

> See: [§5.2 VPC Basics](transcripts-formatted.md#52-vpc-basics) · [§3.5 Security Groups](transcripts-formatted.md#35-security-groups) · [§5.4 Route Tables](transcripts-formatted.md#54-route-tables)

---

**Q10: What actually makes a subnet "public" vs "private"?**

It is the **route table**. A subnet is public if — and only if — its route table has a route sending `0.0.0.0/0` traffic to an **Internet Gateway**. Without that route, the subnet is private even if the instances inside it have public IP addresses assigned.

> See: [§5.4 Route Tables](transcripts-formatted.md#54-route-tables) · [§5.6 Subnets](transcripts-formatted.md#56-subnets)

---

**Q11: What is the difference between a NAT Gateway and an Internet Gateway?**

| Gateway | Direction | Who can initiate? |
|---------|-----------|-------------------|
| **Internet Gateway** | Two-way | Public instances reach the internet; internet can reach them back |
| **NAT Gateway** | Outbound only | Private instances can reach the internet (e.g., download updates), but no one on the internet can initiate a connection inward |

> See: [§5.3 Gateways](transcripts-formatted.md#53-gateways)

---

**Q12: If a NACL allows traffic but the Security Group blocks it, does the traffic get through?**

No. Both layers must allow the traffic independently:
- **NACL** is evaluated first at the **subnet boundary**.
- **Security group** is evaluated at the **instance level**.

If either one blocks the traffic, it doesn't get through. When troubleshooting connectivity, check both.

> See: [§3.5 Security Groups](transcripts-formatted.md#35-security-groups) · [§5.5 Network Access Control Lists (NACLs)](transcripts-formatted.md#55-network-access-control-lists-nacls)

---

**Q13: Does rule order matter in a NACL?**

Yes. NACL rules are evaluated in **ascending numeric order** (100, 110, 120…). The **first matching rule wins** — everything below it is ignored. The implicit last rule (`*`) is a **Deny all** that cannot be removed.

Security groups work differently — all rules are evaluated together and the most permissive match wins.

> See: [§5.5 Network Access Control Lists (NACLs)](transcripts-formatted.md#55-network-access-control-lists-nacls)

---

## Databases

**Q14: When should you use RDS vs DynamoDB?**

- **RDS** — your data has a fixed structure (tables, rows, columns) and you need complex SQL queries across multiple tables.
- **DynamoDB** — your data is flexible or document-based (JSON/XML, key-value) and you need very fast, simple lookups with minimal query complexity.

> See: [§6.2 RDS Basics](transcripts-formatted.md#62-rds-basics) · [§6.3 DynamoDB Basics](transcripts-formatted.md#63-dynamodb-basics)

---

## Security & Monitoring

**Q15: Is a single-region CloudTrail trail sufficient?**

No. A single-region trail only captures activity in one region — anything happening in other regions goes completely unlogged. Always create a **multi-region trail** to capture all account activity.

> See: [§8.5 CloudTrail](transcripts-formatted.md#85-cloudtrail)

---

**Q16: What does AWS Trusted Advisor actually check?**

It automatically scans your account in five areas:

| Category | Example checks |
|----------|---------------|
| **Security** | S3 public access, IAM password policy, CloudTrail enabled |
| **Performance** | EC2 instance efficiency, service limits |
| **Cost Optimization** | Low-utilization instances, idle resources |
| **Fault Tolerance** | Multi-AZ RDS, EBS snapshot coverage |
| **Service Limits** | Usage approaching AWS quotas |

The basic checks are free — there is no reason not to review them regularly.

> See: [§8.8 AWS Trusted Advisor](transcripts-formatted.md#88-aws-trusted-advisor)

---

**Q17: What are the three states a CloudWatch alarm can be in?**

| State | Meaning |
|-------|---------|
| **OK** (green) | Metric is within the normal range |
| **In alarm** (red) | Metric has crossed the threshold you set |
| **Insufficient data** (grey) | Not enough data to evaluate — common when an instance is stopped |

> See: [§8.2 CloudWatch Basics](transcripts-formatted.md#82-cloudwatch-basics)
