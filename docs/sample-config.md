# 🔧 Sample Configuration – Zscaler ZPA and AWS EC2 Access

This sample outlines the required policies and settings for enabling secure RDP access to an AWS EC2 instance via Zscaler ZPA.

---

## 1️⃣ Zscaler ZPA Configuration

### a. Create an Application Segment

- **Name:** EC2-RDP-AppSegment
- **Domain/FQDN:** ec2-user-desktop.internal.local
- **TCP Ports:** 3389
- **Enabled:** True

### b. Create an Access Policy

- **Name:** EC2 Remote Access Policy
- **Action:** Allow
- **Application Segment:** EC2-RDP-AppSegment
- **Source User Group:** CorpUsers
- **Destination:** ec2-user-desktop.internal.local
- **Protocol:** TCP
- **Port:** 3389

**Notes:**

- Ensure **ZPA Connectors** are deployed in the same AWS VPC or a peered network where the EC2 resides.
- If DNS is used, confirm that `ec2-user-desktop.internal.local` resolves to the EC2 private IP via ZPA.

---

## 2️⃣ AWS EC2 Security Group Configuration

- **Inbound Rule:**
  - **Type:** RDP
  - **Protocol:** TCP
  - **Port Range:** 3389
  - **Source:** ZPA Connector private IP addresses (or the VPC subnet used by ZPA Connectors)

**Notes:**

- Do **NOT** expose port 3389 to the public internet.
- Only allow inbound RDP traffic from **ZPA Connector private IP ranges**.

---

## 3️⃣ DNS Configuration (if applicable)
ec2-user-desktop.internal.local   A   10.0.1.100

## ➡️ Ensure the EC2 instance is resolvable inside the VPC or via ZPA DNS forwarding.

⸻

## 4️⃣ User Assignment

Assign each user an EC2 instance and provide:
	•	Hostname or FQDN of their EC2 desktop
	•	EC2 login credentials
	•	Instructions to authenticate to Zscaler ZPA before attempting RDP

⸻

## 📝 General Recommendations
	•	Ensure Zscaler Client Connector is installed on user devices
	•	No VPN client is required
	•	Validate ZPA policy allows RDP traffic to the private EC2 instance