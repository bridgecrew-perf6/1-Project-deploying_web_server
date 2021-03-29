# Deny creation of resources without any tag

This policy deny whether a creation of a resource has no tag.

## Try with Azure portal

[![Deploy to Azure](http://azuredeploy.net/deploybutton.png)](https://portal.azure.com/?#blade/Microsoft_Azure_Policy/CreatePolicyDefinitionBlade/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-policy%2Fmaster%2Fsamples%2FCompute%2Faudit-existing-linux-vm-ssh-with-password%2Fazurepolicy.json)
[![Deploy to Azure Gov](https://docs.microsoft.com/azure/governance/policy/media/deploy/deployGovbutton.png)](https://portal.azure.us/?#blade/Microsoft_Azure_Policy/CreatePolicyDefinitionBlade/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-policy%2Fmaster%2Fsamples%2FCompute%2Faudit-existing-linux-vm-ssh-with-password%2Fazurepolicy.json)

## Try with Azure PowerShell

````powershell
# Create the Policy Definition (Subscription scope)
$definition = New-AzPolicyDefinition -Name 'deny-creation-resources-without-tag' -DisplayName 'Deny the creation of resources that do not have tags' -description 'This policy denies the creation of resources without tag. In order to create any resource it is mandatory to include coherent tags' -Policy azurepolicy.rules.json -Mode All

# Set the scope to a resource group; may also be a subscription or management group
$scope = Get-AzResourceGroup -Name 'YourResourceGroup'

# Create the Policy Assignment
$assignment = New-AzPolicyAssignment -Name 'deny-creation-resources-without-tag' -DisplayName 'Deny the creation of resources that do not have tags' -Scope $scope.ResourceId -PolicyDefinition $definition
````

## Try with Azure CLI

```cli
# Create the Policy Definition (Subscription scope)
az policy definition create --name "deny-creation-resources-without-tag" --display-name "Deny the creation of resources that do not have tags" --description "This policy denies the creation of resources without tag. In order to create any resource it is mandatory to include coherent tags" --rules tagging-policy.json --mode Indexed

# Create the Policy Assignment
# Set the scope to a resource group; may also be a subscription or management group
az policy assignment create --name "deny-creation-resources-without-tag-assinment" --display-name "Deny the creation of resources that do not have tags Assignment" --scope /subscriptions/<subscriptionId>/resourceGroups/<resourceGroupName> --policy /subscriptions/<subscriptionId>/providers/Microsoft.Authorization/policyDefinitions/deny-creation-resources-without-tag