# DevOps Learning Hub - Kubernetes Deployment

A simple Kubernetes Deployment project created for learning and practicing core Kubernetes concepts such as:

- Deployments
- ReplicaSets
- Pods
- Containerized Applications
- Scaling Applications in Kubernetes

This project deploys a Docker container image using a Kubernetes Deployment with 3 replicas.

---

# Project Structure

```bash
DEVOPS-LEARNING-HUB-DEPLOYMENT/
│
├── deployment.yaml
├── output-pods.txt
├── output-rs.txt
└── README.md
```

---

# Kubernetes Deployment Configuration

The deployment uses:

- Kubernetes Deployment (`apps/v1`)
- 3 Pod replicas
- Docker image hosted on Docker Hub
- Container Port: `8000`

---

# Deployment YAML

```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: devops-learning-hub-deployment
  labels:
    app: devops-learning-hub

spec:
  replicas: 3

  selector:
    matchLabels:
      app: devops-learning-hub

  template:
    metadata:
      labels:
        app: devops-learning-hub

    spec:
      containers:
      - name: devops-learning-hub-container
        image: vanshikamod/devops-learning-hub:v1

        ports:
        - containerPort: 8000
```

---

# Prerequisites

Before running this project, make sure you have:

- Docker installed
- Kubernetes Cluster
  - Minikube / KOPS / EKS / AKS / Kind
- kubectl installed and configured

---

# Apply Deployment

Run the following command:

```bash
kubectl apply -f deployment.yaml
```

---

# Verify Deployment

## Check Deployment

```bash
kubectl get deployment
```

## Check ReplicaSet

```bash
kubectl get rs
```

## Check Pods

```bash
kubectl get pods
```

---

# Expected Output

You should see:

- 1 Deployment
- 1 ReplicaSet
- 3 Running Pods

Example:

```bash
NAME                                        READY   STATUS    RESTARTS   AGE
devops-learning-hub-deployment-xxxxx        1/1     Running   0          xx
```

---

# Scaling the Deployment

Increase replicas manually:

```bash
kubectl scale deployment devops-learning-hub-deployment --replicas=5
```

---

# Delete Deployment

```bash
kubectl delete -f deployment.yaml
```

---

# Concepts Covered

This project helps in understanding:

- Kubernetes Deployments
- ReplicaSets
- Pod Management
- Desired State Management
- Self-Healing in Kubernetes
- Scaling Applications

---

# Docker Image

Docker Hub Image Used:

```bash
vanshikamod/devops-learning-hub:v1
```

---

# Author

Vanshika Jaiswal

---

# Learning Purpose

This repository is created as part of a DevOps and Kubernetes learning journey to strengthen hands-on understanding of Kubernetes core concepts.