[Official documentation is here](https://microsoft.github.io/AzureTRE/)

But for a convenient one page guide, this is below : 

1. Fork https://github.com/microsoft/AzureTRE-Deployment (_and not the default AzureTre repository ;)_ )
2. Open it in Visual studio Code - run container (note : GitHub codespace is better if you have access to it)
3. Fill in /config.yaml following TRE documentation  https://microsoft.github.io/AzureTRE/tre-admins/setup-instructions/pre-deployment-steps/ and https://microsoft.github.io/AzureTRE/tre-admins/auth/##create_authentication_assets
4. Run az login & az account set --name "SUBSCRIPTIONNAME" & make auth
5. ON Azure Portal/AAD/Enterprise Application, add yourself as administrator to the "TREID API" app.
6. Create a service principal for github :  az ad sp create-for-rbac --name "RandomAppName" --role owner --scopes /subscriptions/SUBSCRIPTIONID --sdk-auth
7. On Github, create a environment variable named "AZURE_CREDENTIALS" and as value, fill in the result of the previous commands, brackets included
8. Execute
```
gh auth login
repo="name/AzureTRE-Deployment"
env="CICD"
ghvar=$(cat ./config.yaml | grep ":" | grep -v -e '#' | grep -v -e ':$' | sed 's/ //g')
for fn in $ghvar; 
do 
	parameter=$(echo $fn |cut -d ":" -f 1)
	value=$(echo $fn |cut -d ":" -f 2)
	gh secret set $parameter -b $value --repo $repo  --env $env
done
```

Note  : Current missmatch
- TEST_APP_ID is test_account_client_id
- TEST_WORKSPACE_APP_ID is api_client_id
- TEST_WORKSPACE_APP_SECRET is api_client_secret

9. Consider removing the cron schedule from the deploy_tre.yml (this is more for dev purposes and a user should only redeploy for a new release)
10. Run Github Action "Deploy Azure TRE"

Note : you may have to rerun : had an issue to login to ACR first time.

11. Setup is complete. 
12. Connect to https://TREID.LOCATION.cloudapp.azure.com/ to manage your Azure TRE
