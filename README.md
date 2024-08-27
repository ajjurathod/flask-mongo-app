# flask-mongo-app
Overview
This guide details the steps to deploy a Python Flask application connected to MongoDB on a Minikube Kubernetes cluster. It covers application setup, Docker image building, Kubernetes deployment, and scaling.

1. Application Setup
Create Flask Application:
Implement endpoints:
/: Returns "Welcome to the Flask app! The current time is: "
/data: Supports POST requests to insert data into MongoDB and GET requests to retrieve data.
Ensure the application is prepared for deployment with at least 2 replic

2. Building and Pushing the Docker Image
Build the Docker Image:

docker build -t ajjurathod1998/flask-mongodb-app .
Push the Docker Image to Docker Hub:

docker push ajjurathod1998/flask-mongodb-app

4. Kubernetes Setup
Start Minikube:

minikube start

6. Deploying to Kubernetes
Apply the MongoDB Secret:

kubectl apply -f mongodb-secret.yaml

Apply the MongoDB StatefulSet:

kubectl apply -f mongodb-statefulset.yaml

Apply the Flask Deployment:

kubectl apply -f flask-deployment.yaml

Apply the Services:
kubectl apply -f flask-service.yaml
kubectl apply -f mongodb-service.yaml

Check the status of the pods:
kubectl get pods

5. DNS Resolution
Explanation:
Kubernetes handles DNS resolution for inter-pod communication through its internal DNS service. Services are accessible by their names within the cluster. The Flask application connects to MongoDB using the MongoDB service name.


6.Resource Requests and Limits
Resource requests and limits ensure that the pods do not consume more resources than allocated:

Resource Requests: Minimum resources guaranteed for the pod.
Resource Limits: Maximum resources a pod is allowed to consume.

Example configuration:
yaml

resources:
  requests:
    cpu: "200m"
    memory: "250Mi"
  limits:
    cpu: "500m"
    memory: "500Mi"


7. Summary
This guide provides a step-by-step approach to deploying a Flask application with MongoDB on Minikube. It includes setting up the application, building and pushing the Docker image, configuring Kubernetes deployments, and managing resources.  
