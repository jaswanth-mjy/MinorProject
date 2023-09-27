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
   
      ![App Output](https://ci3.googleusercontent.com/mail-img-att/AM67uINr4SstD5xQHJFP9Lk9MQdZS4bA9T7f2Hx0Z_HanxbdGozvye8A3mzXQtLYy_wPzMcTVm6TghUnfO6h3QAesCqVbRtk5TUppd1bHhzVrZthKEjLGr8nOcswRdJuZ3X-yg3P3gi-AbYGW1_S9Ayft3CFBkpcsYfNQPec7c_iPPJoyynX8M27dES5PUn-RYGGq-kKFLEy-Mc8_1KiZLfAUUM6pm5wtflSAqIXlXCjA_rcjiuk_9nuBCNCHB_uOEWjA46SErURV4L6iK8s1fvQwAhWp0gSZ8kMixbLbAKwtSouLzF2smFpcR9qIbX_Q0j8Ser5LqvZzkOfeOz8SJLhN9iBeBxOrJ_RoeaWE1VUuao8GxdZWnZ1ORQCmfv65WI21pa6bo-m1lU2oomV5YtvZFbr_U4lhC2_xuxqB3vi8meB9WN5VtfyiyCTRaDGaLSZPi5s7XHE7o_bl-9CMYff6Jr48urbJSYOLFCGQPvRb51kN7w9qjocZBjoMHaLzEJqn7svTxi7RoCWwwCqh6eCe8IjxVyExllL5ycfUFFKaUMwCTWFu8gAuKt5GfHxorXZYinEn7Ufie66cr_K_oZ1jJwZVvgydHd0HG214scPo7o7pW_rfuWRsra0xwhXgYytI8QRMl59ACZGMYBUPpn2Sb0gCBoXyRdYkC3gFnhAgxR6QKP5Sz2IgmC6Pv9QH24IJulKAwij6BduHu8d9vQ05h-GLN_zHAooafwQjxVHDW7hlhluWZSfyCwM_dZpgJ-JY_DUP9B0rZZPWHRKC20t_N-5WNYbxbtUFPWL5Tewudrcmdly36kV5w5m-oCuWBSRCA3mibImSUuPGhE0XT0QHy-_1OU1_izPoAny0qBm_nURjkGf4iXzJ3G_mJxYeiaYqqnJoR1NRIuxPIAvIGZFxRJl5N-k6CllOZ7XuRmXGG_x-eOy3sdQ6AZACwOoB5TOeNi1vLW3Slj8QRjUJ4ceGLM8KmBG2X6qIbCSJCKNBM94J6v2pTvpesbFd3tIOEne4cHexCHazYtouHd6cy_R=s0-l75-ft)

## Clean Up

Don't forget to clean up your resources when you're done testing your app:

```bash
az aks delete --resource-group myResourceGroup --name myakscluster --yes --no-wait
```

Please replace `your-app-deployment.yaml` with the actual deployment configuration for your application. Make sure you have the necessary Kubernetes manifests or Helm charts ready for deployment.

These instructions will guide users on how to deploy your app to AKS and access it using the provided external IP address.
