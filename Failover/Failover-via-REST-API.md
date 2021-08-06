
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
1. Download and install <a href="https://www.postman.com/downloads/" target="_blank">Postman</a> 
2. Import AzureSQLFailoverREST collection from link below:\
&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/cf534305e7901550785d)
3. Click on postman for windows:
&nbsp;![alt text](https://github.com/sinafakhraee/AzureSQL/blob/main/Failover/images/postman.PNG)


