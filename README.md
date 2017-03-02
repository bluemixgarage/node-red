# Instructions for deployment on Bluemix

1. Create the Cloudant service - skip this step if you already have a Cloudant instance ready for Node-RED:
```
cf create-service cloudantNoSQLDB <plan> <cloudant_db_name>
```
For example:
```
cf create-service cloudantNoSQLDB Lite myCloudantDb
```

2. Push the Node-RED runtime:
```
cf push <app_name> -i <num_of_instances> -m <memory_limit> --no-start
```
For example:
```
cf push myApp -i 1 -m 768M --no-start
```

3. Bind the Cloudant service to the Node-RED application:
```
cf bind-service <app_name> <cloudant_db_name>
```
For example:
```
cf bind-service myApp myCloudantDb
```

4. Finally start the Node-RED application:
```
cf start <app_name>
```
For example:
```
cf start myApp
```
