# Deploying a Go Web App on Kubernetes with End-to-End CI/CD

This project demonstrates the deployment of a simple Go web application to a Kubernetes cluster using a complete CI/CD pipeline. The setup covers everything from containerization to automated deployments via GitOps.

> **Credit:** The sample Go application is sourced from [iam-veeramalla/go-web-app](https://github.com/iam-veeramalla/go-web-app). The pipeline implementation is inspired by his tutorial, but all configuration and setup have been built independently for this repository.

---

## 📌 Project Overview

The primary objective is to apply DevOps practices to a basic Golang web application by:

- Building a Docker image using a multi-stage build
- Hosting the application in a container
- Automating builds and tests using GitHub Actions (CI)
- Deploying the app to Kubernetes via Argo CD (CD)

---

## 🛠 Tech Stack

- **Language:** Go  
- **Containerization:** Docker  
- **CI Tool:** GitHub Actions  
- **CD Tool:** Argo CD (GitOps)  
- **Orchestration:** Kubernetes (EKS)  
- **Version Control:** GitHub

---

## 📂 Repository Structure

```
.
├── app/                  # Go web app source code
├── manifests/            # Kubernetes deployment and service manifests
├── Dockerfile            # Multi-stage build Dockerfile
├── .github/workflows/    # CI pipeline definitions
└── README.md
```

---

## 🚀 Workflow

### 1. **Containerization**
- Multi-stage Dockerfile builds a minimal, secure image.
- Example build command:
  ```bash
  docker build -t <your-dockerhub-username>/go-web-app .
  ```

### 2. **Continuous Integration (CI)**
- GitHub Actions triggers on every commit to main.
- Steps include:
  - Checkout code
  - Build Docker image
  - Run unit tests
  - Push image to Docker Hub

### 3. **Continuous Deployment (CD)**
- Argo CD monitors the GitHub repository for Kubernetes manifests.
- Syncs changes automatically to the target Kubernetes cluster.

---

## ⚡ Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   cd <your-repo>
   ```

2. **Build locally**
   ```bash
   docker build -t <your-dockerhub-username>/go-web-app .
   docker run -p 8080:8080 <your-dockerhub-username>/go-web-app
   ```

3. **Push image**
   ```bash
   docker push <your-dockerhub-username>/go-web-app
   ```

4. **Deploy with Argo CD**
   - Create an Argo CD app pointing to your GitHub repo’s `manifests/` directory.
   - Sync changes to deploy to your cluster.

---

## 🏁 Conclusion

This project serves as a foundation for deploying containerized applications with an automated CI/CD pipeline. By combining GitHub Actions with Argo CD, we achieve a smooth workflow from code commit to production deployment.
