# essential-azure-sql

Overview
<https://learn.microsoft.com/en-us/azure/azure-sql/?view=azuresql>

Managed SQL
<https://learn.microsoft.com/en-us/azure/azure-sql/managed-instance/instance-create-quickstart?view=azuresql>

Create edge vm to connect to sql server
<https://learn.microsoft.com/en-us/azure/azure-sql/managed-instance/connect-vm-instance-configure?view=azuresql>

Pool SQL
<https://learn.microsoft.com/en-us/azure/azure-sql/managed-instance/instance-pools-overview?view=azuresql>

Conventional SQL (Windows)
<https://learn.microsoft.com/en-us/azure/azure-sql/virtual-machines/windows/sql-vm-create-portal-quickstart?view=azuresql&tabs=conventional-vm>

Conventional SQL (Linux)
<https://learn.microsoft.com/en-us/azure/azure-sql/virtual-machines/linux/sql-vm-create-portal-quickstart?view=azuresql>

## Step 1

## Step 1 Create a SQL resource

Install azure cli

```bash
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```

Set app variables by saving in .env file

```bash
export SUBSCRIPTION="xxx"
export TENANT="xxx"
export LOCATION="eastus"
export RESOURCE_GROUP="xxx"
```

Set subscription

```bash
source .env
az login --tenant $TENANT
az account set -s $SUBSCRIPTION
```

```bash
source .env
az group create --name $RESOURCE_GROUP \
                --location $LOCATION
az deployment group create --subscription $SUBSCRIPTION \
                           --resource-group $RESOURCE_GROUP \
                           --name rollout01 \
                           --template-file ARMTemplate/ManagedSQL/template.json \
                           --parameters ARMTemplate/ManagedSQL/parameters.json
```

<https://learn.microsoft.com/en-us/azure/azure-sql/managed-instance/connect-vm-instance-configure?view=azuresql>




ssh into sql server

```bash
chmod 400 .ssh/ray-chunkit-chung-vm.pem
ssh -i .ssh/ray-chunkit-chung-vm.pem sqlserveradmin@52.249.248.100
```
