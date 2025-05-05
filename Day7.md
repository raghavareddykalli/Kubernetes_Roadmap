# Introduction to Kubernetes RBAC (Role-Based Access Control)

This session covers the fundamentals of Kubernetes RBAC, its importance in security, and a step-by-step guide on using a **30-day free OpenShift cluster** for hands-on practice.

## 🎯 Key Topics Covered

- **Importance of RBAC**: 
  - RBAC is simple conceptually but can become complex if misconfigured.
  - It's crucial for securing Kubernetes clusters and managing access correctly.

- **Two Main Areas of RBAC**:
  - **User Management**: Assigning access rights to human users like developers, QA engineers, etc.
  - **Service Accounts**: Managing access for applications running in the cluster.

- **Kubernetes Offloads User Management**:
  - Kubernetes does not handle native user creation.
  - It integrates with external Identity Providers (IdPs) like LDAP, GitHub, Google, Okta, or Keycloak.
  - IAM in EKS, AKS, or OpenShift can be used for user authentication.

- **How Access is Managed**:
  - **ServiceAccount/User**: The identity (human or application).
  - **Role/ClusterRole**: Defines permissions.
  - **RoleBinding/ClusterRoleBinding**: Binds roles to users or service accounts.

- **Creating Roles**:
  - Use `Role` for namespace-specific access.
  - Use `ClusterRole` for cluster-wide access.

- **Binding Roles**:
  - Use `RoleBinding` or `ClusterRoleBinding` to attach roles to users or service accounts.

- **Default Behavior**:
  - Every Pod uses a default service account unless specified.
  - Permissions are enforced via RoleBindings.

## 🧪 Practice with OpenShift Sandbox (Free for 30 Days)

1. Go to **OpenShift Sandbox** by searching online.
2. Create or log in with your **Red Hat account**.
3. Launch the cluster and access:
   - **Developer Console**
   - **Admin Console** (limited access)
4. Use `oc` or `kubectl` with your login token to connect via CLI.
5. Perform Kubernetes operations like:
   - `kubectl get pods`
   - Scale deployments
   - Create services, routes, and ingress
6. Try user management features: create service accounts, roles, and role bindings.

