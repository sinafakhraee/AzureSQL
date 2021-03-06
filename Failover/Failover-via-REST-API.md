
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
4. AzureSQLFailoverREST collection gets imported and you will see it under collections in Postman:
&nbsp;![alt text](https://github.com/sinafakhraee/AzureSQL/blob/main/Failover/images/imported.PNG)
5. Right click on AzureSQLFailoverREST collection and click edidt. Select variables tab. Here we will set the collection level variables which are used by the REST APIs in the collection (here we only have one post request)
&nbsp;![alt text](https://github.com/sinafakhraee/AzureSQL/blob/main/Failover/images/vars.PNG)  
**clientid** is the value of appId from the service principal creation output above.\
**clientSecret** is the value of password from the service principal creation output above.\
**tenantId** is the value of tenamt from the service principal creation output above.\
**resourse** is https://management.azure.com/ \
If you dont have failover group and SQL DB setup,please go through this [Tutorial: Add an Azure SQL Database to an autofailover group](https://docs.microsoft.com/en-us/azure/azure-sql/database/failover-group-add-single-database-tutorial?tabs=azure-portal) and fill out the rest of variables accordingly. \
**bearerToken** will be generated by the [pre-request script](https://github.com/sinafakhraee/AzureSQL/blob/main/Failover/js/pre-request-script.js) which was downloaded and is in the collection under the `Pre-request Scripts`. Please see the image below. So you don't need to set the bearerToken manually. \
&nbsp;![alt text](https://github.com/sinafakhraee/AzureSQL/blob/main/Failover/images/script.PNG)
### Execute the post request
1. Submit the post request which would return the opertaion and start time.
&nbsp;![alt text](https://github.com/sinafakhraee/AzureSQL/blob/main/Failover/images/post-request.PNG)
2. Click on response header and note the Azure-AsyncOperation which can be invoked to get the status of the asynchronous failover operation. 
&nbsp;![alt text](https://github.com/sinafakhraee/AzureSQL/blob/main/Failover/images/async.PNG)
3. Create a new Get request in the same collection in order to use the variables we have already setup (token, subscription, etc.) and paste the Azure-AsyncOperation url from 2. submit the request and you will see the status of the failover operation. 
&nbsp;![alt text](https://github.com/sinafakhraee/AzureSQL/blob/main/Failover/images/asyn-response.PNG)
4. If you go to your azure portal and select the failover group you created earlier you will notice that primary and secondary servers are swapped now.   
&nbsp;![alt text](https://github.com/sinafakhraee/AzureSQL/blob/main/Failover/images/servers-swapped.PNG)



