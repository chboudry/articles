[Official documentation is here](https://microsoft.github.io/AzureTRE/)

But for a convenient one page guide, this is below : 

1. Fork https://github.com/microsoft/AzureTRE-Deployment (_and not the default AzureTre repository ;)_ )
2. Open it in Visual studio Code - run container (note : GitHub codespace is better if you have access to it)
3. Fill in /templates/core/.env and /devops/.env following TRE documentation  https://microsoft.github.io/AzureTRE/tre-admins/setup-instructions/pre-deployment-steps/ and https://microsoft.github.io/AzureTRE/tre-admins/auth/##create_authentication_assets
4. Run az login & make auth
5. Create a service principal for github :  az ad sp create-for-rbac --name "RandomAppName"--role owner --scopes /subscriptions/SUBSCRIPTIONID --sdk-auth
6. Download Github Cli https://github.com/cli/cli/releases
7. Fill in and run the following Powershell script
```
$repo = "your forked repo";
$env = "githubenv";
$Secrets = @{
TRE_ID = "";
AAD_TENANT_ID ="";
LOCATION = "";
AUTO_WORKSPACE_APP_REGISTRATION="";
AUTO_WORKSPACE_GROUP_CREATION="";
CORE_ADDRESS_SPACE="";
TRE_ADDRESS_SPACE="";
MGMT_RESOURCE_GROUP_NAME="";
MGMT_STORAGE_ACCOUNT_NAME="";
TERRAFORM_STATE_CONTAINER_NAME="";
ACR_NAME = "";
APPLICATION_ADMIN_CLIENT_ID="";
APPLICATION_ADMIN_CLIENT_SECRET="";
TEST_ACCOUNT_CLIENT_ID="";
TEST_ACCOUNT_CLIENT_SECRET="";
API_CLIENT_ID="";
API_CLIENT_SECRET="";
SWAGGER_UI_CLIENT_ID=""
CORE_APP_SERVICE_PLAN_SKU=""
AZURE_CREDENTIALS="";
}
$Secrets.keys |  ForEach-Object{ gh secret set $_  -b $Secrets[$_] --repo $repo  --env $env}

```
Note 1 : I provided an order to the parameters to remember easily where the values come from: 
  a. The first 11 comes from your config files you previously set up
  b. Next 7 comes from the make auth result stored in /devops/auth.env
  c. Core app service plan sku is official app service SKU, I choosed "P1v2" as value
  d. Last one AZURE_CREDENTIALS comes from the result of the previous command

Note 2 : you might struggle with AZURE_CREDENTIALS multiline secret, you may add this one manually. 
https://learn.microsoft.com/en-us/azure/developer/github/github-key-vault#define-a-service-principal

Note 3 : you might want to double check the expected the env variables within the workflow to make sure there aren't new ones
If you forgot one, the process will fail in the middle https://github.com/microsoft/AzureTRE-Deployment/issues/31

8. Consider removing the cron schedule from the deploy_tre.yml (this is more for dev purposes and a user should only redeploy for a new release)
9. Run Github Action "Deploy Azure TRE"
10. Setup is complete. 
11. Add yourself as "TRE administrators" within the AAD Enterprise Application "TREID API"
12. Connect to https://TREID.LOCATION.cloudapp.azure.com/ to manage your Azure TRE
