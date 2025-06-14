# 🚀 Cloud Infrastructure Automation with Terraform and Docker on Azure

## 1. Requirements

To complete this project, make sure the following tools and accounts are available and properly set up on your system:

- ✅ **Terraform** – Infrastructure as Code tool for provisioning resources
- ✅ **Azure CLI** – Command-line interface to interact with Azure
- ✅ **Azure Account** – Active Azure subscription with sufficient privileges
- ✅ **Docker Desktop & Docker Compose** – To run containerized services locally or on remote VMs
- ✅ **Any Terminal** – To run CLI Command (Gitbash,VsCode,Notebook,etc.)

## 2. Project Objective

The objective of this project is to demonstrate hands-on DevOps skills by automating the deployment of infrastructure and services on Microsoft Azure. This includes:

- Provisioning a Debian-based virtual machine using Terraform
- Installing and configuring Docker and Docker Compose
- Deploying Nginx Proxy Manager and IT Tools as containerized applications
- Managing application access via domain or local hosts configuration
- Ensuring modular and reusable Infrastructure as Code (IaC) structure

This setup reflects real-world practices in cloud infrastructure management and container orchestration.

## 3. Setup Instructions

Follow the steps below to provision the infrastructure, configure the environment, and deploy the services.

### 3.1 Clone the Repository

Download the source code to your local machine via terminal:

```bash
git clone https://github.com/Furkan-Alay/terraform-azure-docker-setup.git
cd terraform-azure-docker-setup
```

## 4.2 Authenticate to Azure

Login to your Azure account using the Azure CLI:
```bash
az login
```
Once the login window appears, select your subscription. For example, if the Subscription ID is listed as 1, enter: 1
This will authenticate and set your active subscription for Terraform.

## 4.3 Generate SSH Key

Navigate to your SSH directory and generate a new SSH key:
```bash
cd ~/.ssh
ssh-keygen -t rsa -b 4096 -f <SSH_Key_Name>
```
Then, open your Terraform configuration file and update the following line:
```bash
public_key = file("~/.ssh/<SSH_Key_Name>.pub")
```

Once the login window appears, select your subscription. For example, if the Subscription ID is listed as 1, enter: 1

This will authenticate and set your active subscription for Terraform.

## 4.4 Initialize and Run Terraform
Run the following Terraform commands in order:
Initializes the Terraform working directory and downloads provider plugins.
```bash
terraform init
```
Formats your code to follow standard Terraform style conventions.
```bash
terraform fmt
```
Checks whether the configuration is syntactically valid.
```bash
terraform validate
```
Generates an execution plan to show what will be created.
```bash
terraform plan
```
Applies the changes required to reach the desired state. Type yes to confirm.
```bash
terraform apply
```
### Once complete, your virtual machine will be successfully provisioned on Azure.

## 4.5 Connect to the Virtual Machine
Use SSH to connect to your VM:
```bash
ssh -i ~/.ssh/<SSH_Key_Name> adminuser@<Virtual_Machine_Public_IP>
```
Replace <SSH_Key_Name> and <Virtual_Machine_Public_IP> with your values from the Azure portal.

Then, update and upgrade system packages:
```bash
sudo apt update && sudo apt upgrade -y
```

## 4.6 Install Docker Engine and Docker Compose
Depending on your operating system, install Docker and Docker Compose by following the official guide:

[Install Docker Engine on Debian](https://docs.docker.com/engine/install/debian/)

Make sure Docker is running and accessible via:
```bash
docker --version
docker compose version
```
## 4.7 Create Docker Compose Files
Switch to the root user:

```bash
sudo -i
```
Create a docker directory and two Docker Compose files:

```bash
mkdir docker
cd docker
touch docker-compose.yml docker-it.yml
```
You can find the content for these files in the cloned repository under:
- docker/docker-compose.yml
- docker/docker-it.yml

Copy the contents accordingly.

## 4.8 Build and Run Docker Containers
Run the services using Docker Compose:

```bash
docker compose -f docker-compose.yml -f docker-it.yml up -d
```
Replace <SSH_Key_Name> and <Virtual_Machine_Public_IP> with your values from the Azure portal.

Then, update and upgrade system packages:
```bash
sudo apt update && sudo apt upgrade -y
```
⚠️ Important Notes:
- Disable firewall or VPN if any issues occur.
- Default ports:
  - Nginx Default Site: http://<VM_Public_IP>:80
  - Nginx Proxy Manager UI: http://<VM_Public_IP>:81
  - IT Tools App: http://<VM_Public_IP>:8090
 
## 4.5 Connect to the Virtual Machine
Use SSH to connect to your VM:
```bash
ssh -i ~/.ssh/<SSH_Key_Name> adminuser@<Virtual_Machine_Public_IP>
```
Replace <SSH_Key_Name> and <Virtual_Machine_Public_IP> with your values from the Azure portal.

Then, update and upgrade system packages:
```bash
sudo apt update && sudo apt upgrade -y
```
