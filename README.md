# Deploy App to Azure Kubernetes Services (AKS)

## Prerequisites
Before deploying your app to Azure Kubernetes Services, make sure you have the following prerequisites in place:
- An Azure account with the necessary permissions to create and manage resources.
- The [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) installed.
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) installed.

## Deployment Steps

1. **Create an Azure Kubernetes Cluster:**

   Use the Azure CLI to create an AKS cluster. Replace `myakscluster` with your desired cluster name and `myResourceGroup` with your desired resource group name.

   ```bash
   az aks create --resource-group myResourceGroup --name myakscluster --node-count 3 --enable-addons monitoring --generate-ssh-keys
   ```

2. **Configure kubectl to Use Your AKS Cluster:**

   Run the following command to configure `kubectl` to use your AKS cluster.

   ```bash
   az aks get-credentials --resource-group myResourceGroup --name myakscluster
   ```

3. **Deploy Your App:**

   Deploy your application to the AKS cluster using Kubernetes manifests or Helm charts.

   ```bash
   kubectl apply -f your-app-deployment.yaml
   ```

4. **Access Your App:**

   To access your app, use the external IP address provided by Azure. Replace `20.232.233.15` with the actual external IP address assigned to your AKS service.

   ```plaintext
   External IP address: 20.232.233.15
   ```

   The output of your app will be available at:

   ![App Output](http://20.232.233.15/)

## Clean Up

Don't forget to clean up your resources when you're done testing your app:

```bash
az aks delete --resource-group myResourceGroup --name myakscluster --yes --no-wait
```

Please replace `your-app-deployment.yaml` with the actual deployment configuration for your application. Make sure you have the necessary Kubernetes manifests or Helm charts ready for deployment.

These instructions will guide users on how to deploy your app to AKS and access it using the provided external IP address.
