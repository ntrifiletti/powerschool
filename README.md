# # Barracuda CloudGen Firewall Custom Scripts for Migration
## Introduction
These Azure Resource Manager (ARM) templates in this repo will deploy single instance or HA clusters of Barracuda CloudGen Firewall F Series virtual machines in an existing VNET. These bare bones configuration are purpose exclude Azure Load Balancers, Routing tables and the applicable variables.

These templates are useful when migrating to existing resource groups, vnets and where you intend to reuse existing infrastructure. 

## Prerequisites
The solution does a check of the template when you use the provide scripts. It does require that [Programmatic Deployment](https://azure.microsoft.com/en-us/blog/working-with-marketplace-images-on-azure-resource-manager/) is enabled for the Barracuda CloudGen Firewall F BYOL or PAYG images. Barracuda recommends use of **DS2_v2**, **Dv3_v3**, or newer series. 

You can enable programmatic deployment via Powershell using the Cloud Shell feature in the portal. Below are two powershell examples for byol and hourly, please adapt as required to your version of powershell and byol or hourly license requirement.

`Get-AzMarketplaceTerms -Publisher "barracudanetworks" -Product "barracuda-ng-firewall" -Name "byol" | Set-AzMarketplaceTerms -Accept`
`Get-AzureRmMarketplaceTerms -Publisher "barracudanetworks" -Product "barracuda-ng-firewall" -Name "hourly" | Set-AzureRmMarketplaceTerms -Accept`




## DEPLOY SINGLE INSTANCE FIREWALL
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fntrifiletti%2Fpowerschool%2F470988f38ff6ac714a36f9151b3918d657f6f7b7%2Fcustom-sa-no-elb-no-rt.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

Following resources will be created by these templates:

- One virtual machine with network interface, NSG, public IP
- Public IP's SKU's are set to basic and should dissociated and deleted during the appropriate migration steps.
- Deploys into existing resource group and VNET
- Template has parameter to set static IP address during preconfiguration 














## DEPLOY HIGH AVAILABILITY CLUSTER
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fntrifiletti%2Fpowerschool%2Fmain%2Fcustom-ha-as-no-elb-no-rt.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

Following resources will be created by these templates:
`Important - You must modify this template in Azure ARM or prior to execution to set the STATIC IP address for each firewall!'`
- Two Virtual machines with network interfaces and public IPs in a Availability Set
- Deploys into existing resource group and VNET
- Public IP's SKU's are set to basic and should disassociated and deleted during the appropriate migration steps. 





