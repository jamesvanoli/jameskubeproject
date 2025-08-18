# jameskubeproject
# Kubernetes Multi‑Tier MySQL + WordPress Deployment
This repo contains an **incremental Kubernetes deployment** for MySQL + WordPress in the `jameskubeproject` namespace, broken into isolated YAMLs for clean version control.
## Folder Structure
| jameskubeproject/│
├── README.md

## File Map
| File Name                  | Task / Purpose |
|----------------------------|----------------|
| **01-deployments.yaml**    | MySQL & WordPress Deployments (with PVC mounts) |
| **02-services.yaml**       | MySQL ClusterIP & WordPress NodePort Services |
| **03-dashboard-access.yaml** | Dashboard admin ServiceAccount & RBAC binding |
| **04-nfs-server-setup.txt** | Shell commands to prep NFS server |
| **05-nfs-client-setup.txt** | Shell commands to prep NFS clients (K8s nodes) |
| **06-persistent-volumes.yaml** | PV/PVC definitions for MySQL & WordPress |
| **07-secrets.yaml**        | MySQL DB credentials (Secret) |
| **08-configmap.yaml**      | WordPress DB host/user/name (ConfigMap) |

## Apply Order
 Create namespace: ```bash kubectl create namespace jameskubeproject

## Apply manifests in order

kubectl apply -f 01-deployments.yaml

kubectl apply -f 02-services.yaml

kubectl apply -f 03-dashboard-access.yaml

#server-side shell commands to prep NFS

04-nfs-server-setup.txt

#Commands to run on each Kubernetes node

05-nfs-client-setup.txt


kubectl apply -f 06-persistent-volumes.yaml

kubectl apply -f 07-secrets.yaml

kubectl apply -f 08-configmap.yaml
