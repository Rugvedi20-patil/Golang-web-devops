# Golang-web-devops
End-to-end DevOps project using a Go web application, Docker for containerization, Kubernetes (Minikube) for deployment, NGINX Ingress for traffic routing, Jenkins for CI/CD automation, and Prometheus/Grafana for monitoring.
# Go Web App – End-to-End DevOps Project

An end-to-end DevOps project demonstrating containerization, Kubernetes deployment, traffic routing, CI/CD automation, and monitoring using a Go web application.

## 🚀 Project Overview

This project deploys a Go web application using Docker and Kubernetes (Minikube). NGINX Ingress routes HTTP requests to the application based on the hostname and URL path.

The next stages are to automate the build and deployment process using Jenkins and configure monitoring using Prometheus and Grafana.

## 🛠️ Tech Stack

- **Go** – Web application
- **Git & GitHub** – Source code management
- **Docker** – Containerization
- **Docker Hub** – Container image registry
- **Kubernetes** – Application deployment and orchestration
- **Minikube** – Local Kubernetes cluster
- **NGINX Ingress** – HTTP traffic routing
- **Jenkins** – CI/CD automation
- **Prometheus & Grafana** – Monitoring and visualization

## 🏗️ Architecture

```text
Developer
    |
    v
GitHub Repository
    |
    v
Jenkins CI/CD Pipeline
    |
    v
Build Docker Image
    |
    v
Push Image to Docker Hub
    |
    v
Kubernetes Deployment
    |
    v
Kubernetes Pod
    |
    v
Go Web Application
```

**Traffic routing:**

```text
Browser
   |
   v
NGINX Ingress Controller
   |
   v
Kubernetes Service
   |
   v
Go Application Pod
   |
   v
Application Response
```

## 📂 Project Structure

```text
golangweb/
├── Dockerfile
├── go.mod
├── go.sum
├── *.go
└── k8s/
    └── manifests/
        ├── deployment.yaml
        ├── service.yaml
        └── ingress.yaml
```

*Note: The Go source files and `go.sum` are included if present in the repository.*

## ⚙️ Prerequisites

Install the following tools:

- Git
- Docker Desktop
- Go (optional for local execution)
- kubectl
- Minikube
- Jenkins

## 🐳 Build and Run with Docker

Build the Docker image:

```bash
docker build -t golangweb:v1 .
```

Run the container:

```bash
docker run --rm -p 8082:8080 golangweb:v1
```

Open `http://localhost:8082` in your browser.

If port 8082 is already in use, choose another available host port.

## ☸️ Kubernetes Deployment

Start Minikube:

```bash
minikube start --driver=docker
```

Enable the NGINX Ingress controller:

```bash
minikube addons enable ingress
```

Apply the Kubernetes manifests:

```bash
kubectl apply -f k8s/manifests/deployment.yaml
kubectl apply -f k8s/manifests/service.yaml
kubectl apply -f k8s/manifests/ingress.yaml
```

Check the deployment:

```bash
kubectl get deployments
kubectl get pods
kubectl get services
kubectl get ingress
```

## 🌐 Access the Application

The local Ingress hostname is:

```text
go-web-app.local
```

For the current Windows setup, add the following entry to the hosts file, located at:

`C:\Windows\System32\drivers\etc\hosts`

```text
127.0.0.1 go-web-app.local
```

Start the local port-forward in a separate PowerShell terminal:

```bash
kubectl port-forward -n ingress-nginx service/ingress-nginx-controller 8082:80
```

Open the application:

- `http://go-web-app.local:8082/home`
- `http://go-web-app.local:8082/courses`
- `http://go-web-app.local:8082/about`
- `http://go-web-app.local:8082/contact`

Keep the port-forward terminal running while accessing these URLs.

## 🔄 Planned CI/CD Pipeline

The intended Jenkins pipeline will automate these steps:

1. Retrieve source code from GitHub.
2. Build the Docker image.
3. Run basic validation checks.
4. Push the image to Docker Hub.
5. Update the Kubernetes deployment.
6. Verify that the application is running.

## 📊 Planned Monitoring

Prometheus and Grafana will be configured in a later stage to monitor application and infrastructure metrics.

## 🎯 Learning Outcomes

- Creating and managing Docker images and containers.
- Deploying applications using Kubernetes Deployments and Services.
- Understanding ClusterIP, NodePort, Ingress, and Ingress Controllers.
- Configuring local application access using hostname resolution and port-forwarding.
- Building a Jenkins CI/CD pipeline.
- Learning application and infrastructure monitoring.

## ⚠️ Notes

- Minikube is used for local learning and development, not as a production deployment.
- The Ingress hostname and port-forward configuration are specific to the current local environment.
- Jenkins automation and Prometheus/Grafana monitoring are planned stages until fully configured and tested.
- Never commit passwords, API tokens, credentials, or secret environment files to GitHub.

## 👩‍💻 Author

**Rugvedi Patil**

DevOps learning project focused on Docker, Kubernetes, CI/CD, and monitoring.
