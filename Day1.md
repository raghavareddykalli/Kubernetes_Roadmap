# Introduction to Kubernetes

In this session, we begin our journey with Kubernetes.

## Key Points Covered:

Kubernetes is Easy: Many people are intimidated by Kubernetes, but it’s simpler than it appears if your basics are clear.

Focus on Kubernetes for DevOps Careers: CI/CD is popular but Kubernetes is essential.

 Long-Term DevOps Journey: Learning just CI/CD may get you initial roles like build/release engineer, but for a solid DevOps career, Kubernetes is crucial.

Prerequisite - Docker: Before learning Kubernetes, you must understand Docker and containers deeply (from basics to security, networking isolation, namespaces, multi-stage builds, etc.).

## Why Kubernetes?

Docker vs Kubernetes:

-Docker is a container platform that helps manage container lifecycle.

-Kubernetes is a container orchestration platform that solves production-grade challenges Docker alone cannot.


## Problems Kubernetes Solves:

**1.Single Host Limitation:**

-In Docker, all containers reside on one host. Resource exhaustion can crash containers unpredictably.

-Kubernetes uses a cluster of nodes (group of machines) preventing one container from affecting others.

**2.Auto-Scaling:**

-Docker cannot auto-scale based on traffic.

-Kubernetes uses YAML configurations and features like Horizontal Pod Autoscaler to scale containers automatically based on load.

**3.Auto-Healing:**

-In Docker, if a container dies, a DevOps engineer must manually restart it.

-Kubernetes automatically detects and replaces failed containers via the API server.

**4.Enterprise-Grade Needs:**

-Docker does not support advanced requirements like auto-healing, load balancing, API gateways, security policies (whitelisting, blacklisting IPs), or resilience needed for enterprise applications.

-Kubernetes addresses many of these, although it is still evolving.

## Additional Insights:

Cluster Nature:

Kubernetes always runs as a cluster (master and worker nodes) in production setups.

Architecture:

Kubernetes has components like API server, controllers, etc., enabling robust container management.

Scaling and Load Balancing:

Kubernetes uses YAML files for deployments, replica sets, and services.

Default Kubernetes load balancing is basic (round-robin), but can be extended using custom resources and third-party solutions.

Security and Extensions:

Kubernetes is highly extensible with Custom Resource Definitions (CRDs).

Offers better security compared to raw Docker, but achieving complete enterprise-level security might need additional configurations.

## Background on Kubernetes:

Developed based on Google’s internal system called Borg.

Kubernetes is open-source and managed by the CNCF (Cloud Native Computing Foundation) with contributions from the global community.
