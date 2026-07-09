# AWS DevOps Intern Assignment – EC2 Website Deployment

##  Objective
Deploy a simple static website on an AWS EC2 instance, configured with Nginx, and document the complete process.

---

##  Tech Stack / Services Used
- **AWS EC2** (Ubuntu 22.04 LTS, t2.micro)
- **AWS Security Groups** (Inbound rules: SSH – 22, HTTP – 80)
- **Nginx** (Web Server)
- **Git & GitHub**
- **Docker** (Bonus task)

---

##  Step 1: EC2 Instance Setup
1. Launched an EC2 instance via AWS Console
   - AMI: Ubuntu 22.04 LTS
   - Instance type: t2.micro (Free Tier eligible)
   - Key pair: created new `.pem` key for SSH access
2. Created a Security Group with the following inbound rules:
   | Type | Port | Source |
   |------|------|--------|
   | SSH  | 22   | My IP |
   | HTTP | 80   | 0.0.0.0/0 |
3. Connected to the instance via SSH:
   ```bash
   chmod 400 your-key.pem
   ssh -i "your-key.pem" ubuntu@<EC2_PUBLIC_IP>
   ```

**EC2 Public IP:** `100.58.113.73`

---

##  Step 2: Linux Basics & Nginx Installation
Commands used on the EC2 instance:

```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Install Nginx
sudo apt install nginx -y

# Check Nginx status
sudo systemctl status nginx

# Restart Nginx
sudo systemctl restart nginx

# Check disk usage
df -h

# Check memory usage
free -h

# Check running processes
top
```

---

##  Step 3: Website Deployment
1. Navigated to the Nginx default web root:
   ```bash
   cd /var/www/html
   sudo rm index.nginx-debian.html
   sudo nano index.html
   ```
2. Created a basic HTML page containing:
   - Name: Lavit Tyagi
   - College: MGM COET, Noida (AKTU)
   - Branch: Computer Science Engineering
   - Email: lavittyagi2004@gmail.com
   - Date: Dynamically generated using JavaScript (`new Date().toDateString()`)
3. Restarted Nginx to reflect changes:
   ```bash
   sudo systemctl restart nginx
   ```
4. Verified the site was accessible at: `http://100.58.113.73`

---

##  Repository Structure
```
├── index.html      # Website file hosted on EC2
├── README.md        # Documentation (this file)
```

---

##  Bonus Task Completed
- [x] Installed Docker and ran `hello-world` container
   ```bash
   sudo apt install docker.io -y
   sudo systemctl enable --now docker
   sudo docker run hello-world
   ```
---

##  Problems Faced
- *(e.g., SSH "Permission denied" error — resolved by running `chmod 400` on the key file before connecting)*
- *(e.g., Website not loading initially — resolved by adding port 80 to the Security Group inbound rules)*

---

##  Learnings
- Hands-on experience launching and configuring an EC2 instance from scratch
- Understanding of Security Groups and network access control
- Installing and managing a web server (Nginx) on Linux
- Deploying a static website and verifying public accessibility
- Basic Docker containerization (bonus)

---

##  Total Time Taken
`<add-total-time-taken>` (e.g., 3 hours)

---

##  Live Website
`http://100.58.113.73`
