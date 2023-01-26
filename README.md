# Cluster Speedrun

## Bootstrap Process

1. Setup AWS Account
2. `cd terraform && terraform apply`
3. Create kubeconfig using with:
    ```shell
    aws eks --region $(terraform output -raw region) update-kubeconfig \
      --name $(terraform output -raw cluster_name)
    ```
4. TBD
