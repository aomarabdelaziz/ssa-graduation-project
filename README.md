# 🏗️ Scalable Web Application on AWS (ALB + Auto Scaling)

> A simple, scalable, and highly available web application architecture using EC2, Application Load Balancer, and Auto Scaling Group (ASG) on AWS.

---

## 📌 Project Description

This project demonstrates how to build and deploy a scalable web application architecture on AWS using EC2 instances behind an Application Load Balancer (ALB), managed through an Auto Scaling Group (ASG). The system automatically scales based on load and ensures high availability, security, and cost-efficiency.

---

## 🧩 Architecture Overview

![Architecture Diagram](./architecture-diagram.png)

### 🧱 Key Components

- **Amazon EC2**: Hosts the web application (Node.js or static site).
- **Auto Scaling Group (ASG)**: Automatically adds/removes instances based on demand.
- **Application Load Balancer (ALB)**: Routes HTTP(S) traffic evenly to healthy instances.
- **Amazon RDS (Optional)**: Backend relational database.
- **IAM**: Role-based access control for instances and services.
- **CloudWatch + SNS**: Monitoring and alerting for health and performance.

---

## 🛠️ Technologies & AWS Services

| Service        | Purpose                                  |
|----------------|-------------------------------------------|
| EC2            | Hosts the application backend/frontend    |
| ALB            | Distributes traffic and health checks     |
| ASG            | Ensures scalability and availability      |
| RDS            | Stores data (e.g., MySQL or PostgreSQL)   |
| IAM            | Manages roles and permissions             |
| CloudWatch     | Logs, metrics, and alarms                 |
| SNS            | Sends notifications on alarm triggers     |

---

## 🚀 Deployment Steps

### ✅ Prerequisites

- AWS CLI configured
- IAM user with EC2, ALB, ASG, RDS, and IAM permissions
- SSH key pair for EC2 login

---

### 🔧 Infrastructure Setup (Manual or IaC)

#### Option 1: Manual (via AWS Console)

1. Launch an EC2 AMI with your app.
2. Create a Launch Template for the instance.
3. Set up a Target Group.
4. Create an Application Load Balancer.
5. Set up Auto Scaling Group with min/max/desired capacity.
6. Attach ALB to the ASG.
7. Configure health checks and CloudWatch alarms.

#### Option 2: Infrastructure as Code (IaC)

Use [Terraform](https://github.com/) or AWS CloudFormation to automate provisioning.

---

### 🧪 Sample EC2 Web App (Node.js)

```bash
#!/bin/bash
yum update -y
yum install -y httpd
echo "<h1>Welcome to Scalable App via ALB</h1>" > /var/www/html/index.html
systemctl enable httpd
systemctl start httpd
