# 🖥️ AWS Commands Used

This document contains the Linux commands used during the implementation and testing of the **AWS Company Network Architecture** project.

---

# 1️⃣ Connect to the Company Server

Use SSH to connect from your local machine to the Company Server (Public EC2 Instance).

```bash
ssh -i aws_login.pem ubuntu@<Company-Public-IP>
```

Example:

```bash
ssh -i aws_login.pem ubuntu@54.123.45.67
```

---

# 2️⃣ Verify Current User

```bash
whoami
```

---

# 3️⃣ Check Current Directory

```bash
pwd
```

---

# 4️⃣ List Files

```bash
ls
```

or

```bash
ls -la
```

---

# 5️⃣ Create Project Directory

```bash
mkdir company-project
```

Move into the directory

```bash
cd company-project
```

---

# 6️⃣ Create Sample HTML Page

```bash
nano index.html
```

Example:

```html
<h1>Welcome to Company Server</h1>
```

Save:

CTRL + O

ENTER

CTRL + X

---

# 7️⃣ Start Python HTTP Server

```bash
python3 -m http.server 8000
```

---

# 8️⃣ Verify Server is Running

Open browser

```
http://<Company-Public-IP>:8000
```

---

# 9️⃣ Copy PEM File to Company Server

```bash
scp -i aws_login.pem aws_login.pem ubuntu@<Company-Public-IP>:/home/ubuntu
```

---

# 🔟 Set Proper Permissions

```bash
chmod 400 aws_login.pem
```

---

# 11️⃣ SSH to HR Server

From the Company Server

```bash
ssh -i aws_login.pem ubuntu@10.0.2.188
```

---

# 12️⃣ SSH to Employee Server

From the Company Server

```bash
ssh -i aws_login.pem ubuntu@10.0.3.99
```

---

# 13️⃣ Create HR Web Page

```bash
nano index.html
```

Example

```html
<h1>Welcome to HR Server</h1>
```

---

# 14️⃣ Run HR Web Server

```bash
python3 -m http.server 8000
```

---

# 15️⃣ Create Employee Web Page

```bash
nano index.html
```

Example

```html
<h1>Welcome to Employee Server</h1>
```

---

# 16️⃣ Run Employee Web Server

```bash
python3 -m http.server 8000
```

---

# 17️⃣ Test HR Server

From Company Server

```bash
curl http://10.0.2.188:8000
```

---

# 18️⃣ Test Employee Server

```bash
curl http://10.0.3.99:8000
```

---

# 19️⃣ Check Running Processes

```bash
ps -ef
```

---

# 20️⃣ Check Listening Ports

```bash
sudo ss -tulnp
```

or

```bash
sudo netstat -tulnp
```

---

# 21️⃣ Kill a Running Process

```bash
kill -9 <PID>
```

Example

```bash
kill -9 2345
```

---

# 22️⃣ Update Ubuntu Packages

```bash
sudo apt update
```

---

# 23️⃣ Upgrade Packages

```bash
sudo apt upgrade -y
```

---

# 24️⃣ Install Python (if required)

```bash
sudo apt install python3 -y
```

---

# 25️⃣ Check Python Version

```bash
python3 --version
```

---

# 26️⃣ View EC2 Private IP

```bash
hostname -I
```

---

# 27️⃣ Exit SSH Session

```bash
exit
```

---

# 📌 Project Workflow

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

# ✅ Project Outcome

Successfully achieved:

- Created a custom AWS VPC
- Configured one Public Subnet
- Configured two Private Subnets
- Configured Internet Gateway
- Configured Route Tables
- Configured Security Groups
- Launched three Ubuntu EC2 instances
- Established SSH connectivity
- Hosted Python HTTP servers
- Verified communication using private IP addresses
- Successfully tested secure communication between Company, HR, and Employee servers
