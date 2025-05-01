# Kubernetes Deployment, ReplicaSets

In this session we will deep dive into Kubernetes Deployments and ReplicaSets. 

## Key Concepts Covered

**Container vs Pod vs Deployment**

-Container: Defined and run using CLI (docker run -it -p -v etc.).

-Pod: A YAML-defined specification for running one or more containers with shared storage and networking.

-Deployment: A higher-level Kubernetes resource that manages Pods via ReplicaSets, enabling features like auto-scaling and auto-healing.

**Why Deployments Instead of Direct Pods?**

-Pods lack auto-scaling and auto-healing capabilities.

-Deployments manage these concerns via an intermediate ReplicaSet.

-Use Deployments for zero-downtime updates, high availability, and self-healing clusters.

## How Deployments Work

-You define the desired state in a deployment.yaml.

-Deployment creates a ReplicaSet.

-ReplicaSet creates and manages the desired number of Pods.

-If a Pod is deleted, ReplicaSet auto-recreates it to match the declared replica count.

##  Interview Questions

1.What is the difference between a Container, Pod, and Deployment?

2.How is a Deployment different from a ReplicaSet?

3.What is a Kubernetes Controller?

  -Maintains desired vs actual state (e.g., ReplicaSet, Deployment).

## Practice
-Create a deployment file using official documentation or github resources

-Below is the sample deployment.yaml file we are going to use in this demo

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

-Create a deployment using the below command 

  ```kubectl apply -f deployment.yaml```

-Check the deployment created
  ```kubectl get deployment```

-As we discussed before, deployment creates Replicaset and Replicaset creates pods.

-We can check Replicaset and pods using below commands

```
kubectl get rs
kubectl get pods
```
 
-The pods created depends on the replicas you provided in the deployment.yaml file.

-If a Pod is deleted, ReplicaSet auto-recreates it to match the declared replica count.

-This is how we can achieve zero-downtime updates, high availability, and self-healing clusters
