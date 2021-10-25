# # Barracuda CloudGen Firewall Custom Scripts for Migration
## Introduction
This Azure Resource Manager (ARM) templates in this repo will deploy single instance or clusters of Barracuda CloudGen Firewall F Series virtual machines in an existing VNET. 

## Prerequisites
The solution does a check of the template when you use the provide scripts. It does require that [Programmatic Deployment](https://azure.microsoft.com/en-us/blog/working-with-marketplace-images-on-azure-resource-manager/) is enabled for the Barracuda CloudGen Firewall F BYOL or PAYG images. Barracuda recommends use of **D**, **D_v2**, **DS2_v2**, **F** or newer series. 

You can enable programatic deployment via Powershell using the Cloud Shell feature in the portal. Below are two powershell examples for byol and hourly, please adapt as required to your version of powershell and byol or hourly license requirement.

`Get-AzMarketplaceTerms -Publisher "barracudanetworks" -Product "barracuda-ng-firewall" -Name "byol" | Set-AzMarketplaceTerms -Accept`
`Get-AzureRmMarketplaceTerms -Publisher "barracudanetworks" -Product "barracuda-ng-firewall" -Name "hourly" | Set-AzureRmMarketplaceTerms -Accept`


## Deployed resources
Following resources will be created by these templates:

#Stand Alone
- One virtual machine with network interface, NSG, public IP
- Public IP's SKU's are set to basic and should disassociated and deleted during the appropriate migration steps. 

## Launching the Template - STAND ALONE FIREWALL

The package provides a deploy.ps1 and deploy.sh for Powershell or Azure CLI based deployments. This can be peformed from the Azure Portal as well as the any system that has either of these scripting infrastructures installed. Or you can deploy from the Azure Portal using the provided link.

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fntrifiletti%2Fpowerschool%2F470988f38ff6ac714a36f9151b3918d657f6f7b7%2Fcustom-sa-no-elb-no-rt.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>


#HA Clustered
- Two Virtual machines with network interfaces and public IPs in a Availability Set
- Public IP's SKU's are set to basic and should disassociated and deleted during the appropriate migration steps. 

