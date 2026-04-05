🚀 CI/CD Pipeline with Security Scan & EKS Deployment
📌 Overview

This project implements a complete CI/CD pipeline using GitHub Actions that automates:

Build process
Code quality analysis using SonarQube
Containerization using Docker
Security scanning using Trivy
Deployment to Amazon EKS
🧱 Architecture Flow
Developer → GitHub → GitHub Actions → SonarQube → Docker Build → Trivy Scan → EKS Deployment
⚙️ Tech Stack
CI/CD: GitHub Actions
Code Quality: SonarQube
Containerization: Docker
Security: Trivy
Cloud: AWS
Orchestration: Kubernetes (EKS)
🔁 Pipeline Workflow Explanation
1. Trigger
on:
  workflow_dispatch:
Manual trigger from GitHub UI
2. Runner
runs-on: [self-hosted]
Uses a self-hosted runner (important for real-world DevOps setups)
3. Checkout Code
uses: actions/checkout@v2
Pulls repository code
fetch-depth: 0 ensures full history for SonarQube analysis
4. Code Analysis (SonarQube)
uses: sonarsource/sonarqube-scan-action@master
Performs:
Code quality checks
Bug detection
Code smells analysis
5. Setup Node Environment
uses: actions/setup-node@v1
Prepares Node.js runtime (for app build)
6. Docker Authentication
uses: docker/login-action@v3
Logs into Docker Hub using secrets
7. Build & Push Docker Image
uses: docker/build-push-action@v5.1.0
Builds container image
Pushes to Docker Hub:
manikandan1084/test:new
8. Image Pull (Verification)
docker pull manikandan1084/test:new
Ensures image is successfully pushed
9. Security Scan (Trivy)
trivy image --severity HIGH manikandan1084/test:new
Scans for vulnerabilities
Focuses on HIGH severity issues
10. Configure Kubernetes Access
aws eks update-kubeconfig
Connects to EKS cluster:
EKS_CLOUD
11. Deploy to Kubernetes
kubectl apply -f deployment.yaml
Deploys application to EKS cluster
🔐 Secrets Required

Configure in GitHub:

SONAR_TOKEN
SONAR_HOST_URL
DOCKER_USER
DOCKER_LOGIN
AWS credentials (for EKS access)
📂 Key Files
.github/workflows/ci.yml   # Pipeline definition
deployment.yaml           # Kubernetes deployment
Dockerfile                # Container build config
🚀 Key Features
✅ End-to-end CI/CD pipeline
✅ Automated code quality analysis
✅ Container-based deployment
✅ Security scanning integrated
✅ Kubernetes deployment (EKS)
✅ Self-hosted runner setup
