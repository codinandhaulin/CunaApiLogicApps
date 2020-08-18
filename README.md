# CunaApiLogicApps
Logic apps created to satisfy the 4 API calls for the CUNA Backend Tech Lead Coding Challenge.

I decided that the most straightforward way to implement the 4 API calls would be using Azure Logic Apps, as they are very useful way to orchestrate a workflow of HTTP requests in a very micro-service way.  Data is persited for each request in Azure Cosmos Db.
There is a single Logic App for each HTTP request that must be supported.  I have used Visual Studio 2019 to build the logic apps, as this allows saving incrementally to this GitHub repository.

Deployment
==========
In order to deploy these logic apps to Azure, the reader will need the following created in an Azure account:
  Resource Group
  Cosmos Db (with Core(SQL) API enabled).
  
Each Logic App can be deployed separately - the Azure subscription and resource group will have to be changed in the deployment dialog box.  Additionally, the appropriate Cosmos Db parameters will have to be supplied in the parameters file of each Logic App.

Testing
=======
I have supplied a Postman Collection and corresponding Postman Environment to be used together in testing my endpoints.  They are located in the "Postman artifacts" folder.

Regarding API 1, which calls out to a third-party API.  As configured, a call to "http://example.com/request" is made within the Logic App.  This, of course, will fail.  However, this is useful, as it demonstrates the capability for error handling in the Logic App.  If the call to the third-party API fails, the request item in the database is updated with an ERROR status, and the error status code is returned to the caller.  In order for the API 1 Logic App to run correctly, I recommend replacing the call to "http://example.com/request"  with a call to the public API, "https://jsonplaceholder.typicode.com/posts".  This allows us to make a real POST, and test the Logic App completely.
