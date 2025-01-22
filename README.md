# KV_Cloud_Computing

## Structure, language and illustrations

- Our project is split into two distinct parts, frontend and backend. The Frontened is written in Svelte, the backend in flask. 
- These two parts a hosted as pods in Azure Kubernetes Services. The frontend and backend each have a dev and a production environment.
- The backend works with a MongoDB database, we used CosmosDb with the MongoDB Api enabled.
- Each service is reachable from outside through a Load balancer in AKS.
- The services each have an own repository where the code can be checked out. The deployments and actions are in the original repositories, but the source files are also in this repository
  - Frontend [https://github.com/BirnDo/lectify-frontend](https://github.com/BirnDo/lectify-frontend)
  - Backend [https://github.com/BirnDo/lectify-backend](https://github.com/BirnDo/lectify-backend)
- currently, the last step of the action fails, because AKS is not running all the time because of cost reasons

<img src="https://github.com/user-attachments/assets/92a294b5-f793-4428-b817-543ee3c30511" style="width:50%;" />

## Summary of research
### Kubernetes resources

How to configure Rolling update to our liking and how to use secrets as environment variables. 
For this we mostly used the Kubernetes documentation.

### Github actions
We looked into how we can set up the needed steps of GitHub actions. Different preexisting steps that can be implemented in the pipeline were very helpful.

### AKS
Setting up a new AKS cluster, connecting to AKS and setting up a container registry. THis was all done through the UI and was very straightforward.

### Testing
Testing in python with pytest and testing the frontend with playwright and setting up jobs for each. For this, we mostly used online tutorials and the corresponding documentation.

## Tutorial how to set up
### setting up Azure resources
- Everything can be set up through [Azure Portal](portal.azure.com)
- First create a new resource Group by searching resource group in the search bar. The other components can also be found through the main search bar.
- The needed components are
  - CosmosDb
  - Azure Container Registry
  - Azure Kubernetes services
    - In AKS, select the container registry when setting up, so the images get taken from there
- From these components we need some secrets, which we will go into when they are needed
- Download the Azure CLI to merge the kubeConfig into your local kubeconfig to use it on your PC

### GitHub action
- Multiple secrets are needed for the Actions, namely:
  -  Container registry Username and Password -> These are found in the container registry under Access keys
    - LECTIFYFRONTEND_REGISTRY_USERNAME in frontend
    - LECTIFYFRONTEND_REGISTRY_PASSWORD in frontend
    - LECTIFYBACKEND_REGISTRY_USERNAME in backend
    - LECTIFYBACKEND_REGISTRY_USERNAME in backend
  -  Kube config of AKS base64 encoded. This can be achieved by running ```az aks get-credentials -n <aks-name> -g <resource-group> --file <output-file>``` and encoding it
    - KUBE_CONFIG in front- and backend   

When the Action is set up, run the first deployment locally, since the action only updates the image to the newest version

### Lessons learned
- setting up github actions
- creating and configuring multiple resources in Azure, including container registries, kubernetes clusters and databases
- testing in python and running frontend end to end tests with svelte and playwright
- There are more cost effective ways to deploy your app on Azure e.g. Container Apps, but with the drawback of being platform specific and not so configurable
