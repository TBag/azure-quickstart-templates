# Deploy A Windows VM with MSI

This template shows how to use Managed Service Idenity from within a VM to access azure resources, in particular it shows how to:

- Create a VM with a system assigned idenity
- Install the MSI extension on the VM to allow OAuth tokens to be issued for Azure resources
- Assign RBAC permissions to the Managed Identity
- Run a script that uses Azure PowerShell modules with the MSI

This template creates a new Windows VM with a MSI and deploys the MSI extension to the VM. The MSI associated with the VM is given owner permission on a storage account that is created by the template. A PowerShell script is then run on the VM using the customscript extension , this script installs Azure Powershell Modules and logs in using an OAuth token returned from the token issuing endpoint provided by the MSI extension. It then uses the Azure PowerShell modules to retrieve the keys for the storage account and then writes a blob with a name matching the VM name into the storage account.

The script depends on PowerShell 5.0 or above as it uses PowerShell Package Management to install the Azure AD modules, it therefore requires either Windows Server 2016, or if not using Windows Server 2016 for WMF5 or above to be installed on the VM or for the Package Managment Modules targeted for PowerShell 3 or 4 to be installed. Alternatively the script could be updated to install Azure PowerShell using a different mechamism.

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F201-vm-msi-windows%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
