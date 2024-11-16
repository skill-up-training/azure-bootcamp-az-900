# Creer un resources 
 az group create --name MyResourceGroup --location australiaeast

 # Creer un plan de facturation
 ```
 az appservice plan create \
     --name MyAppServicePlan \
     --resource-group MyResourceGroup \
     --sku B1 \
     --is-linux

az appservice plan list --resource-group MyResourceGroup --output table

```

# créer la webapp
```
 az webapp create \
     --resource-group MyResourceGroup \
     --plan MyAppServicePlan \
     --name MyPrivateGitHubApp \
     --runtime "NODE|16-lts"

```
# Créer un deployment 
```
az webapp deployment source config \
  --name MyPrivateGitHubApp \
  --resource-group MyResourceGroup \
  --repo-url https://github.com/skill-up-training/simpleAppNodeJs \
  --branch main \
  --git-token <VOTRE_PAT_GITHUB>
  
```

# Obtenir l'url de l'application
``` az webapp show --resource-group MyResourceGroup --name MyPrivateGitHubApp --query "defaultHostName" -o tsv ```

# Nettoyer les ressources   

``` az group delete --name MyResourceGroup --yes --no-wait```