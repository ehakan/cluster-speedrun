# Cluster Speedrun

## Bootstrap Process

### Create EKS Cluster

1. Setup AWS Account
2. `$ cd terraform && terraform apply`
3. Create kubeconfig using with:
    ```shell
    $ aws eks --region $(terraform output -raw region) update-kubeconfig \
         --name $(terraform output -raw cluster_name)
    ```
   
### Setup GitOps

1. Install ArgoCD with `$ kubectl apply -k kubernetes/apps/argocd`
2. Wait for `argocd/svc/argocd-server` to be ready
3. Apply the bootstrapping app of apps ArgoCD Application manifest with
   `$ kubectl apply -f kubernetes/bootstrap/application.yaml`