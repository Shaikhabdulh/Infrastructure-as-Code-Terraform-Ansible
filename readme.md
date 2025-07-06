# 🚀 Terraform & Ansible Infrastructure Lab
This project demonstrates modern **Infrastructure as Code (IaC)** using **Terraform**, **Ansible**, and **Shell scripting** to provision and configure AWS infrastructure — from EC2 instances to VPCs and NGINX deployment with a mock UI page.
---
## 📁 Project Structure

```
.
├── Ansible/                            # NGINX deployment using Ansible
├── Managing EC2 & SG With Terraform/  # EC2 instance and security group setup
├── Terraform\_Remote\_Backend/          # VPC creation with remote state backend (S3)
├── User\_Data/                          # Shell script to auto-configure EC2 with HTML UI
├── .gitignore
└── readme.md

````
---
## 📦 Modules / Folders Explained
| Folder                              | Purpose                                                                 |
|-------------------------------------|-------------------------------------------------------------------------|
| `Ansible/`                          | Configures web server and deploys a static HTML file using Ansible     |
| `Managing EC2 & SG With Terraform/` | Provisions EC2 with SSH & HTTP access and generates SSH key            |
| `Terraform_Remote_Backend/`         | Creates VPC using module and stores state remotely (S3 backend)        |
| `User_Data/`                        | Bash script to install NGINX and deploy a mock "Fakebook" login page   |
---
## 🧰 Tech Stack
- **Terraform** – Provision AWS infrastructure
- **Ansible** – Automate server setup (like installing NGINX)
- **Shell Script** – Rapid custom setup for EC2
- **AWS** – Cloud platform (EC2, S3, VPC)
- **NGINX** – Web server to serve static content
- **HTML/CSS** – Frontend mock login page
---
## ⚙️ Setup Instructions
### 🔹 EC2 + Security Group
```bash
cd "Managing EC2 & SG With Terraform"
terraform init
terraform apply
```
### 🔹 Remote VPC with S3 Backend
```bash
cd "Terraform_Remote_Backend"
terraform init
terraform apply
```
> 🔐 Make sure S3 bucket and DynamoDB table exist before initializing remote backend.
### 🔹 Ansible NGINX Deployment
```bash
cd Ansible
ansible-playbook -i inventory nginx_playbook.yml
# If vault is used:
ansible-playbook -i inventory nginx_playbook.yml --ask-vault-pass
```
### 🔹 User Data Script (Fakebook Setup)
```bash
cd User_Data
chmod +x setup_fakebook.sh
sudo ./setup_fakebook.sh
```
Then visit `http://<EC2-IP>` in a browser.
---
## ❓ When & Why to Use Each Folder
| Folder                              | When to Use                         | Why It’s Useful                                            |
| ----------------------------------- | ----------------------------------- | ---------------------------------------------------------- |
| `Ansible/`                          | After provisioning                  | Installs packages like NGINX, pushes HTML config           |
| `Managing EC2 & SG With Terraform/` | Need EC2 and key-based access setup | Creates instance and security group from scratch           |
| `Terraform_Remote_Backend/`         | Production/team environments        | Stores state in S3 for collaboration, adds locking support |
| `User_Data/`                        | Quick demo/mock login UI setup      | Lightweight NGINX + Fakebook-like page via Bash script     |
---
## 🧠 Best Practices
* 🔐 Store secrets in **Ansible Vault**
* ✅ Use **Terraform remote backend (S3 + DynamoDB)** for team/production use
* 🧪 Always run `terraform plan` before `apply`
* 🔒 Secure private keys (e.g., `chmod 400`)
---
## 🖼️ Diagrams / Screenshots
You can enhance your documentation with visual aids:
* [`ec2-sg.png`](./Managing EC2 & SG With Terraform/ec2-sg.png): EC2 Instance + Security Group diagram
* [`infrastructure.png`](./Terraform_Remote_Backend/infrastructure.png): Full infrastructure overview (VPC, subnets, etc.)
---

## 📜 License

This repository is licensed under the **MIT License**.
Feel free to use, adapt, and contribute.
