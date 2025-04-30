# Deploy Your First App on Kubernetes

In this session, we deploy our first application on Kubernetes by understanding the fundamental concepts and hands-on steps involved.

## ⚠️ Prerequisites:

-The difference between Docker and Kubernetes.

-Kubernetes architecture.

-Installation of Kubernetes clusters.

## 🧠 Key Concepts Covered:

**Why Kubernetes Over Docker?**

-Kubernetes is a cluster system.

-Offers auto-scaling, auto-healing, and enterprise-grade orchestration.

-Abstracts container management using Pods.

**What is a Pod?**

-The smallest deployable unit in Kubernetes.

-A Pod is a wrapper around one or more containers.

-Unlike Docker (CLI-based), Pods are defined declaratively using YAML files.

-YAML allows easier replication, versioning, and sharing via Git.

**YAML File Anatomy**

-Includes apiVersion, kind, metadata, and spec.

-Inside spec, container details like image, port, and volume mounts are specified.

-Use Pods to run single or multiple containers (e.g., sidecar or init containers).

**Benefits of Multi-Container Pods**

-Shared network and storage.

-Useful for log collectors, data processors, etc.

## 🛠️ Tools & Commands:

**Install kubectl**

-Use the official script (for macOS ARM/Intel, Windows, Linux).

-Refer this URL and download based on your OS >> https://kubernetes.io/docs/tasks/tools/

-Verify installation: ```kubectl version```.

**Install a Kubernetes Cluster**

-Recommended for beginners: minikube.

-Alternative (advanced): kind (Kubernetes IN Docker).

-Refer this URL and download based on your OS >>  https://minikube.sigs.k8s.io/docs/start/

-Start Minikube: minikube start.

-Optionally use: --driver=hyperkit (macOS) for better virtualization.

Note: minikube requires 2 CPUs or more, 2 GB of free memory, 20 GB of free disk space.

## Deploy Your First Pod:

1.Create a pod.yaml file using the official Kubernetes documentation (use sample nginx image).

```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```

2.Apply using:

```kubectl create -f pod.yaml```

3.To access/log/debug:

```
minikube ssh
kubectl get pods
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

**Debugging Tips:**

-Use ```kubectl describe pod <pod-name>``` for status/errors.

-Use ```kubectl logs <pod-name>``` to view application logs.
