# 🚀 End-to-End DevOps Project  
## CI/CD + Terraform + AWS + Docker + Kubernetes  
**By Darshana Manikkuwadura**

---

## 📌 Overview

This repository documents a **real-world, production-style DevOps implementation** that brings together **Infrastructure as Code, CI/CD automation, containerization, and cloud-native deployment** on AWS.

This project is part of my **DevOps Transformation Challenge**, designed to demonstrate how modern DevOps teams design, build, test, and deploy applications using **repeatable, scalable, and secure workflows**.

The focus is not just tooling — but **DevOps thinking**:  
> Automate everything, version everything, and design for scale from Day 1.

---

## 🎯 Project Goals

- Build cloud infrastructure **from scratch** using Terraform  
- Containerize applications using Docker  
- Implement CI/CD pipelines using GitHub Actions (extensible to Jenkins)  
- Deploy workloads to AWS (EC2 → EKS-ready architecture)  
- Follow modular, production-grade DevOps practices  
- Lay the foundation for Kubernetes-based deployments and monitoring  

---

## 🏗️ Architecture Overview

```text
Developer
   │
   ├── Git Push (main branch)
   │
   ├── GitHub Actions (CI Pipeline)
   │       ├── Build Docker Image
   │       ├── Authenticate to AWS
   │       ├── Push Image to ECR
   │
   ├── Terraform (IaC)
   │       ├── VPC
   │       ├── Subnets
   │       ├── Internet Gateway
   │       ├── Route Tables
   │       ├── Security Groups
   │       ├── IAM Roles
   │
   └── AWS
           ├── EC2 / EKS-ready networking
           ├── Amazon ECR
           └── Cloud-native foundation
🧱 Terraform Infrastructure (Day 1–3)
Terraform is used as the single source of truth for all AWS infrastructure.

✔ Day 1–2: Core Networking
Terraform project initialized with remote-ready structure

VPC created with CIDR planning

Public subnets provisioned

Internet Gateway attached

Route Tables created and associated with subnets

Security Groups defined with least-privilege rules

This ensures:

Clean network isolation

Predictable IP allocation

Secure inbound/outbound traffic flow

✔ Day 3: IAM & Permissions
IAM Role created for EC2 workloads

Attached policies:

AWS Systems Manager (SSM)

CloudWatch logging

Amazon ECR read access

IAM configuration modularized for reuse

Integrated cleanly into Terraform modules

Terraform structure follows production best practices:

text
Copy code
terraform/
├── main.tf
├── variables.tf
├── outputs.tf
├── provider.tf
├── vpc/
├── iam/
└── security/
🐳 Docker: Application Containerization
A sample application was selected to demonstrate container workflows.

✔ Docker Implementation
Dockerfile written using best practices

Minimal base image

Layer caching optimized

Exposed ports defined clearly

Image built and tested locally

Key goals:

Small image size

Fast builds

Consistent runtime across environments

🔁 CI Pipeline – GitHub Actions
A CI-first mindset is applied from the beginning.

✔ CI Workflow (.github/workflows/ci.yml)
The pipeline is triggered on every push to main.

Steps include:

Checkout repository

Configure AWS credentials securely

Authenticate to Amazon ECR

Build Docker image

Tag image using commit SHA

Push image to ECR

This ensures:

Every commit produces a deployable artifact

No manual Docker builds

Immutable, traceable container images

Pipeline is intentionally designed to be extensible:

Add unit tests

Add security scans

Add Terraform plan/apply stages

Add Kubernetes deployment stages

📦 AWS ECR Integration
Amazon Elastic Container Registry (ECR) is used as the centralized image registry.

✔ What’s Implemented
ECR repository created

Secure authentication via GitHub Actions

Images pushed automatically from CI

Ready for consumption by EC2 or EKS

This mirrors real enterprise workflows, where:

CI produces artifacts

CD consumes artifacts

No direct builds on servers

☁️ AWS Deployment Strategy
Current phase focuses on EC2-compatible infrastructure, while keeping everything EKS-ready.

Why this matters:

Same networking and IAM model works for Kubernetes

Easy transition from EC2 → EKS

Avoids rework later

Next stages will introduce:

EKS cluster provisioning

Kubernetes manifests / Helm

Ingress controllers

Auto-scaling

📊 Monitoring (Planned)
Monitoring is treated as a first-class citizen, not an afterthought.

Upcoming integrations:

Prometheus for metrics

Grafana dashboards

CloudWatch integration

Container-level observability

The infrastructure already supports this via IAM roles and networking design.

📁 Repository Structure
text
Copy code
.
├── .github/workflows/
│   └── ci.yml
├── docker/
│   └── Dockerfile
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   ├── outputs.tf
│   └── modules/
├── app/
│   └── sample-app
└── README.md
Everything is:

Version controlled

Reproducible

Reviewable

🧠 DevOps Principles Applied
This project demonstrates:

Infrastructure as Code

Immutable infrastructure

Shift-left CI/CD

Security by design

Automation over manual work

Cloud-native thinking

This is not a demo — it’s a real DevOps foundation.

🚧 Next Milestones
Terraform-based EKS provisioning

Kubernetes deployments

Helm charts

GitOps workflows

Canary & blue/green deployments

Observability dashboards

👨‍💻 Author
Darshana Manikkuwadura
Tech Leader DevOps, SRE, Cloud and Platform Engineer | Fintech, AI & Payments Expert | Visiting Lecturer | Advisor | Ambassador and Global Speaker | Investor | 4x Startup Founder (2 exits) | Born in 🇱🇰, Made in 🇬🇧

This repository reflects how I design, build, and scale DevOps platforms in real environments — from infrastructure to CI/CD to production readiness.

⭐ If you find this useful, consider starring the repository and following along as the challenge continues.
