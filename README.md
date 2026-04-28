# Node.js Application with Minikube

This is a simple Node.js application configured to run on Kubernetes using Minikube.

## Prerequisites

- Minikube installed
- kubectl installed
- Docker installed

## Setup Steps

### 1. Start Minikube

```bash
minikube start
```

### 2. Build the Docker image

Point your shell to use Minikube's Docker daemon:

```bash
eval $(minikube docker-env)
```

Then build the image:

```bash
docker build -t node-app:latest .
```

### 3. Deploy to Minikube

Apply the Kubernetes manifests:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

### 4. Verify Deployment

Check the deployment status:

```bash
kubectl get deployments
kubectl get pods
kubectl get services
```

### 5. Access the Application

Get the Minikube IP:

```bash
minikube ip
```

Access the app using:

```bash
curl http://<minikube-ip>:30000
```

Or use port-forward:

```bash
kubectl port-forward svc/node-app-service 3000:80
```

Then access at `http://localhost:3000`

### 6. View Logs

```bash
kubectl logs -f deployment/node-app
```

### 7. Clean up

Delete the resources:

```bash
kubectl delete -f deployment.yaml
kubectl delete -f service.yaml
```

Stop Minikube:

```bash
minikube stop
```
