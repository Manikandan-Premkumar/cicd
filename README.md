🚀 CI/CD Pipeline with SonarQube, Trivy & EKS
📌 Overview

This project implements an end-to-end CI/CD pipeline using GitHub Actions to automate build, analysis, security scanning, and deployment to Kubernetes.

🧱 Architecture
Developer
   ↓
GitHub Repository
   ↓
GitHub Actions (Self-Hosted Runner)
   ↓
SonarQube Analysis
   ↓
Docker Build & Push
   ↓
Trivy Security Scan
   ↓
AWS EKS Deployment
⚙️ Tech Stack
Category	Tool
CI/CD	GitHub Actions
Code Quality	SonarQube
Containerization	Docker
Security Scanning	Trivy
Cloud	AWS
Orchestration	Kubernetes (EKS)
🔁 Pipeline Workflow
🔹 Trigger
Manual trigger using:
workflow_dispatch
🔹 Step-by-Step Flow
1. Checkout Code
Pulls latest code from repository
Full history enabled for accurate analysis
2. Code Quality Analysis
Runs SonarQube scan
Detects bugs, vulnerabilities, code smells
3. Setup Environment
Configures Node.js runtime
4. Docker Authentication
Logs into Docker Hub using secrets
5. Build & Push Image
Builds Docker image
Pushes to repository:
manikandan1084/test:new
6. Image Verification
docker pull manikandan1084/test:new
7. Security Scan
trivy image --severity HIGH manikandan1084/test:new
Detects high severity vulnerabilities
8. Configure EKS Access
aws eks --region ap-south-1 update-kubeconfig --name EKS_CLOUD
9. Deploy to Kubernetes
kubectl apply -f deployment.yaml
