# How to run

run ```func start``` from within the LocalFunctionsProject

navigate by following the green link

pass a parameter into the link with ```?name=Function```

## Create a storage account

1. ```az storage account create --name dylansfunctions --location westeurope --resource-group AzureFunctionsContainers-rg --sku Standard_LRS```
2. ```az functionapp plan create --resource-group AzureFunctionsContainers-rg --name myBasicPlan --location westeurope --number-of-workers 1 --sku EP1 --is-linux```

## build n test

1. build - ```docker build --tag dylankentish/azurefunctionsimage:v1.0.0 .``` - REQUIRES THE EXTRA DOT!
2. run - ```docker run -p 8080:80 -it <docker_id>/azurefunctionsimage:v1.0.0```
3. close -  Ctrl+C.

## push

1. ```docker login```
2. ```docker push <docker_id>/azurefunctionsimage:v1.0.0```

## create function app

1. ```az functionapp create --name <app_name> --storage-account dylansfunctions --resource-group AzureFunctionsContainers-rg --plan myBasicPlan --runtime python --deployment-container-image-name dylankentish/azurefunctionsimage:v1.0.0```

## browser in azure

- <https://portal.azure.com/#home>
- <https://portal.azure.com/#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Web%2Fsites/kind/functionapp>
