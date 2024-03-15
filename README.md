# MERN-Application-Deployment-in-Kubernetes

This project is a basic implementation of a MERN (MongoDB, Express.js, React.js, Node.js) stack deployed on Kubernetes. It includes a simple web application (Mongo Express) interacting with a MongoDB database, orchestrated using Kubernetes.

# Project Components
The project consists of the following components:

MongoDB Deployment: Deploys a MongoDB instance with a predefined root username and password.
MongoDB Service: Exposes the MongoDB instance within the Kubernetes cluster.
# Enter your own usename and password for secrets
MongoDB Secret: Stores sensitive data (username and password) for MongoDB authentication.  
MongoDB ConfigMap: Stores configuration data for MongoDB URL.
Webapp Deployment: Deploys a web application (Mongo Express) connected to the MongoDB database.
Webapp Service: Exposes the web application outside the Kubernetes cluster.

# Prerequisites
Before setting up this project, ensure you have the following:
AWS EC2 instance running with Minikube and kubectl installed.
Docker installed on your EC2 instance.
Access to the internet from your EC2 instance for pulling Docker images.
Setup Instructions
Clone this repository to your local machine:
git clone <repository-url>

#  Apply the Kubernetes configuration files:
bash
Copy code
kubectl apply -f mongo-config.yaml
kubectl apply -f mongo-secret.yaml
kubectl apply -f mongo-deployment.yaml
kubectl apply -f mongo-service.yaml
kubectl apply -f webapp-deployment.yaml
kubectl apply -f webapp-service.yaml
Wait for the pods to be in a running state:
bash
Copy code
kubectl get pods
Once all pods are running, access the web application using the NodePort service URL. You can get the NodePort service URL by:
bash
Copy code
minikube service Webapp-Service --url
Open the provided URL in a web browser to access the web application.
Usage
Once the web application is accessed, you can interact with it to perform CRUD operations on the MongoDB database.

# Use the provided MongoDB username and password for authentication.

# To clean up the resources created by this project, run the following command:

kubectl delete -f .
# This will delete all resources created by the Kubernetes configuration files