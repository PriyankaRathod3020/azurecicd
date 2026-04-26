# In a Kubernetes cluster (like AKS), your nodes are essentially "outsiders" to your private Azure Container Registry (ACR). 
#  Even if they are in the same Azure subscription, Kubernetes needs an explicit "key" to unlock the registry and pull your private images.
    
  ```
shell
   kubectl create secret docker-registry <secret-name> \
    --namespace <namespace> \
    --docker-server=<container-registry-name>.azurecr.io \
    --docker-username=<service-principal-ID> \
    --docker-password=<service-principal-password>
```

# To pull the image with explicit key, "imagePullSecrets" is added in deployment.yml file
 ```
shell
   imagePullSecret:
    - name: acr-secret-key
 ```   
