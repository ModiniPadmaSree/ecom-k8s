# End-to-End DevOps Automation for E-Commerce Application

This project demonstrates a complete DevOps implementation for a containerized E-Commerce application using CI/CD, GitOps, Infrastructure as Code, Monitoring, Logging, and Kubernetes.

The setup automates:
- Infrastructure provisioning
- Application build and testing
- Security scanning
- Docker image management
- Continuous deployment using Argo CD
- Kubernetes deployment with Helm
- Monitoring and logging using Prometheus, Grafana, and ELK Stack

---

# Project Repositories

## 1. Application Source Code

Repository:
```text
https://github.com/ModiniPadmaSree/ecom
```

Contains:
- E-Commerce application source code
- Docker configuration
- Jenkins pipeline
- SonarQube integration
- Slack notifications
- CI automation

---

## 2. Kubernetes & GitOps Repository

Repository:
```text
https://github.com/ModiniPadmaSree/ecom-k8s
```

Contains:
- Kubernetes manifests
- Helm charts
- Argo CD Application manifests
- Deployment configurations
- Values files for image updates

---

## 3. Infrastructure Provisioning Repository

Repository:
```text
https://github.com/ModiniPadmaSree/ecom-infra
```

Contains:
- Terraform scripts
- Ansible playbooks
- Infrastructure provisioning automation
- Kubernetes cluster setup configuration

---

# Project Architecture

```text
Developer Commit -> GitHub Repository (ecom) -> Jenkins CI Pipeline -> Update Image Tag in ecom-k8s Repository -> GitHub Repository (ecom-k8s) -> Argo CD Watches Repository -> Automatic Kubernetes Deployment -> Kubernetes Cluster on AWS EC2
                                                    │                                                                                                                                                                           |- Logging & API Monitoring (ELK Stack)
                                                    ├── Build Application                                                                                                                                                       |-Application Monitoring (Prometheus + Grafana) 
                                                    ├── Run Tests
                                                    ├── SonarQube Security Scan
                                                    ├── Build Docker Image
                                                    ├── Push Docker Image to Docker Hub
                                                    └── Slack Notification
     

        

       
        
```

---

# Complete Workflow

## Step 1 — Infrastructure Provisioning

Infrastructure is provisioned using:
- Terraform
- Ansible

The infrastructure repository automates:
- EC2 provisioning
- Kubernetes cluster setup
- Server configuration
- Environment preparation

Repository:
```text
ecom-infra
```

---

## Step 2 — Application Development

The E-Commerce application source code is maintained in the `ecom` repository.

Developers push code changes to GitHub.

---

## Step 3 — Jenkins CI Pipeline

Jenkins automatically triggers the CI pipeline on code commits.

The pipeline performs:
- Application build
- Automated testing
- SonarQube code quality and security scanning
- Docker image creation
- Docker image push to Docker Hub
- Slack notification for pipeline success/failure

---

## Step 4 — Docker Image Management

After successful CI:
- Docker images are tagged
- Images are pushed to Docker Hub

Example:
```text
ecommerce-app:v1
ecommerce-app:v2
```

---

## Step 5 — Update Kubernetes Deployment Repository

The Jenkins pipeline updates the Docker image tag inside the Helm values/manifests stored in the `ecom-k8s` repository.

This repository acts as the GitOps source of truth for Kubernetes deployments.

---

## Step 6 — Argo CD Continuous Deployment

Argo CD continuously monitors the `ecom-k8s` repository.

When image tags or manifests change:
- Argo CD detects the changes
- Synchronizes the Kubernetes cluster automatically
- Deploys the updated application

This enables automated GitOps-based deployment.

---

## Step 7 — Kubernetes Deployment

The application is deployed inside a Kubernetes cluster running on AWS EC2.

Deployment includes:
- Deployments
- Services
- Helm charts
- Argo CD applications

---

## Step 8 — Monitoring & Logging

The deployed application is monitored using:

### Prometheus + Grafana
Used for:
- Node monitoring
- Pod monitoring
- CPU utilization
- Memory utilization
- Pod health/status
- Kubernetes metrics visualization

Helm repositories were used to install:
- Prometheus
- Grafana

---

### ELK Stack Monitoring

ELK Stack is used for:
- Centralized logging
- API request monitoring
- Application-level monitoring

The setup provides dashboards for:
- All API requests
- Success vs Error requests
- API-specific monitoring
    - Products API
    - Users API
    - Orders API

---

# Technologies Used

## DevOps & CI/CD
- Jenkins
- Argo CD
- GitHub
- GitOps
- Docker Hub
- SonarQube
- Slack Notifications

---

## Infrastructure & Provisioning
- Terraform
- Ansible
- AWS EC2

---

## Containerization & Orchestration
- Docker
- Kubernetes
- Helm

---

## Monitoring & Logging
- Prometheus
- Grafana
- ELK Stack

---

## Application
- MERN Stack
- Node.js
- React.js
- MongoDB
- Express.js

---

# Repository Structure

## ecom

```text
ecom/
│
├── frontend/
├── backend/
├── Jenkinsfile
├── Dockerfile
└── README.md
```

---

## ecom-k8s

```text
ecom-k8s/
│
├── helm/
├── manifests/
├── argocd/
├── values.yaml
└── README.md
```

---

## ecom-infra

```text
ecom-infra/
│
├── terraform/
├── ansible/
└── README.md
```

---

# CI Pipeline Features

The Jenkins pipeline includes:
- Automated build
- Automated testing
- Docker image build
- Docker image push
- SonarQube scanning
- Slack notifications
- GitOps deployment trigger

---

# GitOps Deployment Features

Argo CD provides:
- Continuous synchronization
- Automated deployment
- Drift detection
- Self-healing
- Declarative Kubernetes deployment

---

# Monitoring Features

## Grafana Dashboards

Dashboards include:
- Pod health
- Node status
- CPU usage
- Memory usage
- Kubernetes metrics

---

## ELK Dashboards

Dashboards include:
- Total API requests
- Success vs error requests
- API-level monitoring
- Request analytics

---

# Deployment Flow Summary

```text
Code Commit
    ↓
Jenkins CI Pipeline
    ↓
Test + Scan + Build
    ↓
Docker Image Push
    ↓
Update Helm Values
    ↓
Argo CD Detects Change
    ↓
Kubernetes Deployment
    ↓
Monitoring & Logging
```

---
# Repositories

## Application Repository
```text
https://github.com/ModiniPadmaSree/ecom
```

---

## Kubernetes & GitOps Repository
```text
https://github.com/ModiniPadmaSree/ecom-k8s
```

---

## Infrastructure Repository
```text
https://github.com/ModiniPadmaSree/ecom-infra
```
