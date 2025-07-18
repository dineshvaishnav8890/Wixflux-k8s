# 🚀 Scalable Web Server with Kubernetes & Docker

This project demonstrates how to containerize a simple web server using Docker and deploy it on a Kubernetes cluster (via Minikube) with horizontal scaling capability.

![Kubernetes + Docker](https://raw.githubusercontent.com/kubernetes/website/main/content/en/images/logo/kubernetes-horizontal-color.png)

---

## 📦 Docker Image

- 🐳 DockerHub Image: [`dineshvaishnav/web-server`](https://hub.docker.com/r/dineshvaishnav/web-server)
- Dockerized lightweight Node.js (or your custom) app.

---

## 🧱 Project Structure

├── k8s/
│ ├── deployment.yaml
│ ├── service.yaml
│ └── hpa.yaml ( for autoscaling)
└── README.md

---

## ⚙️ Prerequisites

- Docker ✅
- Minikube ✅
- kubectl ✅
- DockerHub account (for pushing images) ✅
- hey` or `ab` for load testing


---

## 🐳 Docker Commands (Build & Push)

```bash
# Build image locally
docker build -t dineshvaishnav/web-server:latest .

# Push to DockerHub
docker push dineshvaishnav/web-server:latest

## 📦 Docker Image

![Docker Build](screenshots/Docker-Image.png)




☸️ Deploy to Kubernetes (via Minikube)
Step 1: Start Minikube

minikube start


Step 3: Apply Kubernetes Manifests

kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml


Step 4: Access the Web App
minikube service web-server-service


## Enable Autoscaling (HPA)


Step 1: Enable Metrics Server
minikube addons enable metrics-server




Step 2: Apply HPA

kubectl apply -f k8s/hpa.yaml



Step 3: Simulate Load
hey -z 1m -c 50 http:192.168.49.2:31637




Step 4: Watch Scaling
kubectl get hpa





