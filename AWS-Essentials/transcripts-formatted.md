# AWS Essentials — Course Transcripts

> **Instructor:** Elizabeth Hord | AWS Certified (5 certifications)

---

## Table of Contents

1. [Getting Started](#1-getting-started)
   - [1.1 Course Introduction](#11-course-introduction)
   - [1.2 Overview of AWS Accounts & Free Tier](#12-overview-of-aws-accounts--free-tier)
   - [1.3 Creating an AWS Account & Navigating the Console](#13-creating-an-aws-account--navigating-the-console)
   - [1.4 Leveraging Billing Alerts](#14-leveraging-billing-alerts)
   - [1.5 AWS Documentation](#15-aws-documentation)

2. [Identity and Access Management (IAM)](#2-identity-and-access-management-iam)
   - [2.1 What IAM Is](#21-what-iam-is)
   - [2.2 Provisioning IAM for the First Time](#22-provisioning-iam-for-the-first-time)
   - [2.3 Creating Users, Groups, and Policies](#23-creating-users-groups-and-policies)
   - [2.4 Establishing IAM Roles](#24-establishing-iam-roles)

3. [Elastic Cloud Compute (EC2)](#3-elastic-cloud-compute-ec2)
   - [3.1 Overview of EC2](#31-overview-of-ec2)
   - [3.2 EC2 Basics — Purchasing Categories & Instance Types](#32-ec2-basics--purchasing-categories--instance-types)
   - [3.3 Amazon Machine Images (AMI)](#33-amazon-machine-images-ami)
   - [3.4 Elastic Block Store (EBS)](#34-elastic-block-store-ebs)
   - [3.5 Security Groups](#35-security-groups)
   - [3.6 Auto Scaling](#36-auto-scaling)
   - [3.7 IP Addressing](#37-ip-addressing)
   - [3.8 Resource Groups and Tagging](#38-resource-groups-and-tagging)
   - [3.9 Elastic Load Balancer (ELB)](#39-elastic-load-balancer-elb)
   - [3.10 Creating an EC2 Instance](#310-creating-an-ec2-instance)
   - [3.11 Connecting to an EC2 Instance](#311-connecting-to-an-ec2-instance)
   - [3.12 Installing Software on EC2](#312-installing-software-on-ec2)
   - [3.13 EC2 Section Review](#313-ec2-section-review)

4. [Storage Services (S3)](#4-storage-services-s3)
   - [4.1 Overview of Storage Services](#41-overview-of-storage-services)
   - [4.2 S3 Basics](#42-s3-basics)
   - [4.3 Creating Buckets and Objects](#43-creating-buckets-and-objects)
   - [4.4 S3 Permissions](#44-s3-permissions)
   - [4.5 Object Versioning](#45-object-versioning)
   - [4.6 S3 Section Review](#46-s3-section-review)

5. [Virtual Private Cloud (VPC) & Networking](#5-virtual-private-cloud-vpc--networking)
   - [5.1 AWS Global Services — Regions & Availability Zones](#51-aws-global-services--regions--availability-zones)
   - [5.2 VPC Basics](#52-vpc-basics)
   - [5.3 Gateways](#53-gateways)
   - [5.4 Route Tables](#54-route-tables)
   - [5.5 Network Access Control Lists (NACLs)](#55-network-access-control-lists-nacls)
   - [5.6 Subnets](#56-subnets)
   - [5.7 Availability Zones Inside a VPC](#57-availability-zones-inside-a-vpc)
   - [5.8 Route 53](#58-route-53)
   - [5.9 VPC Section Review](#59-vpc-section-review)

6. [Database Services](#6-database-services)
   - [6.1 Overview of Databases](#61-overview-of-databases)
   - [6.2 RDS Basics](#62-rds-basics)
   - [6.3 DynamoDB Basics](#63-dynamodb-basics)
   - [6.4 Provisioning RDS](#64-provisioning-rds)

7. [CloudFormation](#7-cloudformation)
   - [7.1 CloudFormation Basics](#71-cloudformation-basics)
   - [7.2 Using CloudFormation](#72-using-cloudformation)

8. [Management Tools](#8-management-tools)
   - [8.1 Overview of Management Tools](#81-overview-of-management-tools)
   - [8.2 CloudWatch Basics](#82-cloudwatch-basics)
   - [8.3 CloudWatch Metrics and Alarms](#83-cloudwatch-metrics-and-alarms)
   - [8.4 SNS — Simple Notification Service](#84-sns--simple-notification-service)
   - [8.5 CloudTrail](#85-cloudtrail)
   - [8.6 AWS Health Dashboard](#86-aws-health-dashboard)
   - [8.7 Cost Explorer](#87-cost-explorer)
   - [8.8 AWS Trusted Advisor](#88-aws-trusted-advisor)
   - [8.9 Lambda Basics](#89-lambda-basics)
   - [8.10 Management Tools Section Review](#810-management-tools-section-review)

9. [Security Tools](#9-security-tools)
   - [9.1 Overview — Secrets Manager & CloudFront](#91-overview--secrets-manager--cloudfront)
   - [9.2 GuardDuty](#92-guardduty)
   - [9.3 AWS Security Hub](#93-aws-security-hub)

10. [Conclusion](#10-conclusion)
    - [10.1 Course Review](#101-course-review)
    - [10.2 Where to Go from Here](#102-where-to-go-from-here)

---

## 1. Getting Started

### 1.1 Course Introduction

In this course, we'll cover the things that make your **AWS** account essential — the things that get you off the ground quickly and efficiently. This is not necessarily a certification course, but it builds a solid groundwork for one.

**Topics covered in this course:**

| # | Topic |
|---|-------|
| 1 | The power of the **AWS account** — how it works and how to set one up |
| 2 | **IAM** (Identity and Access Management) — controls the *who's who* inside your account |
| 3 | **EC2** (Elastic Cloud Compute) |
| 4 | Storage solutions, specifically **S3** |
| 5 | **VPC** (Virtual Private Cloud) — the bubble that holds it all together |
| 6 | Database services — **RDS** and **DynamoDB** |
| 7 | **CloudFormation** — automates how you build your environment |
| 8 | Management tools — small tools that make a giant difference |
| 9 | Security — **Security Hub** and **GuardDuty** |
| 10 | Conclusion and where to go from here |

---

### 1.2 Overview of AWS Accounts & Free Tier

**Key terms:** `AWS account`, `Free Tier`, `cloud computing`, `AWS Organizations`, `Lambda`, `SNS`, `Security Hub`, `GuardDuty`, `Trusted Advisor`

An **AWS account** is the foundation — without it, you can't enter the cloud computing space. Everything is accessible through the **console**, and with **AWS Organizations**, multiple accounts can be managed from one place.

#### AWS Free Tier — Four Categories

| Category | Description | Examples |
|----------|-------------|---------|
| **Free with soft limits** | Set limit for the first **12 months** | 5 GB storage in **S3**, certain EC2 instance hours |
| **Always free** | Free even after 12 months | First 1 million requests with **Lambda**; 1 million notification requests via **SNS** |
| **Trial basis** | Shorter than 12-month window | **Security Hub**, **GuardDuty** — 30-day free trial |
| **Free with upgrade option** | Basic tier free, premium available | **AWS Trusted Advisor** — basic checks free, deeper checks require upgrade |

> **Tip:** Check the AWS Free Tier documentation page monthly — it grows as new services are added.

---

### 1.3 Creating an AWS Account & Navigating the Console

**Key terms:** `root account`, `root email`, `console`, `sandbox`, `ACG`, `IAM`

#### Creating an AWS Account — 3 Steps

1. Navigate to the **AWS website**
2. Fill out the **account form** (root email, account name, personal info, credit card)
3. **Confirm your email address**

#### Console Navigation Tips

- Use the **search bar** to find any service (e.g., type `EC2`, then star ★ it to pin to the bookmark bar)
- **Recently visited** section provides quick access to services used before
- **Training and certification** section links to AWS learning paths

#### ACG Cloud Sandbox

The **A Cloud Guru (ACG)** platform offers **sandbox environments** — pre-configured AWS accounts with:
- A `cloud_user` **IAM** user and password
- **Access keys** for CLI use
- No credit card required — ideal for hands-on practice
- Some limitations on **IAM** and security settings

> Open the sandbox in an **incognito window** to avoid session conflicts.

---

### 1.4 Leveraging Billing Alerts

**Key terms:** `billing alert`, `budget`, `CloudWatch`, `AWS Budgets`, `EstimatedCharges`, `SNS`, `alarm`

A **billing alert** monitors your environment to prevent unexpected charges. It lets you set a **budget** and receive notifications before you exceed it.

**Why use billing alerts?**
- **Security and peace of mind** — no surprise bills
- Always know your account costs via the **notification system**

#### Setting Up a Budget (AWS Budgets)

1. Navigate to **AWS Budgets** via the search bar
2. Click **Create budget** → Use a template
3. Choose a template type:

| Template | Use Case |
|----------|----------|
| **Daily savings plan** | Monitor daily spend targets |
| **Zero spend budget** | Ideal for Free Tier users — alerts at $0.01 |
| **Monthly cost budget** | Alerts at 85% of budget and 100% forecasted |

#### Setting Up a Billing Alarm (CloudWatch)

1. Navigate to **CloudWatch** → **Billing**
2. Create an alarm with metric `EstimatedCharges`
3. Set threshold (e.g., `> $15 USD`)
4. Link to an **SNS topic** for email notifications
5. Name the alarm (e.g., `Spend over $15`)

---

### 1.5 AWS Documentation

**Key terms:** `whitepapers`, `developer guide`, `documentation`, `SNS`, `RDS`, `Amazon Polly`

**AWS documentation** (whitepapers) provides detailed instructions for every AWS service — written by technical writers who make complex ideas accessible.

**Why use it?**
- **AWS is constantly growing** — new services and features are added regularly
- **Services change** — UI updates, output changes, and new options are documented
- Recommended: review documentation for services you use **at least once a month**

**How to find it:**
- In the console: **Getting Started with AWS** → AWS Documentation
- Google: `aws [service name] documentation` (e.g., `aws sns documentation`)
- Use the **developer guide** for deep dives into specific services

---

## 2. Identity and Access Management (IAM)

### 2.1 What IAM Is

**Key terms:** `IAM`, `identity and access management`, `users`, `groups`, `policies`, `roles`

**IAM** stands for **Identity and Access Management**. It controls *who can do what and where* inside your AWS account.

- **Best practice for security** — people only access what they need
- Allows **services to interact** with each other securely
- Acts as the main entrance — controls all access to your AWS resources

**IAM covers:**
- Provisioning for the first time (MFA, root account security)
- Creating **users**, **groups**, and **policies**
- Establishing **IAM roles**

---

### 2.2 Provisioning IAM for the First Time

**Key terms:** `MFA`, `multi-factor authentication`, `root account`, `access keys`, `password policy`, `Virtual MFA`, `RSA token`

#### Multi-Factor Authentication (MFA)

**MFA** adds an extra protection layer when logging in — a **best practice** for all AWS accounts.

**Types of MFA:**
| Type | Description |
|------|-------------|
| **Virtual MFA** | Authenticator app on phone or computer (scan QR code) |
| **Security key** | Physical device like an RSA token |
| **Hardware device** | Other hardware MFA options |

#### Securing the Root Account — 3 Key Steps

1. **Access keys** — Avoid access keys on the **root account** entirely (major security risk). If required, rotate them **monthly**.
2. **Strong passwords** — Minimum 8 characters; include uppercase, lowercase, numbers, and symbols
3. **MFA** — Enable **multi-factor authentication** on the root account

#### Password Policy Settings (Account Settings)

- Minimum password length (default: **8 characters**)
- Require uppercase, lowercase, numbers, non-alphanumeric characters
- Set **password expiration** (default: **90 days**)
- Require admin reset on expiry, or allow users to self-reset
- **Prevent password reuse** (e.g., cannot reuse last 5 passwords)

---

### 2.3 Creating Users, Groups, and Policies

**Key terms:** `users`, `groups`, `policies`, `identities`, `inline policy`, `least privilege`, `S3`, `EC2`, `CloudWatch`, `SNS`, `programmatic access`, `management console access`

#### Users, Groups, and Policies — Key Differences

| Concept | Description |
|---------|-------------|
| **Users** | Individual identities (e.g., Bree, Tina) — track who does what |
| **Groups** | Collections of users (e.g., HR, IT) — apply shared **policies** |
| **Policies** | Permission sets — control what actions identities can take |

#### Why Use Multiple Users?
- **Security** — track individual actions inside the account
- **Easier maintenance** — users change own passwords; targeted notifications (e.g., auto-scaling alerts go to IT, not HR)

#### Why Use Groups?
- **Least privilege** — people only access what they need
- **Efficiency** — add a new person to a group and they instantly inherit all required permissions

#### Why Use Custom Policies?
- **Best practice:** Attach **policies** to **groups**, not individual users (inline policies on users can create security gaps)
- Policy structure: **resource** → **action** → **effect** (Allow/Deny)

#### Demo: Creating User "Tina" (IT Team)

1. Go to **IAM** → Users → **Add users**
2. Name: `Tina`
3. Access type: **Programmatic access** (CLI/API) + **Management Console** access
4. Password: Auto-generated, require reset on first login (**best practice**)
5. Add to group: `IT` (has `AmazonEC2FullAccess`, `CloudWatchFullAccess`, `SNSFullAccess`)
6. Add tags (e.g., `Company: Company A`)
7. Download **CSV file** with access key, secret key, login URL

#### Demo: Creating Group "HR" with Custom Policy

1. Create group `HR`, add user `Bree`
2. Assign `S3ReadOnlyAccess` (or `S3FullAccess` if write needed)
3. Create a **custom policy** (e.g., `Updated-HR`):
   - Service: **S3**
   - Actions: List, Read, Write — **uncheck Delete**
   - Resource: Any (or specific bucket ARN)
4. Attach `Updated-HR` to the `HR` group, remove `S3FullAccess`

---

### 2.4 Establishing IAM Roles

**Key terms:** `IAM roles`, `temporary access`, `EC2`, `S3`, `Lambda`, `trusted entity`, `EC2FullAccess`

**IAM roles** are like policies, but they also allow **services to have access to each other** and grant **temporary access** to users.

#### Identities vs. Policies vs. Roles

| Type | Purpose |
|------|---------|
| **Users & Groups** (Identities) | Login credentials; track people in the account |
| **Policies** | Permissions for identities — what they can/can't touch |
| **Roles** | Allow users and **services** to interact; can be **temporary** |

**Example:** A **Lambda** function that needs to call **EC2** instances requires a role:
1. **IAM** → Roles → **Create role**
2. Trusted entity: `AWS service` → **Lambda**
3. Attach policy: `EC2FullAccess`
4. Name: `Function Test`

Result: Lambda can now call EC2 services on your behalf.

> **Roles are temporary** — grant access for a task, then revoke it without changing the user's base permissions.

---

## 3. Elastic Cloud Compute (EC2)

### 3.1 Overview of EC2

**Key terms:** `EC2`, `Elastic Cloud Compute`, `virtual server`, `server rack`, `cloud compute`

**EC2** stands for **Elastic Cloud Compute** — one of the **backbone services** of AWS. It replaces physical on-premises servers with virtual servers in the cloud.

**Benefits of EC2 over on-premises servers:**
- No dedicated server room required
- Pay only for what you use
- Instantly scalable
- Ideal for startups and small businesses

**Topics in this section:**
- EC2 basics (purchasing categories, instance types)
- **AMI** (Amazon Machine Images)
- **EBS** (Elastic Block Storage)
- **Security groups**
- **Auto Scaling**
- **IP addressing**
- **Resource groups and tagging**
- **Elastic Load Balancers (ELB)**
- Creating, connecting to, and installing software on EC2 instances

---

### 3.2 EC2 Basics — Purchasing Categories & Instance Types

**Key terms:** `on-demand`, `saving plans`, `spot instances`, `general purpose`, `compute optimized`, `memory optimized`, `storage optimized`, `accelerated computing`

#### Purchasing Categories

| Category | Description | Best For |
|----------|-------------|----------|
| **On-Demand / Per-Second** | Pay per second; most expensive | Testing, unpredictable workloads |
| **Saving Plans** | Pay upfront, locked-in contract; cheaper | Known, long-term usage |
| **Spot Instances** | Bid on unused capacity; huge discounts | Flexible start/stop, short-term work |

> **Spot instances** shut off if the market price exceeds your bid — ideal only for interruptible workloads.

#### Instance Types

| Type | Characteristics | Use Cases |
|------|-----------------|-----------|
| **General Purpose** | Balanced CPU, memory, storage | Everyday tasks, web servers |
| **Accelerated Computing** | Hardware accelerators | AutoCAD, graphics-heavy developer tasks |
| **Compute Optimized** | High CPU performance | Video transcoding, multimedia |
| **Memory Optimized** | Large RAM | Big data processing, in-memory databases |
| **Storage Optimized** | High I/O, large storage | Compliance reports, data warehouses |

---

### 3.3 Amazon Machine Images (AMI)

**Key terms:** `AMI`, `Amazon Machine Image`, `snapshot`, `backup`, `Amazon Linux`, `key pair`, `t2.micro`

An **AMI** is a pre-configured image of an EC2 instance. It is the foundation from which instances are launched.

**Uses of AMIs:**

| Use | Benefit |
|-----|---------|
| **Backups** | Fast recovery if something goes wrong |
| **Cost control** | Only save what you need; boot a temporary instance without reinstalling software |
| **Consistency** | All instances from the same AMI share identical settings |
| **Snapshot during development** | Roll back to a clean state if new code breaks something |

#### Demo: Creating an AMI

1. Launch an instance (e.g., **Amazon Linux** `t2.micro`)
2. Once running: **Actions** → **Image and templates** → **Create image**
3. Name the image (e.g., `Backup`)
4. Once `Available`, use it: **Launch instances** → paste the AMI ID
5. Alternatively: **AMI section** → **Launch instance from AMI**

---

### 3.4 Elastic Block Store (EBS)

**Key terms:** `EBS`, `Elastic Block Store`, `SSD`, `HDD`, `snapshot`, `volume`, `gp2`, `encryption`, `lifecycle`

**EBS** (**Elastic Block Store**) is attachable storage for **EC2** instances — like a virtual hard drive you can plug in and out.

#### EBS Volume Types

| Type | Description | Use Cases |
|------|-------------|-----------|
| **General Purpose SSD (gp2/gp3)** | Lowest-cost SSD | Virtual desktops, small-scale apps |
| **Provisioned IOPS SSD** | High-performance SSD | Large, mission-critical workloads |
| **Throughput Optimized HDD** | Optimized for big data | Frequently accessed data, big data |
| **Cold HDD** | Lowest cost HDD | File servers, infrequently accessed data |

#### Snapshots

A **snapshot** is a point-in-time copy of an **EBS** volume — perfect for:
- **Redundancy and backups** — don't start from zero after a failure
- **Data recovery** — create a volume from a snapshot
- **Scheduled lifecycle** — automatic daily snapshots at a specific time

#### Demo: Creating and Attaching an EBS Volume

1. **EC2** → **Elastic Block Storage** → **Volumes** → **Create volume**
2. Type: `gp2`, Size: `50 GB`, match the **availability zone** of your instance
3. Add a **tag** (e.g., `Name: Test`)
4. **Actions** → **Attach volume** → select your running instance
5. Device name: `/dev/sdf` (Linux) or a drive letter (Windows)
6. To snapshot: **Actions** → **Create snapshot** → name it (e.g., `Mission Crit`)

---

### 3.5 Security Groups

**Key terms:** `security group`, `inbound rules`, `outbound rules`, `SSH`, `HTTP`, `HTTPS`, `port 80`, `port 443`, `port 22`, `bastion`, `private IP`, `public IP`

**Security groups** act as the primary firewall for **EC2** instances — controlling what traffic can reach your resources.

**Key characteristics:**
- Can only specify **allow** rules (no explicit deny)
- Shared across resources (**RDS**, **Lambda**, **EC2**)
- If you have connectivity issues, **check security groups first**

**Common Rules:**

| Rule Type | Port | Use Case |
|-----------|------|----------|
| **SSH** | 22 | Linux instance access |
| **RDP** | 3389 | Windows instance access |
| **HTTP** | 80 | Public website access |
| **HTTPS** | 443 | Secure website access |

#### Demo: Adding a Security Rule

1. **EC2** → **Security Groups** → select group
2. **Edit inbound rules** → **Add rule**
3. Type: `SSH`, Source: `Custom` → paste the **Bastion IP**
4. **Save rules**

> A **bastion host** (public IP) is used to connect into private instances — the bastion acts as a secure entry point.

---

### 3.6 Auto Scaling

**Key terms:** `Auto Scaling group`, `launch template`, `launch configuration`, `desired capacity`, `minimum capacity`, `maximum capacity`, `health checks`, `spot instances`, `on-demand`, `Application Load Balancer`, `target group`

An **Auto Scaling group** allows your environment to dynamically adjust EC2 capacity based on demand.

**Benefits:**
- **Efficiency** — automation triggers scale-out at specific times or CPU thresholds
- **Health** — constant health checks; unhealthy instances are terminated and replaced
- **Cost control** — only run what you need

#### Capacity Settings

| Setting | Description |
|---------|-------------|
| **Desired capacity** | Target number of instances to maintain |
| **Minimum capacity** | Lowest the group will scale in to |
| **Maximum capacity** | Highest the group will scale out to |

#### Demo: Creating an Auto Scaling Group

1. **EC2** → **Auto Scaling** → **Launch Configurations** → **Create launch template**
   - Name: `Webserver`, select an existing **AMI**, instance type: `t1.micro`
   - Select existing **security group**
2. **Auto Scaling Groups** → **Create Auto Scaling Group**
   - Select the `Webserver` template
   - Choose **subnets** (select all availability zones)
   - Attach a new **Application Load Balancer**
   - Set **Desired: 2**, **Minimum: 1**, **Maximum: 4**
   - (Optional) Add **SNS notification** for scaling events

---

### 3.7 IP Addressing

**Key terms:** `IP address`, `public IP`, `private IP`, `IPv4`, `bastion host`, `subnet`, `VPC`

**IP address** (Internet Protocol address) — the identifier for your resources in both your **VPC** and on the internet.

| Type | Accessibility | Security |
|------|---------------|----------|
| **Public IP** | Accessible from anywhere | Less secure; exposed to the internet |
| **Private IP** | Only accessible within the network | More secure; not reachable from outside |

**Access pattern:**
1. Log into the **public instance** (via public IP)
2. From inside the network, use the **private IP** to connect to private instances

#### Demo: Launching a Bastion Server

1. **EC2** → **Launch instance** → name: `Bastion server`
2. Instance type: `t2.micro`, add **key pair**
3. Network settings: select **project VPC**, **public subnet**
4. **Auto-assign public IP**: enabled
5. Select existing **security group**

---

### 3.8 Resource Groups and Tagging

**Key terms:** `resource group`, `tagging`, `Tag Editor`, `CloudFormation stack`, `tag-based`, `key-value`, `patching`, `EC2`, `RDS`

**Resource groups** are collections of instances grouped together by:
- Project membership
- Patching schedule
- Creation time or team ownership

**Three reasons to use resource groups:**

| Reason | Benefit |
|--------|---------|
| **Organization** | Group instances by team or project |
| **Security** | Notate deletion dates, responsible teams |
| **Efficiency** | Easier patching, automation filtering |

#### Tags — Key Concepts

A **tag** is a key-value pair attached to a resource (e.g., `Project: Website`, `OS: Linux`, `Department: IT`).

**Best practices:**
- Add tags to **EBS volumes** so you can track them across instances
- Use **Tag Editor** (`Resource Groups & Tag Editor` service) to bulk-tag resources
- Tags drive **resource group** membership

#### Demo: Creating a Resource Group

1. Go to **Resource Groups & Tag Editor** → **Tag Editor**
2. Select region (`us-east-1`), Resource type: `EC2::Instance`
3. **Search resources** → add tags (e.g., `OS: Linux`)
4. **Create Resource Group** → Tag-based → filter by `OS: Linux`
5. Name group `Linux` → **Create group**

---

### 3.9 Elastic Load Balancer (ELB)

**Key terms:** `ELB`, `Elastic Load Balancer`, `Application Load Balancer`, `Network Load Balancer`, `target group`, `health check`, `internet-facing`, `private subnet`, `Route 53`, `A record`, `DNS`, `port 80`, `port 443`

**ELB** (**Elastic Load Balancer**) distributes traffic to a set of backend instances, ensuring availability and health.

#### ELB Types

| Type | Location | Context-Aware | Traffic Capacity | Use Case |
|------|----------|---------------|-----------------|----------|
| **Application Load Balancer** | Internet-facing (public subnets) | Yes — understands HTTP/HTTPS | Moderate | Websites, applications, custom routing |
| **Network Load Balancer** | Private subnets | No — routes by IP/port only | Very high | High-throughput, low-latency traffic |

#### Demo: Creating an Application Load Balancer

1. **EC2** → **Load Balancing** → **Target Groups** → **Create target group**
   - Type: `Instances`, Name: `Websites`, Protocol: `HTTP`, Port: `80`
   - Add both EC2 instances as pending targets
2. **Load Balancers** → **Create Load Balancer** → **Application Load Balancer**
   - Name: `Website`, Scheme: `Internet-facing`, IP type: `IPv4`
   - Select **availability zones** and **security group**
   - Listener: `HTTP:80` → Forward to `Websites` target group
3. After creation, copy the **DNS name** → use in **Route 53** as an `A record`

> **Unhealthy hosts** in target groups means traffic cannot flow. Use **CloudWatch** alarms to be notified of unhealthy targets.

---

### 3.10 Creating an EC2 Instance

**Key terms:** `EC2 wizard`, `Amazon Linux`, `t2.micro`, `key pair`, `security group`, `VPC`, `subnet`, `public IP`, `EBS volume`, `Auto Scaling group`, `bootstrap`, `user data`, `termination protection`, `stop protection`

#### Steps to Launch an EC2 Instance

1. **EC2** → **Launch instance**
2. **Name** the instance (e.g., `Test`)
3. **AMI**: Amazon Linux 2 (`t2.micro` — **Free Tier** eligible)
4. **Key pair**: select existing or create new (download `.pem` file)
5. **Network settings**: default **VPC**, default subnet
6. **Security group**: Allow **SSH** from My IP; optionally allow **HTTP** and **HTTPS**
7. **Storage**: 8 GB `gp2` (default)
8. **Advanced details** (optional):
   - **IAM profile**, **spot instance**, **shutdown behavior** (stop or terminate)
   - **Termination protection** — prevents accidental deletion
   - **Stop protection** — prevents accidental stop
   - **User data** — bootstrap scripts to pre-install software
9. Click **Launch instance**

---

### 3.11 Connecting to an EC2 Instance

**Key terms:** `SSH`, `PuTTY`, `PuTTYgen`, `PEM key`, `PPK key`, `RDP`, `Remote Desktop`, `ec2-user`, `Session Manager`, `SSM role`, `chmod 400`, `bastion host`

#### Connection Methods by OS

**Linux/Mac → Linux EC2:**
```bash
chmod 400 Test.pem
ssh -i Test.pem ec2-user@<PUBLIC_IP>
```

**Windows → Linux EC2 (via PuTTY):**
1. Open **PuTTYgen** → Load `.pem` key → Save as `.ppk`
2. Open **PuTTY** → Enter public IP
3. **Connection** → **Data**: username = `ec2-user`
4. **SSH** → **Auth**: browse to `.ppk` file
5. Click **Open** (optionally save session as `maintenance`)

**Windows/Mac → Windows EC2 (RDP):**
1. **EC2** → Instance → **Connect** → **RDP client**
2. Copy **public DNS**
3. Open **Remote Desktop Connection** (Windows) or **Microsoft Remote Desktop** (Mac)
4. Enter DNS, username: `Administrator`
5. **Get password** from console (requires `.pem` key) → **Decrypt password**
6. Connect and accept the certificate warning

**Browser (Session Manager):**
- Requires **SSM role** attached to the instance
- Connect from **EC2** → **Connect** → **Session Manager**
- Useful for quick edits; no SSH key needed

---

### 3.12 Installing Software on EC2

**Key terms:** `yum`, `httpd`, `Apache`, `IIS`, `systemctl`, `Web Platform Installer`, `sudo`, `root user`, `NGINX`, `WordPress`

#### Linux — Install Apache (httpd)

```bash
sudo -i                          # Switch to root user
yum install httpd -y             # Install Apache
httpd -t                         # Syntax check
systemctl start httpd            # Start Apache
systemctl status httpd           # Verify running
systemctl enable httpd           # Auto-start on reboot
```

#### Windows — Install IIS

1. Open **Microsoft Edge** → download **Web Platform Installer**
2. Install the extension and open it
3. Accept the license → click **Add** next to IIS
4. Click **Install** and follow the prompts

---

### 3.13 EC2 Section Review

**Topics covered:**
- EC2 overview — what it is and server basics
- Purchasing categories and instance types
- **AMIs** — backups and environment snapshots
- **EBS** — storage solutions and volume types
- **Security groups** — locking down access
- **Auto Scaling** — dynamic scaling in/out
- **IP addresses** — public vs. private
- **Resource groups and tagging** — organization
- **Load balancing** — high availability traffic routing
- Creating, connecting to, and installing software on instances

---

## 4. Storage Services (S3)

### 4.1 Overview of Storage Services

**Key terms:** `S3`, `Simple Storage Service`, `bucket`, `object`, `versioning`, `encryption`, `replication`, `durability`

**S3** (**Simple Storage Service**) is AWS's virtually unlimited object storage — like a cargo hold for your data. Each object can be up to **5 TB** in size.

**Why use S3?**

| Benefit | Detail |
|---------|--------|
| **Reliability** | 99.9% durability — very low chance of data loss |
| **Unlimited space** | Virtually no storage limit |
| **Cost effective** | Cheaper than managing on-premises storage |
| **Easy protection** | One-click **encryption**, **versioning**, simple **replication** |

---

### 4.2 S3 Basics

**Key terms:** `bucket`, `object`, `versioning`, `encryption`, `static website`, `access control`

S3 **buckets** are containers for your data. Like a physical bucket, they hold items that can be shared, retrieved, and organized.

**Customization Options:**

| Feature | Description |
|---------|-------------|
| **Encryption** | One-click to encrypt the entire bucket; only key holders can access |
| **Static website hosting** | Host simple HTML websites directly from a bucket |
| **Versioning** | Keep multiple versions of an object; restore previous versions if needed |
| **Access control** | Fine-grained permissions on who can read/write/delete |

---

### 4.3 Creating Buckets and Objects

**Key terms:** `bucket name`, `globally unique`, `ACL`, `public access`, `versioning`, `Object Lock`, `encryption`, `upload`, `ARN`, `S3 URL`

#### Creating a Bucket

1. **S3** → **Create bucket**
2. **Bucket name** — must be **globally unique**, lowercase, no uppercase letters
3. **ACLs** — disabled (recommended)
4. **Block public access** — leave enabled (private by default)
5. **Versioning** — enable if needed (cannot be disabled once enabled)
6. **Encryption** — enable if needed
7. **Object Lock** — makes objects read-only once written
8. Click **Create bucket**

#### Uploading Objects

Two methods:
- **Add files** button → browse your filesystem
- **Drag and drop** into the bucket interface

After upload, you can see:
- File size and type
- **ARN** (Amazon Resource Name)
- **S3 URL** (for CLI access)
- Access status and **versioning** info

---

### 4.4 S3 Permissions

**Key terms:** `bucket policy`, `ARN`, `Principal`, `Action`, `Effect`, `Allow`, `Deny`, `Policy Generator`, `IAM`, `s3:DeleteBucket`

S3 permissions have three components:

| Component | Description | Example |
|-----------|-------------|---------|
| **Resource** | What is being affected | S3 bucket `awsessentials` |
| **Action** | What can be done | `s3:DeleteBucket`, `s3:PutObject` |
| **Effect** | Allow or Deny the action | `"Effect": "Deny"` |

#### Demo: Creating a Bucket Policy (deny delete)

1. **S3** → select bucket → **Properties** → copy **ARN**
2. **Permissions** → **Edit** → use **Policy Generator**
3. Set:
   - Service: `S3 Bucket`
   - **Principal**: paste IAM user ARN (from **IAM** → Users → select user → copy ARN)
   - Effect: `Deny`
   - Action: `s3:DeleteBucket`
   - Resource: paste bucket **ARN**
4. Click **Add Statement** → **Generate Policy** → copy JSON → paste and save

---

### 4.5 Object Versioning

**Key terms:** `versioning`, `version ID`, `null version`, `delete marker`, `restore`, `bucket`

**Object versioning** stores multiple versions of the same object in a bucket — the safest way to protect S3 data.

**Benefits:**
- Restore a previous version if the wrong file is uploaded
- Control who can delete or change versions
- Recover accidentally deleted files

> ⚠️ Once **versioning** is enabled on a bucket, it **cannot be disabled** — only suspended.

#### Demo: Using Versioning

1. Upload `ACG_Test.txt` with content `ACG Test 1`
2. Click the file → **Versions** tab — see version 1
3. Edit file → content `ACG Test 2` → upload again
4. **Versions** tab now shows two versions
5. Delete the newer version: check it → **Delete** → type `permanently delete`
6. Download the file — it now contains `ACG Test 1` again ✓

---

### 4.6 S3 Section Review

**Topics covered:**
- What **S3** is and how it works
- **Buckets**, **versioning**, **encryption**, static website hosting
- Creating buckets and uploading objects
- **S3 permissions** — using the **Policy Generator**
- **Object versioning** in practice — restoring previous versions

---

## 5. Virtual Private Cloud (VPC) & Networking

### 5.1 AWS Global Services — Regions & Availability Zones

**Key terms:** `data center`, `region`, `availability zone`, `redundancy`, `North Virginia`, `Ohio`, `Ireland`

| Concept | Description |
|---------|-------------|
| **Data center** | Physical location holding servers — large rooms filled with server racks |
| **Region** | Physical location where data centers reside (e.g., North Virginia, Ohio, Ireland) |
| **Availability Zone (AZ)** | One or more data centers with redundancies in separate facilities |

**Best practice:** Deploy resources across at least **two availability zones** per region for high availability.

- At least **1–2 data centers** per **availability zone**
- At least **2 availability zones** per **region**

---

### 5.2 VPC Basics

**Key terms:** `VPC`, `Virtual Private Cloud`, `CIDR`, `subnet`, `route table`, `internet gateway`, `S3 endpoint`, `DHCP`, `NAT gateway`, `NACL`, `security group`

**VPC** (**Virtual Private Cloud**) contains the majority of your AWS resources — **EC2**, **RDS**, **S3** — and gives you control over who connects to what.

**Common VPC resources:**

| Resource | Purpose |
|----------|---------|
| **Subnets** | Segments of the VPC — public or private |
| **Route tables** | Direct traffic within and outside the VPC |
| **Internet gateway** | Connects public subnets to the internet |
| **NAT gateway** | Allows private subnet instances to reach the internet |
| **NACLs** | Subnet-level firewall |
| **Security groups** | Instance-level firewall |
| **DHCP options** | IP address assignment settings |

#### Demo: Creating a VPC

1. **VPC** → **Your VPCs** → **Create VPC** → select **VPC and more**
2. Name: `project`, CIDR: `10.0.0.0/24` (256 IPs, vs /16 which gives 65,536)
3. Availability zones: **2** (best practice — 3 for extra stability)
4. Public subnets: **2**, Private subnets: **2**
5. NAT gateway: None (for demo)
6. Enable **DNS hostnames** and **DNS resolutions** (required for websites)
7. Click **Create VPC**

---

### 5.3 Gateways

**Key terms:** `internet gateway`, `NAT gateway`, `transit gateway`, `public subnet`, `private subnet`, `Elastic IP`, `ASN`, `DNS support`, `route propagation`

Three main gateway types in AWS:

#### Internet Gateway
- Connects **public subnets** to and from the internet
- One internet gateway can serve multiple **VPCs**

#### NAT Gateway
- Allows **private subnet** instances to reach the internet **without** accepting inbound connections
- **Public NAT gateway**: instances get internet access via an **Elastic IP**
- **Private NAT gateway**: connects private subnets to on-premises resources or other **VPCs**

#### Transit Gateway
- Central communication point between **on-premises** resources and the cloud
- Simplifies connections — single routing point
- Better visibility across hybrid environments
- Scales independently as your environment grows

#### Demo: Creating a NAT Gateway

1. **VPC** → **NAT gateways** → **Create NAT gateway**
2. Name: `Nat`, select a **private subnet**, Connection type: `Private`
3. Click **Create NAT gateway**

#### Demo: Creating a Transit Gateway

1. **VPC** → **Transit gateways** → **Create transit gateway**
2. Name: `Transit`
3. Enable: **DNS support**, **Default route association**, **Default route propagation**
4. Click **Create** — waits in `Pending` then moves to `Available`

---

### 5.4 Route Tables

**Key terms:** `route table`, `routing`, `DNS lookup`, `Route 53`, `default route`, `internet gateway`, `NAT gateway`, `VPC peering`, `S3 endpoint`, `subnet association`, `main route table`

A **route table** is a list of directions — it tells network traffic where to go.

| Routing Scope | Analogy |
|---------------|---------|
| **DNS** (global) | Galaxy — everything online |
| **Route 53** (account-wide) | Solar system — account-level domain management |
| **Route tables** (local) | Street map — local VPC routing |

**Route table destinations:**
- `0.0.0.0/0` → **Internet gateway** (for public subnets)
- `0.0.0.0/0` → **NAT gateway** (for private subnets reaching the internet)
- VPC CIDR (e.g., `10.0.0.0/16`) → **local** (same-VPC traffic)
- Other CIDRs → **VPC peering**, **S3 endpoint**, **DynamoDB endpoint**

**Best practice:** Customize your **route table** — explicitly define where traffic goes rather than relying on defaults.

---

### 5.5 Network Access Control Lists (NACLs)

**Key terms:** `NACL`, `network access control list`, `firewall`, `inbound rules`, `outbound rules`, `subnet`, `rule number`, `allow`, `deny`, `port 80`, `port 443`, `port 22`

**NACLs** act as a **firewall at the subnet level** — they control traffic entering and leaving subnets.

**Key differences from Security Groups:**

| Feature | NACL | Security Group |
|---------|------|----------------|
| Level | **Subnet** | Instance |
| Rule types | Allow **and** Deny | Allow only |
| Rule evaluation | Sequential by **rule number** | All rules evaluated together |
| Applies to | All resources in subnet | Specific instances |

#### Rule Numbering

Rules are evaluated in **ascending numeric order** (100, 110, 120…):
- Rule 100 → checked first
- If no match → falls to the next rule
- Last rule (`*`) → **Deny all** (default, not editable)

#### Demo: Creating a NACL

1. **VPC** → **Network ACLs** → **Create network ACL**
2. Name: `NACL2`, associate with all subnets
3. **Edit inbound rules**:

| Rule # | Type | Port | Source | Action |
|--------|------|------|--------|--------|
| 100 | HTTP | 80 | 0.0.0.0/0 | Allow |
| 110 | HTTPS | 443 | 0.0.0.0/0 | Allow |
| 120 | SSH | 22 | 0.0.0.0/0 | Allow |

4. **Edit outbound rules**: Rule 100 → All traffic → Allow

> Always check your **NACLs** and **security groups** first when troubleshooting connectivity issues.

---

### 5.6 Subnets

**Key terms:** `subnet`, `public subnet`, `private subnet`, `CIDR`, `availability zone`, `NACL`, `NAT gateway`, `internet gateway`, `route table`

**Subnets** are the segments inside a **VPC** where resources actually live.

| Type | Characteristics |
|------|-----------------|
| **Public subnet** | Has a route to an **internet gateway**; resources can have public IPs |
| **Private subnet** | No direct internet access; uses **NAT gateway** to reach the internet |

#### Traffic Flow

```
Public subnet → NACL → Router → Internet Gateway → Internet
Private subnet → NACL → NAT Gateway → Router → Public subnet resources
```

#### Demo: Creating a Subnet

1. **VPC** → **Subnets** → **Create subnet**
2. Select **Test VPC** (CIDR: `10.0.0.0/16`)
3. Name: `My-subnet`, AZ: `us-east-1f`
4. CIDR: `10.0.0.0/24` (must be smaller than `/16`, so use `/24` or higher)
5. Click **Create subnet** → 251 available IP addresses

> To make a subnet **public**, create an **internet gateway** and add a route in the **route table** pointing `0.0.0.0/0` to the gateway.

---

### 5.7 Availability Zones Inside a VPC

**Key terms:** `availability zone`, `high availability`, `redundancy`, `subnet`, `VPC`, `public subnet`, `private subnet`, `route table`

**Availability zones** are isolated physical locations within a **region** — distributing resources across AZs provides **high availability** and **redundancy**.

**Configuration recommendation:**
- At least **2 availability zones** per VPC
- Each AZ should have one **public** and one **private** subnet
- Each **private subnet** gets its own **route table**
- All **public subnets** share one **public route table** pointing to the **internet gateway**

#### Demo: Launching Instance into a Specific AZ

1. **EC2** → **Launch instance**
2. **Network settings** → select the new VPC
3. Choose subnet in desired AZ (e.g., public subnet in `us-east-1f`)
4. Launch — the instance **availability zone** confirms `us-east-1f`

---

### 5.8 Route 53

**Key terms:** `Route 53`, `DNS`, `domain name`, `A record`, `CNAME`, `MX record`, `name server`, `hosted zone`, `private hosted zone`, `PTR`, `TXT`, `SSL`

**Route 53** maps **domain names** to **IP addresses**, controlling network traffic for your applications.

#### Common Record Types

| Record Type | Full Name | Use Case |
|-------------|-----------|---------|
| **A record** | Address record | Maps domain name → IPv4 address |
| **CNAME** | Canonical Name | Maps one domain to another (e.g., `www.` → root domain) |
| **NS** | Name server | Tracks where domain records are located |
| **MX** | Mail Exchange | Custom email server routing |
| **PTR** | Pointer | Reverse DNS lookup |
| **TXT** | Text | SSL verification, sender verification |

#### Demo: Creating a Hosted Zone and A Record

1. **Route 53** → **Hosted zones** → **Create hosted zone**
2. Domain: `AWSessentials`, Type: **Private hosted zone**
3. Select VPC: `Test VPC`, Region: `N. Virginia`
4. Click **Create hosted zone** (NS records auto-generated)
5. **Create record** → **A record**
6. Get the **public IP** of your EC2 web server → paste as the **Value**
7. Click **Create record**

> In a **public zone**, domain names would include `.com` or `.org`. In a **private zone**, internal names are used.

---

### 5.9 VPC Section Review

**Topics covered:**
- **AWS global services** — data centers, regions, availability zones
- **VPC basics** — creation and structure
- **Gateways** — internet, NAT, transit
- **Route tables** — routing logic
- **NACLs** — subnet-level firewall
- **Subnets** — public vs. private
- **Availability zones** — high availability design
- **Route 53** — DNS and record types

---

## 6. Database Services

### 6.1 Overview of Databases

**Key terms:** `database`, `relational database`, `NoSQL`, `serverless`, `inventory`, `user base`, `rows`, `columns`

A **database** is an organized collection of data — rows and columns of structured information. It can be:
- **Server-based** — traditional database on a managed instance
- **Serverless** — specialized, managed, no underlying server to manage

**Common use cases:**
- E-commerce inventory / order management
- Website user account storage
- Financial records and invoices

---

### 6.2 RDS Basics

**Key terms:** `RDS`, `Relational Database Service`, `SQL`, `NoSQL`, `DQL`, `query`, `data definition`, `data manipulation`, `data control`, `transactional control`, `EC2`, `scaling`

**RDS** (**Relational Database Service**) is a managed database service. AWS handles underlying hardware monitoring and scaling.

**Why RDS over self-managed EC2 database?**
- AWS monitors **hardware utilization** automatically
- Easy to **scale up or down** based on demand
- No need to patch or maintain the OS yourself

#### SQL vs. NoSQL

| Type | Structure | Query Method | Example |
|------|-----------|--------------|---------|
| **SQL** | Tables (rows and columns) | Complex **SQL** queries | MySQL, PostgreSQL |
| **NoSQL** | Unstructured | Simple key lookups, documents | **DynamoDB**, MongoDB |

#### SQL Query Types (DQL — Data Query Language)

| Query Type | Commands | Purpose |
|------------|----------|---------|
| **Data Definition** | CREATE, MODIFY | Add tables, columns |
| **Data Manipulation** | SELECT, UPDATE, DELETE | Retrieve or change data |
| **Data Control** | GRANT, REVOKE | Control who sees what |
| **Transactional Control** | COMMIT, ROLLBACK | Save or undo changes |

---

### 6.3 DynamoDB Basics

**Key terms:** `DynamoDB`, `NoSQL`, `key-value`, `document`, `DynamoDB Accelerator`, `partition key`, `sort key`, `JSON`, `XML`, `latency`

**DynamoDB** is AWS's fully managed **NoSQL** database — low latency, serverless, and highly scalable.

**Two main NoSQL database types:**

| Type | Description | Use Case |
|------|-------------|---------|
| **Key-value pair** | Associates data with a key for fast lookup | Indexing, references |
| **Document** | Stores entries in JSON or XML format | Flexible schemas, PDFs, graphics |

#### DynamoDB Table Structure Example

| Partition Key | Sort Key | Value |
|---------------|----------|-------|
| Shuttle-1 | Package | Food |
| Shuttle-2 | Box | Tools |
| Shuttle-3 | Package | Parts |

- **Partition key** — where items are going (e.g., `Shuttle-1`)
- **Sort key** — how to sort (e.g., `Package`, `Box`)
- **Value** — the actual data

**DynamoDB Accelerator (DAX)** — provides extremely low latency for read-heavy workloads.

---

### 6.4 Provisioning RDS

**Key terms:** `RDS`, `PostgreSQL`, `MySQL`, `Free Tier`, `Multi-AZ`, `Single-AZ`, `burstable class`, `master password`, `EC2 connection`, `storage`, `security group`, `password authentication`, `IAM authentication`

#### Steps to Create an RDS Instance

1. **RDS** → **Create database**
2. Creation method: **Standard create**
3. Engine: **PostgreSQL** (Free Tier eligible)
4. Template: **Free tier** (Single DB instance; no Multi-AZ)

> **Multi-AZ** = multiple availability zones — better for preventing outages; use for Production.

5. DB identifier: `database-1`
6. **Master username** and **password** (auto-generate for best security)
7. Instance class: `Burstable class` (Free Tier)
8. Storage: `200 GB` (up to `1000 GB` max auto-scaling threshold)
9. Connectivity: no EC2 connection (or connect to an EC2 for app backend)
10. Public access: **No**
11. Security group: default
12. Authentication: **Password authentication**
13. Click **Create database**

---

## 7. CloudFormation

### 7.1 CloudFormation Basics

**Key terms:** `CloudFormation`, `automation`, `template`, `stack`, `consistency`, `security`, `deployment`, `JSON`, `YAML`

**CloudFormation** is AWS's **infrastructure-as-code** service — it automates the creation of AWS resources from template files.

**Why use CloudFormation?**

| Benefit | Detail |
|---------|--------|
| **Automation** | Build entire environments without clicking through the console |
| **Consistency** | Same template = identical environment every time |
| **Security** | No human error — encryption steps can't be skipped |
| **Speed** | Deploy a **VPC**, **EC2**, **S3** all at once from one template |
| **Auditing** | Tracks when and where resources were built |

---

### 7.2 Using CloudFormation

**Key terms:** `template file`, `JSON`, `YAML`, `stack`, `S3 bucket`, `stack name`, `rollback`, `outputs`, `parameters`, `resource type`, `CREATE_COMPLETE`, `Mission-Alpha`

#### Template File Structure

CloudFormation templates are written in **JSON** or **YAML** and define:
- **Resource type** — what AWS resource to build (e.g., `S3 Bucket`)
- **Properties** — configuration (e.g., public read access)
- **Outputs** — values returned after creation (e.g., website URL, domain name)

**Example (S3 website bucket template):**
```yaml
Resources:
  S3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      AccessControl: PublicRead
      WebsiteConfiguration:
        IndexDocument: index.html
        ErrorDocument: error.html
Outputs:
  WebsiteURL:
    Value: !GetAtt S3Bucket.WebsiteURL
```

#### Demo: Creating a CloudFormation Stack

1. **CloudFormation** → **Create stack** → **With new resources**
2. Upload a template file (or use **Template designer** for drag-and-drop)
3. Stack name: `Mission-Alpha`
4. Add tags if needed
5. **On failure**: `Roll back all stack resources` (recommended)
6. Click **Create stack**

After creation:
- Stack events show: `S3Bucket CREATE_IN_PROGRESS` → `CREATE_COMPLETE`
- Navigate to **S3** to confirm the `mission-alpha` bucket was created

---

## 8. Management Tools

### 8.1 Overview of Management Tools

**Key terms:** `CloudWatch`, `SNS`, `CloudTrail`, `Health Dashboard`, `Cost Explorer`, `Trusted Advisor`, `Lambda`, `serverless`

Management tools fall into two categories:

| Category | Tools | Purpose |
|----------|-------|---------|
| **Account management** | **Cost Explorer**, **CloudTrail** | Monitor spend; track user activity |
| **Service-to-service** | **Lambda**, **SNS**, **CloudWatch** | React to events; send notifications; trigger automation |

---

### 8.2 CloudWatch Basics

**Key terms:** `CloudWatch`, `alarm`, `monitoring`, `notification`, `OK`, `In alarm`, `Insufficient data`, `EC2`, `SNS`

**CloudWatch** is the primary **monitoring tool** in AWS.

**Two main functions:**
1. **Monitoring** — tracks environment health and efficiency
2. **Notification** — alerts via **SNS** when alarms trigger

#### Alarm States

| State | Meaning |
|-------|---------|
| **OK** (green) | Metric is within normal range |
| **In alarm** (red) | Metric has exceeded the threshold |
| **Insufficient data** (grey) | Not enough data to evaluate (e.g., instance stopped) |

---

### 8.3 CloudWatch Metrics and Alarms

**Key terms:** `metric`, `threshold`, `CPU utilization`, `estimated charges`, `EC2`, `RDS`, `billing alarm`, `SNS topic`, `Auto Scaling`, `terminate`, `reboot`, `stop`

**CloudWatch metrics** let you monitor any measurable attribute of your AWS environment — CPU, network, billing, and more.

#### Creating a CloudWatch Alarm

1. **CloudWatch** → **Alarms** → **Create alarm** → **Select metric**
2. Browse metrics by service (e.g., **EC2**, **Billing**, **RDS**)
3. Example — **Billing alarm for EC2**:
   - Metric: `Estimated Charges` → `EC2`
   - Threshold: `>= $10`
4. **Notifications**: add **SNS topic** for alarm state, OK state, or insufficient data
5. **EC2 actions** on alarm:
   - **Terminate** — stop the instance permanently
   - **Reboot** — restart (resolves out-of-memory errors)
   - **Stop** — gracefully stop the instance (triggers Auto Scaling health check)

> **Auto Scaling integration**: If a **CloudWatch alarm** triggers (e.g., CPU > threshold), it can automatically scale out your **Auto Scaling group** without manual intervention.

---

### 8.4 SNS — Simple Notification Service

**Key terms:** `SNS`, `Simple Notification Service`, `topic`, `subscription`, `protocol`, `email`, `phone`, `event-driven`, `FIFO`, `encryption`, `CloudWatch`, `Lambda`

**SNS** (**Simple Notification Service**) enables app-to-person and app-to-app notifications — the communication layer outside your AWS account.

**Key features:**

| Feature | Benefit |
|---------|---------|
| **Event-driven** | Triggers on events (scaling, alarms, uploads) |
| **Encrypted communications** | Private links for sensitive data |
| **Cost reduction** | Built-in filtering, batch delivery, subscriber management |
| **High durability** | Messages stored across multiple data centers; retry on failure |
| **FIFO support** | First-in, first-out queues reduce duplication and message loss |

#### Demo: Adding SNS to a CloudWatch Alarm

1. **SNS** → **Create topic** → Name: `Alarm`, Type: `Standard`
2. **Create subscription** → Protocol: `Email` → enter your email
3. **Confirm subscription** via email link
4. **CloudWatch** → select alarm → **Actions** → **Edit**
5. **Notifications** → Add: **Alarm state** → **Alarm** SNS topic → **Update alarm**
6. Test: stop the EC2 instance → alarm triggers → email notification received ✓

---

### 8.5 CloudTrail

**Key terms:** `CloudTrail`, `trail`, `API call`, `event log`, `user ID`, `multi-region trail`, `single-region trail`, `S3`, `SNS`, `audit`, `principal ID`, `event record`, `TerminateInstances`, `RunInstances`

**CloudTrail** tracks all user and service activity in your AWS account — every API call generates an event log entry.

**Why use CloudTrail?**

| Reason | Detail |
|--------|--------|
| **Security** | Track who did what — every event includes the **user ID** |
| **Notifications** | Attach **SNS** to alert on specific events |
| **Auditing** | Trails stored in **S3** — export for regulatory/compliance reports |

#### Trail Types

| Type | Coverage | Best Practice? |
|------|----------|----------------|
| **Multi-region trail** | All regions | ✅ Yes — catches events you might miss |
| **Single-region trail** | One region only | ❌ Leaves gaps in monitoring |

#### Demo: Viewing CloudTrail Events

1. **CloudTrail** → **Event history**
2. Filter by **Resource type** → `AWS::EC2::Instance`
3. Find `TerminateInstances` event → click to see:
   - **Event ID** — CloudTrail's tracking number
   - **Event record** — full JSON with action, resource IDs, previous state
   - **Principal ID** — who performed the action
   - **Source IP** — console = `AWS Internal`; CLI/API = your IP address

---

### 8.6 AWS Health Dashboard

**Key terms:** `Health Dashboard`, `instance retirement`, `S3 update`, `event log`, `scheduled changes`, `other notifications`, `service history`, `EC2`, `region`

The **AWS Health Dashboard** provides notifications about events affecting your account and the global AWS infrastructure.

**Notification types:**

| Type | Examples |
|------|---------|
| **Scheduled changes** | Instance retirement, hardware migration |
| **Other notifications** | Billing alerts, certificate rotation, vulnerability notices |
| **Event log** | All recent AWS global events |

**Two ways to access:**
1. Bell icon (🔔) in the console — shows quick alerts
2. Search for `AWS Health` → **AWS Health Dashboard**

**Useful for troubleshooting:** If a service is behaving unexpectedly, check the **Health Dashboard** to determine if it's an AWS-side issue vs. a configuration issue.

---

### 8.7 Cost Explorer

**Key terms:** `Cost Explorer`, `budget`, `monthly budget`, `zero spend budget`, `forecasted spend`, `reports`, `DynamoDB`, `SNS`, `S3`, `CloudWatch`

**Cost Explorer** helps you track and forecast your AWS spending — no more surprise bills.

**Features:**

| Feature | Description |
|---------|-------------|
| **Current spend view** | See what you're spending right now |
| **Forecasted spend** | Estimate future costs and plan ahead |
| **Granular filtering** | Break down costs by service, region, time range |
| **Custom reports** | Monthly costs by service, linked accounts, etc. |

#### Demo: Setting Up Cost Explorer Budgets

1. **Cost Explorer** → **Reports** → **Monthly costs by service**
   - Identify top-spending services (e.g., **DynamoDB**, **SNS**, **S3**)
2. **Budgets** → **Create budget**:
   - **Zero spend budget** → alert at `$0.01` for Free Tier protection
   - **Monthly cost budget** → set amount (e.g., `$20`); alert at 85% and 100%

When budget threshold is crossed, you'll receive an email via **SNS** notification.

---

### 8.8 AWS Trusted Advisor

**Key terms:** `Trusted Advisor`, `security`, `performance`, `cost optimization`, `fault tolerance`, `regulatory compliance`, `S3 public access`, `CloudTrail logging`, `IAM password policy`, `recommendations`, `download checks`

**AWS Trusted Advisor** is your automated account advisor — it scans your environment and recommends improvements.

**Five check categories:**

| Category | Examples |
|----------|---------|
| **Security** | S3 public access, IAM password policy, CloudTrail logging |
| **Performance** | EC2 instance type efficiency, service limits |
| **Cost Optimization** | Low-utilization EC2 instances, idle resources |
| **Fault Tolerance** | Multi-AZ RDS, EBS snapshots |
| **Service Limits** | Usage close to AWS service limits |

**Check result states:**
- 🔴 **Action recommended** — fix this now
- 🟡 **Investigation recommended** — review needed
- 🟢 **No problems detected** — all good

#### Demo: Using Trusted Advisor

1. Search for **Trusted Advisor** → home page shows summary counts
2. Navigate to **Security** → review flagged items
3. Example fix — delete a public **S3** bucket → refresh checks → count improves
4. **Notifications** → add contacts (billing, operations, security) for weekly emails
5. **Download all checks** → Excel spreadsheet for compliance reports

> You can **disable** Trusted Advisor with a single toggle — but it's not recommended.

---

### 8.9 Lambda Basics

**Key terms:** `Lambda`, `serverless`, `event-driven`, `function`, `blueprint`, `test event`, `SNS`, `trigger`, `key-value`, `Hello World`

**Lambda** is a **serverless** compute service — run code without provisioning or managing servers.

**Key characteristics:**
- **Serverless** — no underlying hardware to manage
- **Event-driven** — triggered by events (user login, S3 upload, scheduled time)
- Integrates with **SNS**, **CloudWatch**, **S3**, **DynamoDB**, and more

#### Demo: Creating a Lambda Function

1. **Lambda** → **Create function** → **Use a blueprint** → `Hello World`
2. Name: `Helloworld` → **Create function**
3. Code view shows `return event.key1` — echoes back the first key value
4. **Configure test event**:
   - Event name: `WorldEvent`
   - `key1`: `Hello_World`
5. Click **Test** → Response: `Hello_World` ✓
6. Change `key1` to `Lets go Gurus` → Test → Response: `Let's go Gurus` ✓

**Next step:** Wire a real trigger (e.g., first-time user login) → response sent to **SNS topic** → notification delivered.

---

### 8.10 Management Tools Section Review

**Topics covered:**
- Overview of management tools
- **CloudWatch** basics and alarm setup
- **CloudWatch metrics** — billing, EC2, custom
- **SNS** — topics, subscriptions, CloudWatch integration
- **CloudTrail** — event history, user tracking, audit trails
- **Health Dashboard** — service and account health monitoring
- **Cost Explorer** — spend tracking and budgets
- **Trusted Advisor** — security, performance, cost recommendations
- **Lambda** — serverless, event-driven functions

---

## 9. Security Tools

### 9.1 Overview — Secrets Manager & CloudFront

**Key terms:** `Secrets Manager`, `CloudFront`, `edge location`, `CDN`, `DDoS`, `AWS Shield`, `password rotation`, `hard coding`, `latency`

#### AWS Secrets Manager

**Secrets Manager** stores and manages credentials (passwords, API keys) securely — eliminates the need to **hard-code** secrets in application code.

**Benefits:**
| Benefit | Detail |
|---------|--------|
| **Improved security** | Never put passwords in code that could be pushed to a public repo |
| **Easy rotation** | Rotate secrets without changing application code |
| **Easy integration** | Works across multiple applications and services |

#### Amazon CloudFront

**CloudFront** is a **Content Delivery Network (CDN)** that caches your content at **edge locations** worldwide, reducing latency for end users.

**Benefits:**
| Benefit | Detail |
|---------|--------|
| **DDoS protection** | Works with **AWS Shield** to defend against distributed denial-of-service attacks |
| **Content security** | Only serves your content to authorized locations |
| **Low latency** | Content cached close to users via edge locations |

---

### 9.2 GuardDuty

**Key terms:** `GuardDuty`, `threat detection`, `malware`, `malicious activity`, `security reports`, `remediation`, `compromise`, `account monitoring`

**GuardDuty** is AWS's intelligent threat detection service — it actively monitors your account for signs of unusual activity, malware, or compromise.

**Key features:**
- Continuous **account monitoring** for suspicious activity
- **Detailed security reports** — identifies vulnerabilities and recommends remediation
- Detects **compromised credentials**, unauthorized access, and anomalous behavior

**Why use it?**
- Rapidly identifies **account compromisation** before it causes major damage
- Security reports support **transparency** with customers and reporting bodies
- **30-day free trial** available

---

### 9.3 AWS Security Hub

**Key terms:** `Security Hub`, `best practices`, `compliance`, `standardization`, `custom reports`, `filtering`, `integration`, `support technicians`

**AWS Security Hub** centralizes security findings across your AWS environment, ensuring **best practices** are consistently applied.

**Key features:**
| Feature | Detail |
|---------|--------|
| **Standardization** | Enforces best practices across all accounts and environments |
| **Custom reports** | Filter and surface only the data you need to see |
| **Easy integration** | Connects with outside services and ticketing tools for support teams |
| **30-day free trial** | Available to evaluate before committing |

---

## 10. Conclusion

### 10.1 Course Review

**Topics covered throughout this course:**

| Module | Topic |
|--------|-------|
| 1 | **AWS account** — setup, console navigation, Free Tier |
| 2 | **IAM** — users, groups, policies, roles, MFA |
| 3 | **EC2** — instances, AMIs, EBS, security groups, auto scaling, load balancing |
| 4 | **S3** — buckets, permissions, versioning, encryption |
| 5 | **VPC** — subnets, gateways, route tables, NACLs, Route 53 |
| 6 | **Databases** — RDS, DynamoDB |
| 7 | **CloudFormation** — infrastructure automation with templates |
| 8 | **Management tools** — CloudWatch, SNS, CloudTrail, Cost Explorer, Trusted Advisor, Lambda |
| 9 | **Security tools** — Secrets Manager, CloudFront, GuardDuty, Security Hub |

---

### 10.2 Where to Go from Here?

**Recommended next steps:**

| Path | Description |
|------|-------------|
| **Service deep dives** | AWS Introduction to Polly, Deep Dive into Lambda — go deeper on specific services |
| **Solutions Architect** | AWS Solutions Architect certification — one of the best certifications in cloud |
| **More A Cloud Guru (ACG) courses** | Explore service-specific courses aligned to your business needs |

> *"Keep being awesome!"* — Elizabeth Hord

---

*End of AWS Essentials Course Transcripts*
