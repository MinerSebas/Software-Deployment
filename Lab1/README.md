# Deployment

1. Login

```sh
az login
```

2. Create a resource group

```sh
az group create --name lab1ResourceGroup --location "West Europe"
```

3. Deploy Template

```sh
az deployment group create --name lab1deployment --resource-group lab1ResourceGroup --template-file azuredeploy.json --parameters azuredeploy.parameters.json
```