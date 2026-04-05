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
Manual trigger using workflow_dispatch
🔹 Steps
Checkout Code
Pulls source code with full history for analysis
SonarQube Analysis
Detects bugs
Identifies vulnerabilities
Checks code quality
Setup Node.js
Prepares runtime environment
Docker Login
Authenticates with Docker Hub
Build & Push Image
Image pushed to:
manikandan1084/test:new
Image Verification
Pulls image to confirm successful push
Trivy Security Scan
Scans for HIGH severity vulnerabilities
Configure EKS Access
Connects to AWS EKS cluster
Deploy to Kubernetes
Applies deployment.yaml to cluster
