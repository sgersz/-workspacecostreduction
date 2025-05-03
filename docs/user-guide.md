# 📝 User Guide – Accessing EC2 Virtual Desktop via Zscaler ZPA

This guide explains how end users can access their dedicated virtual desktop hosted on AWS EC2, using Zscaler ZPA (Zero Trust Network Access) to securely connect without a VPN or AWS Workspaces Client.

---

## 🔑 Prerequisites

Before accessing your virtual desktop, ensure you have:

✅ A Zscaler ZPA account and credentials  
✅ Zscaler Client Connector installed and running on your device  
✅ Remote Desktop Protocol (RDP) client installed (default on Windows, Microsoft Remote Desktop for Mac)  
✅ Your assigned EC2 instance name or IP address (provided by IT/admin)  

---

## 🖥️ Steps to Access Virtual Desktop

### 1. **Authenticate to Zscaler ZPA**

- Open **Zscaler Client Connector**
- Log in with your company credentials
- Verify status shows **“Connected”**

ZPA will apply access policies in the background to enable secure connectivity to the AWS VPC hosting your EC2 instance.

---

### 2. **Launch Remote Desktop Client**

- Open **Remote Desktop Connection** (Windows) or **Microsoft Remote Desktop** (Mac)
- Enter the **hostname or IP address of your EC2 instance** in the computer field
- Click **Connect**

📝 *Tip: Use the fully qualified domain name (FQDN) if DNS resolution is required via ZPA.*

---

### 3. **Authenticate with EC2 Credentials**

When prompted:

- Enter your assigned **username** and **password** for the EC2 instance
- Click **OK** to initiate the session

⚠️ If you see a security certificate warning, click **Yes** to continue.

---

## 🚩 Troubleshooting

| Issue                                 | Solution                                   |
|--------------------------------------|-------------------------------------------|
| Can’t connect to EC2                  | Ensure Zscaler Client Connector shows “Connected”; verify you’re logged into ZPA |
| RDP timeout or unreachable            | Confirm EC2 instance is running; check hostname/IP; contact admin |
| Invalid credentials                   | Check with IT to reset your EC2 password   |

---

## 📝 Notes

- No VPN client is required; access is securely tunneled via Zscaler ZPA
- You do **not** need the AWS Workspaces client for this environment
- If you switch devices, ensure Zscaler Client Connector is installed and configured

