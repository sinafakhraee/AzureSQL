
# How to call Azure SQL Failver via REST API using Postman on Windows
---
### Create a [service principal](https://docs.microsoft.com/en-us/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) to get Bearer token in order to authenticate the client application (e.g. postman) to call the rest api. 

1. Login to azure using [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) and select your active subscription
&nbsp;![alt text](https://github.com/sinafakhraee/AzureSQL/blob/main/Failover/images/login.PNG)
2. Select your active azure subscription using `az account set --subscription {name of your sub}` command
&nbsp;![alt text](https://github.com/sinafakhraee/AzureSQL/blob/main/Failover/images/subs.PNG)
3. Create the service principal with `az ad sp create-for-rbac` Azure CLI command:
&nbsp;![alt text](https://github.com/sinafakhraee/AzureSQL/blob/main/Failover/images/create_sp.PNG)

### Setting up postman 
[![Run in Postman](https://run.pstmn.io/button.svg)](https://god.gw.postman.com/run-collection/12756893-bf00acfd-390c-441b-b66a-776750bc03e2?action=collection%2Ffork&collection-url=entityId%3D12756893-bf00acfd-390c-441b-b66a-776750bc03e2%26entityType%3Dcollection%26workspaceId%3Df31347ee-af96-4b62-adc6-52c26529f6a6)



