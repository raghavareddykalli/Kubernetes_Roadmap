# Kubernetes Custom Resources & Controllers

In this session, we explore **Custom Resources**, **Custom Resource Definitions (CRDs)**, and **Custom Controllers** in Kubernetes. Below is a detailed breakdown of the key concepts and flow.

## 📘 Topics Covered

- **CRDs (Custom Resource Definitions):**
  - CRDs are used to **extend Kubernetes APIs**.
  - Allow users to define **new resource types** in Kubernetes beyond built-in ones like Pods, Services, etc.
  - Defined using a YAML file that outlines what fields a user can submit.

- **Custom Resources:**
  - Created by users or DevOps engineers based on CRDs.
  - Submitted to the Kubernetes API and **validated against their respective CRDs**.
  - Example: Istio's `VirtualService` is a custom resource defined using a CRD.

- **Custom Controllers:**
  - Required to **watch and act upon Custom Resources**.
  - Written typically in **Golang** (also possible in Python, Java).
  - Use **client-go**, Kubernetes' client library, with components like `Informer`, `Reflector`, and `WorkQueue`.
  - Watch for create/update/delete events on resources and take actions accordingly.

## 🧩 Flow Summary

1. **DevOps Engineer deploys a CRD** (e.g., VirtualService CRD).
2. **User creates a Custom Resource** (e.g., VirtualService instance).
3. **API server validates** the custom resource against the CRD.
4. **Custom Controller (already deployed) watches** for the custom resource and performs actions.

## ⚙️ Controller Development Notes

- Kubernetes natively watches built-in resources like Deployments, Services.
- Custom controllers set up their own watchers.
- **Most controllers are written in Golang** due to Kubernetes’ native implementation.
- `client-go` is the preferred tool for communicating with the Kubernetes API.

## 🚀 Example Projects & Tools

- CNCF landscape includes many custom controllers like:
  - **Istio**
  - **ArgoCD**
  - **Keycloak**
  - **Crossplane**
  - **Prometheus**

- Istio custom resources (like VirtualService) are deployed using:
  - **Helm charts**
  - **Kubernetes manifests**
  - **Operators**

## 🧠 Role of DevOps Engineers

- **Not expected to write custom controllers**, but must:
  - Deploy CRDs and controllers.
  - Understand behavior of custom resources (e.g., Istio's service mesh).
  - Troubleshoot configurations like destination rules, service mesh traffic, etc.

## 📎 Helpful Links

- Istio GitHub: https://github.com/istio/istio
- CNCF Projects: https://www.cncf.io/projects/
- Sample Kubernetes Controller: [Kubernetes Sample Controller GitHub](https://github.com/kubernetes/sample-controller)

---

> Note: Deep controller development (e.g., Golang coding) is more relevant for Kubernetes developers than typical DevOps engineers.
