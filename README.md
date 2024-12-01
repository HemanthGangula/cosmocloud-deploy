# Cosmocloud Deployment Helm Chart

This repository contains a Helm chart for deploying an application stack comprising a Backend, Frontend, and Redis database. The project demonstrates my ability to work with Kubernetes and Helm, following real-world DevOps practices.

## Technologies Used
- **Kubernetes**: For container orchestration and resource management.
- **Helm**: To simplify the deployment process by managing Kubernetes resources as a package.
- **Minikube**: For setting up a local Kubernetes cluster.

## How I Deployed the Application

### 1. Installing and Configuring Kubernetes
- First, I installed Minikube to create a local Kubernetes cluster.
- Then, I started Minikube and set up `kubectl` to communicate with the cluster.
- Finally, I checked the cluster status to make sure everything was running smoothly.

### 2. Creating the Helm Chart
- Used the `helm create` command to generate the initial chart structure:
  ```bash
  helm create cosmocloud-deploy
  ```
- Cleaned up unnecessary default files and organized the `templates/` directory into:
  - `backend-deployment.yaml` and `backend-service.yaml`
  - `frontend-deployment.yaml` and `frontend-service.yaml`
  - `redis-deployment.yaml` and `redis-service.yaml`

### 3. Defining Kubernetes Resources
- Configured Deployments:
  - **Backend**: Used `shreybatra/sample-backend` Docker image with the environment variable `REDIS_URI`.
  - **Frontend**: Used `shreybatra/sample-frontend` Docker image with the environment variable `BACKEND_URL`.
  - **Redis**: Used the `redis` image.

- Configured Services:
  - **Backend**: Exposed as `ClusterIP` on port 8000.
  - **Frontend**: Exposed as `NodePort` on port 5175 with NodePort 31000.
  - **Redis**: Exposed as `ClusterIP` on port 6379.

### 4. Deploying the Application
- Installed the Helm chart:
    ```bash
    helm install testapp ./cosmocloud-deploy --atomic --timeout 30s
    ```
- Verified the deployment:
    ```bash
    kubectl get pods
    kubectl get services
    ```
- Accessing the Application:
    - Retrieved the Minikube IP:
    ```bash
    minikube ip
    ```
    - Opened the frontend service in the browser:
    ```bash
    http://<minikube-ip>:31000
    ```

### 5. Cleaning Up
- Uninstalled the Helm chart:
    ```bash
    helm uninstall testapp
    ```



## Project Structure
```bash
cosmocloud-deploy/
├── Chart.yaml               # Helm chart metadata
├── README.md                # Project documentation (this file!)
├── charts/                  # Chart dependencies (none for this project)
├── templates/               # Kubernetes YAML templates
│   ├── backend-deployment.yaml
│   ├── backend-service.yaml
│   ├── frontend-deployment.yaml
│   ├── frontend-service.yaml
│   ├── redis-deployment.yaml
│   ├── redis-service.yaml
│   └── NOTES.txt
└── values.yaml              # Configuration values for the chart
```

## Why This Project Matters
This project showcases my ability to:
- **Deploy Cloud-Native Applications**: Set up a complete stack on Kubernetes using Helm.
- **Follow Real-World Practices**: Use environment variables, service types, and organized chart structures for maintainable deployments.
- **Adapt Quickly**: Learn and implement Kubernetes and Helm concepts efficiently.

By completing this assignment, I demonstrated my readiness to contribute to real-world DevOps workflows.

## Let's Connect
- LinkedIn: [linkedin.com/in/hemanthgangula](https://www.linkedin.com/in/hemanthgangula/)
- HashNode: [hemanthgangula.hashnode.dev](https://hemanthgangula.hashnode.dev/)
