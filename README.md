# Infinity Search Solo — Production-Style Deployment on EKS with GitOps

![Infinity Search Screenshot](images/search.png)

---

## Project Overview

**Infinity Search Solo** is a Flask-based search app deployed on an **AWS EKS cluster** using **GitOps principles**.  
This project demonstrates:

- Containerized Flask app with Docker
- Kubernetes deployment and service manifests
- Public exposure via NGINX Ingress
- HTTPS-ready setup (optional via cert-manager)
- GitOps workflow with ArgoCD (or manual `kubectl apply`)

Thi