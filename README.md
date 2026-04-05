🚀 CI/CD Pipeline with SonarQube, Trivy & EKS
📌 Overview

This project implements an end-to-end CI/CD pipeline using GitHub Actions to automate build, code analysis, security scanning, and deployment to Kubernetes.



🧱 Architecture

Flow:
Developer → GitHub → GitHub Actions → SonarQube → Docker → Trivy → AWS EKS

⚙️ Tech Stack
CI/CD: GitHub Actions
Code Quality: SonarQube
Containerization: Docker
Security: Trivy
Cloud: AWS
Orchestration: Kubernetes (EKS)



🔁 Pipeline Workflow
🔹 Trigger
Manual trigger using:
workflow_dispatch
🔹 Step-by-Step Flow

=> Checkout Code
Pulls latest code from repository
Full history enabled for accurate analysis

=> Code Quality Analysis
Runs SonarQube scan
Detects bugs, vulnerabilities, code smells

=> Setup Environment
Configures Node.js runtime

=> Docker Authentication
Logs into Docker Hub using secrets

=> Build & Push Image
Builds Docker image
Pushes to repository:
manikandan1084/test:new

=> Image Verification
docker pull manikandan1084/test:new

=> Security Scan
trivy image --severity HIGH manikandan1084/test:new
Detects high severity vulnerabilities

=> Configure EKS Access
aws eks --region ap-south-1 update-kubeconfig --name EKS_CLOUD

=> Deploy to Kubernetes
kubectl apply -f deployment.yaml
