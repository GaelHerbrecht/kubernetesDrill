# Hello World Kubernetes Application

This project contains a simple "Hello World" application that is deployed on Kubernetes. Below are the instructions on how to build the Docker image, deploy it to Kubernetes, and access the application.

## Project Structure

```
hello-world-k8s
├── src
│   └── app.py
├── Dockerfile
├── k8s
│   ├── deployment.yaml
│   └── service.yaml
└── README.md
```

## Prerequisites

- Docker
- Kubernetes cluster (e.g., Minikube, GKE, EKS, AKS)
- kubectl command-line tool

## Building the Docker Image

1. Navigate to the project directory:
   ```
   cd hello-world-k8s
   ```

2. Build the Docker image:
   ```
   docker build -t hello-world-app .
   ```

## Deploying to Kubernetes

1. Apply the deployment configuration:
   ```
   kubectl apply -f k8s/deployment.yaml
   ```

2. Apply the service configuration:
   ```
   kubectl apply -f k8s/service.yaml
   ```

## Accessing the Application

- If you are using a LoadBalancer service, you can access the application using the external IP provided by the service.
- If you are using a ClusterIP service, you may need to port-forward to access the application:
  ```
  kubectl port-forward service/hello-world-service 8080:80
  ```
  Then, access the application at `http://localhost:8080`.

## Cleanup

To remove the deployment and service, run:
```
kubectl delete -f k8s/deployment.yaml
kubectl delete -f k8s/service.yaml
```