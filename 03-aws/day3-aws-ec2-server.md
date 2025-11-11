# 💻 Day 3 — Understanding Servers & Launching an AWS EC2 Instance

> “A server is not just a computer — it’s the heart that keeps digital life alive.”  
> — *FLM Institute | DevOps with Multi-Cloud*

---

## 🎯 **Objective**
To understand what a **server** is, how cloud servers differ from physical ones, and how to create a secure, scalable virtual server using **AWS EC2 (Elastic Compute Cloud)**.

---

## 🧠 **What is a Server?**
A **server** is a powerful computer that provides data, services, or resources to other systems (clients) over a network.

💡 **Example:**  
When you open YouTube, Netflix, or Gmail — your device (client) communicates with a **server** hosted in the cloud.

---

## 🏗️ **Physical vs Cloud Server**

| Type | Description | Example |
|------|--------------|----------|
| **Physical Server** | On-premise hardware owned by a company | Local data center |
| **Cloud Server** | Virtual machine hosted in AWS/Azure | AWS EC2 instance |

🧩 AWS manages thousands of these cloud servers worldwide.

---

## ⚙️ **Server Components**

| Component | Purpose |
|------------|----------|
| **Operating System** | Linux / Windows that manages processes |
| **Hardware (CPU + RAM)** | Determines compute power |
| **Storage (EBS)** | Keeps data even after restart |
| **Network (VPC)** | Connects server securely |
| **Security (IAM + SG)** | Controls who can access the server |

---

## ☁️ **AWS EC2 — Elastic Compute Cloud**

EC2 lets you create and manage **virtual servers** in the AWS Cloud.  
Each EC2 instance can host a website, app, or database.

---

## 🪜 **Steps to Launch an EC2 Instance**

### 🔹 Step 1 — Name and Tags
- Give your instance a name (e.g., `tanu-web-server`).  
- Add tags for organization:  
  | Key | Value | Description |
  |------|--------|-------------|
  | Name | web-server | Instance name |
  | Owner | Tanu | Created by |
  | Environment | Dev | Environment name |

---

### 🔹 Step 2 — Choose Amazon Machine Image (AMI)
- Select **Amazon Linux 2 AMI (Free Tier Eligible)**  
  - Other options: Ubuntu, Red Hat, Windows Server.

---

### 🔹 Step 3 — Choose Instance Type
Defines compute power (CPU & RAM).

| Instance Type | vCPU | Memory | Free Tier |
|----------------|------|--------|-----------|
| t2.micro | 1 | 1 GB | ✅ Yes |
| t3.medium | 2 | 4 GB | ❌ No |

💡 *Use `t2.micro` for Free Tier practice.*

---

### 🔹 Step 4 — Key Pair (Login Authentication)
Used to connect securely via SSH.

- Create new key pair → Name it `tanu-key` → Download `.pem` file.  
- Keep it safe — it’s your only login key.

---

### 🔹 Step 5 — Configure Network
- Choose **Default VPC**.  
- Enable **Auto-assign Public IP**.  
- Create new **Security Group** → Allow:
  - **SSH (22)** – to connect
  - **HTTP (80)** – to access web page
  - **HTTPS (443)** – for secure sites

---

### 🔹 Step 6 — Storage
- Default: 8 GB EBS volume  
- Type: gp3 (SSD)  
- You can expand later if needed.

---

### 🔹 Step 7 — Review and Launch
- Check all settings  
- Click **Launch Instance**  
- Wait until **Instance State = Running**

---

## 🔐 **Connect to Instance**

After instance is running:
1. Select it → Click **Connect → SSH Client**  
2. Copy the example SSH command:  
   ```bash
   chmod 400 tanu-key.pem
   ssh -i "tanu-key.pem" ec2-user@<Public-IP>
