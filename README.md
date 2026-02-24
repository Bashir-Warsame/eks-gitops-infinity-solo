# Infinity Search Solo — Production-Style Deployment on EKS with GitOps

![Infinity Search Screenshot](images/search.png)  
*Screenshot of the app running via Kubernetes Ingress*

---

## Project Overview

**Infinity Search Solo** is a Flask-based search app deployed on an **AWS EKS cluster** using **GitOps principles**.  
This project demonstrates:

- Containerized Flask app with Docker
- Kubernetes deployment and service manifests
- Public exposure via NGINX Ingress
- HTTPS-ready setup (optional via cert-manager)
- GitOps workflow with ArgoCD (or manual `kubectl apply`)

This setup is **portfolio-ready**, showing a cloud-native production-like deployment without heavy infrastructure.

---

## Prerequisites

- Docker & Docker Hub or AWS ECR account
- AWS CLI configured with access to your account
- `kubectl` installed
- (Optional) `eksctl` for quick cluster creation
- (Optional) ArgoCD for GitOps automation

---

## Step 1 — Build Docker Image

```bash
cd infinity-search-solo
docker build -t infinity-search:1.0 .

aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin <account-id>.dkr.ecr.us-east-1.amazonaws.com
docker tag infinity-search:1.0 <account-id>.dkr.ecr.us-east-1.amazonaws.com/infinity-search:1.0
docker push <account-id>.dkr.ecr.us-east-1.amazonaws.com/infinity-search:1.0