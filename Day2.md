# Kubernetes Architecture

In this session, we dive into the Kubernetes Architecture with a focus on making complex concepts simple through real-world examples.

## Quick Fun Fact

**Why is Kubernetes called K8s?**

Kubernetes is often shortened to K8s because there are 8 letters between 'K' and 's'.

(Not an interview question, just for fun!)

## Prerequisite
It's highly recommended to learn docker.

Without knowing Docker's platform and limitations, it’s hard to grasp why Kubernetes architecture exists.

## Key Advantages of Kubernetes Over Docker

Cluster Nature (manages multiple machines as one unit)

Auto-healing (self-recovery from failures)

Auto-scaling (scale applications based on load)

Enterprise-Level Support (advanced networking, security, load balancing)

##Common Misunderstanding

Many resources only describe Kubernetes as having a Control Plane and a Data Plane.

However, simply listing components (API server, etcd, scheduler, etc.) doesn’t give true architectural understanding.

**Approach to Learning**

Compare Docker container creation vs Kubernetes pod creation to understand why Kubernetes needs so many components.

## Deep Dive: Architecture

### Docker vs Kubernetes

**In Docker:**

-Container is the basic unit.

-When you run a container, you rely on Docker Engine and a container runtime (Docker Shim).

**In Kubernetes:**

-Pod is the basic unit (a wrapper over containers providing advanced capabilities).

-Requires multiple components for reliability, scaling, and orchestration.

### Worker Node (Data Plane) Components

-Each Kubernetes Worker Node contains 3 main components:

**Kubelet**

-Ensures pods are running.

-If a pod crashes, informs control plane for corrective action.

**Kube-proxy**

-Manages networking.

-Allocates IP addresses to pods.

-Handles load balancing using IPTables.

**Container Runtime**

-Runs containers inside pods.

-Kubernetes supports multiple runtimes like Docker Shim, containerd, CRI-O, etc., via a standard Container Runtime Interface (CRI).

### Summary:

-At the Worker Node level:

Kubelet: Deploys and monitors pods.

Kube-proxy: Handles networking and service discovery.

Container Runtime: Executes containers inside pods.

### Control Plane (Master Node) Components

The control plane manages the Kubernetes cluster and consists of the following core components:

**API Server**

-The heart of Kubernetes.

-Accepts all requests (e.g., create pods, scale apps).

-Exposes Kubernetes cluster to external users and internal components.

**Scheduler**

-Decides which node a pod should be deployed on based on resource availability.

**etcd**

-A key-value store acting as Kubernetes' backing store.

-Stores all cluster data (state of pods, services, etc.).

**Controller Manager**

-Manages Kubernetes' built-in controllers like ReplicaSet.

-Responsible for ensuring the desired state matches the actual state.

**Cloud Controller Manager**

-Interacts with the underlying cloud provider.

-Manages cloud-specific operations like load balancer creation or storage provisioning.

-Kubernetes offers it as an open-source utility, allowing new cloud providers to integrate.
