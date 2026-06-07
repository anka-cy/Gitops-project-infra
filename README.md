# ⚙️ GitOps Pipeline (Infrastructure Repository)

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=for-the-badge&logo=argo&logoColor=white)

This is the **Infrastructure Repository** of a two-part GitOps pipeline. It exclusively holds the Kubernetes deployment manifests for the application.

> 🔗 **Application Repository:** The source code and CI pipeline are located in the [Gitops-project](https://github.com/anka-cy/Gitops-project) repository.

---

## 🏗️ What is this repository for?

By separating the infrastructure configuration into its own repository, we avoid commit conflicts and ensure a secure, auditable deployment history. 

This repository acts as the **Single Source of Truth** for the Kubernetes cluster state.

## 🚀 How it connects to the Pipeline

1. When the CI pipeline in the Application Repository successfully builds a new Docker image, an automated bot commits the new image tag to `k8s/deployment.yaml` in *this* repository.
2. **ArgoCD** continuously watches this repository. 
3. When ArgoCD detects the new commit, it automatically syncs the changes to the Kubernetes cluster, deploying the new application version with zero downtime.

---

### Manifests Included:
- `k8s/deployment.yaml`: Defines the application pods and the specific Docker image tag to run.
- `k8s/service.yaml`: Exposes the application to the network via a NodePort.
