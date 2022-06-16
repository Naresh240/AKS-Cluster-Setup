# AKS-Cluster-Setup

## Verify Microsoft.OperationsManagement and Microsoft.OperationalInsights are registered on your subscription. To check the registration status
```sh
az provider show -n Microsoft.OperationsManagement -o table
az provider show -n Microsoft.OperationalInsights -o table
```

## If they are not registered, register Microsoft.OperationsManagement and Microsoft.OperationalInsights using
```sh
az provider register --namespace Microsoft.OperationsManagement
az provider register --namespace Microsoft.OperationalInsights
```
## Create a resource group
```sh
az group create --name crossplane1 --location northeurope
```
## Create AKS cluster
```sh
az aks create --resource-group crossplane1 --name aks-demo-cluster --node-count 1 --node-vm-size standard_D2a_v4 --enable-addons monitoring --generate-ssh-keys
```
## Connect to the cluster
```sh
az aks get-credentials --resource-group crossplane1 --name aks-demo-cluster
```
## Checking nodes
```sh
kubectl get nodes
```
## `Deleting AKS Cluster
```sh
az aks delete --resource-group crossplane1 --name aks-demo-cluster
```
