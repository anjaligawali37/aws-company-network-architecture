# 🏢 AWS Secure Company Network Architecture

A real-world AWS networking project demonstrating secure communication between Company, HR, and Employee servers using Amazon VPC, Public and Private Subnets, Route Tables, NAT Gateway, Security Groups, and EC2 Instances.

---

# 📌 Project Overview

This project simulates a secure company infrastructure where:

- The **Company Server** is deployed inside a **Public Subnet**.
- The **HR Server** is deployed inside **Private Subnet 1**.
- The **Employee Server** is deployed inside **Private Subnet 2**.
- Only the Company Server is publicly accessible through SSH.
- HR and Employee servers remain private and can only be accessed through the Company Server.
- Python HTTP servers are hosted on both private instances.
- Internal communication between servers is verified using Private IP addresses.

---

# 🏗 Architecture

![Architecture](architecture/aws-company-network-architecture.png)

---

# 🛠 AWS Services Used

- Amazon VPC
- Amazon EC2
- Public Subnet
- Private Subnet
- Internet Gateway
- NAT Gateway
- Route Tables
- Security Groups
- SSH
- Python HTTP Server

---

# 🌐 Network Design

## VPC

| Property | Value |
|----------|--------|
| CIDR Block | 10.0.0.0/16 |

---

## Public Subnet

| Property | Value |
|----------|--------|
| CIDR | 10.0.1.0/24 |

Contains:

- Company Server

---

## Private Subnet 1

| Property | Value |
|----------|--------|
| CIDR | 10.0.2.0/24 |

Contains:

- HR Server

---

## Private Subnet 2

| Property | Value |
|----------|--------|
| CIDR | 10.0.3.0/24 |

Contains:

- Employee Server

---

# 🖥 EC2 Instances

| Instance | Type | Private IP | Public IP |
|-----------|------|------------|-----------|
| Company Server | t3.micro | 10.0.1.81 | Yes |
| HR Server | t3.micro | 10.0.2.188 | No |
| Employee Server | t3.micro | 10.0.3.99 | No |

---

# 🌍 Internet Access

## Company Server

- Internet Gateway
- Public IP
- SSH Access

## HR Server

- Private IP only
- Internet via NAT Gateway

## Employee Server

- Private IP only
- Internet via NAT Gateway

---

# 🔒 Security Groups

## Company Security Group

Inbound Rules

- SSH (22)

Outbound Rules

- Allow All

---

## HR Security Group

Inbound Rules

- SSH (22)
- Custom TCP (8000)

Outbound Rules

- Allow All

---

## Employee Security Group

Inbound Rules

- SSH (22)
- Custom TCP (8000)

Outbound Rules

- Allow All

---

# 🛣 Route Tables

## Public Route Table

| Destination | Target |
|-------------|--------|
| 10.0.0.0/16 | Local |
| 0.0.0.0/0 | Internet Gateway |

Associated with:

- Public Subnet

---

## Private Route Table

| Destination | Target |
|-------------|--------|
| 10.0.0.0/16 | Local |
| 0.0.0.0/0 | NAT Gateway |

Associated with

- Private Subnet 1
- Private Subnet 2

---

# 🔐 SSH Connectivity

Laptop

↓

Company Server (Public IP)

↓

HR Server (Private IP)

↓

Employee Server (Private IP)

This configuration ensures that private instances are never directly exposed to the Internet.

---

# 🌐 Python HTTP Server

Python HTTP Server was started on both private instances.

Command

```bash
python3 -m http.server 8000
```

---

# ✅ Testing Internal Communication

## Company → HR

Command

```bash
curl http://10.0.2.188:8000
```

Output

```
This is HR Server
```

---

## Company → Employee

Command

```bash
curl http://10.0.3.99:8000
```

Output

```
This is EMPLOYEE Server
```

---

# 📷 Project Screenshots

## VPC

![](screenshots/01-VPC.png)

---

## Public Route Table

![](screenshots/02-Public-Route-Table.png)

---

## Private Route Table

![](screenshots/03-Private-Route-Table.png)

---

## Company Security Group

![](screenshots/04-Company-Security-Group.png)

---

## HR Security Group

![](screenshots/05-HR-Security-Group.png)

---

## Employee Security Group

![](screenshots/06-Employee-Security-Group.png)

---

## EC2 Instances

![](screenshots/07-EC2-Instances.png)

---

## SSH into Company Server

![](screenshots/08-SSH-Company-Server.png)

---

## SSH into HR Server

![](screenshots/09-SSH-HR-Server.png)

---

## SSH into Employee Server

![](screenshots/10-SSH-Employee-Server.png)

---

## Python HTTP Server on HR

![](screenshots/11-HR-Python-HTTP-Server.png)

---

## Python HTTP Server on Employee

![](screenshots/12-Employee-Python-HTTP-Server.png)

---

## Company Server → HR Server Communication

![](screenshots/13-Company-to-HR-Communication.png)

---

## Company Server → Employee Server Communication

![](screenshots/14-Company-to-Employee-Communication.png)

---

# 📚 Key Learning Outcomes

Through this project I learned:

- Designing a custom Amazon VPC
- Creating Public and Private Subnets
- Configuring Internet Gateway and NAT Gateway
- Creating Public and Private Route Tables
- Launching EC2 instances in different subnets
- Configuring Security Groups
- Using SSH to securely access private servers
- Hosting web applications using Python HTTP Server
- Testing secure internal communication using Private IP addresses
- Understanding secure network architecture on AWS

---

# 🚀 Future Improvements

- Application Load Balancer (ALB)
- Auto Scaling Group (ASG)
- HTTPS using ACM
- Route 53 Domain
- CloudWatch Monitoring
- Nginx Reverse Proxy
- CI/CD Pipeline using GitHub Actions
- Infrastructure as Code using AWS CloudFormation or Terraform

---

# 👩‍💻 Author

**Anjali Gawali**

Computer Engineering Student

AWS | Linux | Networking | Cloud Computing

GitHub: https://github.com/anjaligawali37

LinkedIn: *(Add your LinkedIn profile URL here)*

---
