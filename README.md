# Techdome_Assignment

## Steps to deploy a Frontend and Backend Application to Kubernetes
1. Prerequisites
    * Install Minikube or enable Kubernetes in Docker Desktop
    * Install Kubectl
    * Start Minikube
      ```
      Minikube Start
      ```
    * Ensure Minikube or Docker Kubernetes is the active context
      ```
      kubectl config use-context minikube
      ```

2. Create a Docker Image
    * If using Minikube
      ```
      eval $(minikube docker-env)
      docker build -t frontend-app .
      docker build -t backend-app .
      ```
    * If using Docker Desktop's Kubernetes, push the image to your Docker Hub or a local registry
      ```
      docker tag frontend-app <your-dockerhub-username>/frontend-app
      docker push <your-dockerhub-username>/frontend-app
      ```

3. Write Kubernetes Manifests files
4. Deploy to Kubernetes
   * Apply the manifests to the cluster
     ```
     kubectl apply -f frontend-deployment.yaml
     kubectl apply -f frontend-service.yaml
     ```
   * Verify that the pods and service are running
     ```
     kubectl get pods
     kubectl get svc
     ```

5.  Access the Application
    * If using Minikube, get the service URL
      ```
      minikube service frontend-service
      ```
    * If using Docker Desktop, note the NodePort of the service (e.g., 30080) and access it via
      ```
      http://localhost:<NodePort>
      ```



