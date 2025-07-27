# DevOps Project: Containerized Microservices Architecture

This project demonstrates a complete DevOps pipeline for a microservices-based web application using Jenkins, Docker, and Kubernetes on Minikube.

## 🛠️ Tech Stack

- **CI/CD**: Jenkins
- **Containerization**: Docker
- **Orchestration**: Kubernetes (Minikube)
- **Source Control**: Git & GitHub
- **Container Registry**: DockerHub
- **Microservices**:
  - `user-service`: Python Flask
  - `product-service`: Node.js Express
  - `frontend`: React.js

---

## 📦 Microservices Structure

devops-microservices-project/
├── user-service/ # Flask App
├── product-service/ # Node.js App
├── frontend/ # React Frontend
├── k8s/ # Kubernetes YAMLs
└── Jenkinsfile # CI/CD Pipeline Script

🚀 CI/CD Pipeline Workflow

1. Code committed to GitHub
2. Jenkins pipeline triggers:
   - Clones the repo
   - Builds Docker images for each microservice
   - Pushes images to DockerHub
3. Manual deployment to Kubernetes (via kubectl on Windows Minikube)

On your local Minikube machine:
kubectl apply -f k8s/

DockerHub Images
yatindrap6/user-service

yatindrap6/product-service

yatindrap6/frontend

Notes
Jenkins is hosted on AWS Free Tier EC2 (Amazon Linux)

Kubernetes runs locally on Windows via Minikube

Due to EC2 limitations, Kubernetes deployment is manual

