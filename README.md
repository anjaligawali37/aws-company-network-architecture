# ☁️ AWS Company Network Architecture

A hands-on AWS networking project demonstrating a secure cloud infrastructure using **Amazon VPC**, **Public & Private Subnets**, **EC2 Instances**, **Security Groups**, and **Route Tables**.

This project was built to understand how organizations securely host public and internal servers using AWS networking services.

---

# 📖 Project Overview

In this project, I designed and deployed a secure AWS infrastructure from scratch.

The architecture consists of:

- ✅ 1 Custom Amazon VPC
- ✅ 1 Public Subnet
- ✅ 2 Private Subnets
- ✅ Internet Gateway
- ✅ Public Route Table
- ✅ Private Route Tables
- ✅ Security Groups
- ✅ 3 Ubuntu EC2 Instances

### EC2 Instances

| Server | Type | Purpose |
|----------|------|-----------------------------|
| Company Server | Public | Entry point to the network |
| HR Server | Private | Internal HR application |
| Employee Server | Private | Internal Employee application |

---

# 🏗️ Architecture Diagram

> The complete architecture diagram is available below.

![Architecture](architecture/architecture-diagram.png)

---

# 🎯 Project Objectives

The main objectives of this project were:

- Learn AWS Networking
- Understand VPC Architecture
- Configure Public & Private Subnets
- Implement Secure Communication
- Configure Security Groups
- Understand Route Tables
- Practice SSH Connectivity
- Host Simple Web Applications
- Test Private Communication

---

# 🌐 Network Architecture

## Amazon VPC

```
CIDR Block

10.0.0.0/16
```

---

## Public Subnet

```
10.0.1.0/24
```

### Resources

- Company Server

### Purpose

- Internet Access
- SSH Access
- Secure Entry Point

---

## Private Subnet 1

```
10.0.2.0/24
```

### Resources

- HR Server

Purpose

Internal company services.

---

## Private Subnet 2

```
10.0.3.0/24
```

### Resources

- Employee Server

Purpose

Internal employee services.

---

# 🔒 Security Groups

Separate Security Groups were created for each EC2 instance.

### Company Server

Allowed

- SSH (22)
- HTTP (8000 when required)

---

### HR Server

Allowed

- SSH only from Company Server
- Port 8000 only from Company Server

---

### Employee Server

Allowed

- SSH only from Company Server
- Port 8000 only from Company Server

---

# 💻 EC2 Instances

### Company Server

- Ubuntu
- Public IP
- SSH Accessible

Purpose

Acts as the gateway to access private servers.

---

### HR Server

- Ubuntu
- Private IP

Purpose

Hosts the HR web application.

---

### Employee Server

- Ubuntu
- Private IP

Purpose

Hosts the Employee web application.

---

# 🔄 Communication Flow

```
Laptop
    │
    │ SSH
    ▼
Company Server (Public)
    │
    ├──────── SSH ───────► HR Server
    │
    └──────── SSH ───────► Employee Server

Company Server
      │
      ├──── curl ─────► HR Server
      │
      └──── curl ─────► Employee Server
```

---

# 🚀 Project Workflow

### Step 1

Created a Custom Amazon VPC.

---

### Step 2

Created one Public Subnet.

---

### Step 3

Created two Private Subnets.

---

### Step 4

Attached an Internet Gateway.

---

### Step 5

Configured Public and Private Route Tables.

---

### Step 6

Configured Security Groups.

---

### Step 7

Launched three Ubuntu EC2 instances.

---

### Step 8

Connected to the Company Server using SSH.

---

### Step 9

Connected to HR Server using Private IP.

---

### Step 10

Connected to Employee Server using Private IP.

---

### Step 11

Hosted Python HTTP Server.

```bash
python3 -m http.server 8000
```

---

### Step 12

Verified communication using:

```bash
curl http://10.0.2.188:8000

curl http://10.0.3.99:8000
```

---

# 📸 Project Screenshots

The screenshots for each implementation step are available in the **screenshots/** folder.

They include:

- VPC Creation
- Public Subnet
- Private Subnets
- Route Tables
- Security Groups
- EC2 Instances
- SSH Connection
- HR Server
- Employee Server
- Python HTTP Server
- Private Communication

---

# 📂 Repository Structure

```
aws-company-network-architecture/
│
├── README.md
│
├── architecture/
│   ├── README.md
│   └── architecture-diagram.png
│
├── screenshots/
│   ├── README.md
│   ├── 01-vpc-created.png
│   ├── 02-public-subnet.png
│   ├── 03-private-subnet.png
│   ├── 04-route-table.png
│   ├── 05-security-group.png
│   ├── 06-company-server.png
│   ├── 07-company-ssh.png
│   ├── 08-hr-server.png
│   ├── 09-employee-server.png
│   ├── 10-private-communication.png
│   ├── 11-python-http-server.png
│   └── 12-final-architecture.png
│
└── commands/
    └── aws-commands.md
```

---

# 🛠️ AWS Services Used

- Amazon EC2
- Amazon VPC
- Internet Gateway
- Route Tables
- Security Groups
- Ubuntu Linux
- SSH
- Python HTTP Server

---

# 📚 Key Learnings

During this project, I learned:

- AWS Networking Fundamentals
- Virtual Private Cloud (VPC)
- Public & Private Subnets
- Internet Gateway
- Route Tables
- Security Groups
- EC2 Deployment
- Secure SSH Access
- Linux Networking
- Private Server Communication
- Hosting a Web Server
- Troubleshooting Connectivity Issues

---

# 🚀 Future Improvements

This project will be extended by implementing:

- NAT Gateway
- Application Load Balancer (ALB)
- Auto Scaling Groups (ASG)
- Multi-AZ Architecture
- Amazon Route 53
- HTTPS using SSL/TLS
- Docker Deployment
- CI/CD Pipeline
- Amazon CloudWatch Monitoring

---

# 👩‍💻 Author

**Anjali Gawali**

Engineering Student | AWS Cloud Learner | Building real-world cloud networking projects to strengthen my cloud and DevOps skills.

- 💼 LinkedIn: https://www.linkedin.com/in/anjali-gawali-248b2a399/
- 💻 GitHub: https://github.com/anjaligawali37
  
---


⭐ If you found this project helpful, feel free to fork the repository or leave a star!
