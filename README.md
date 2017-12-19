# Azure Resource Manager Hybrid Use Scripts

Set of scripts to get and toggle Azure Hybrid Use Benefit / Standard licensing - http://blog.superautomation.co.uk/2017/07/convert-azure-windows-virtual-machine.html

__WARNING__ - The Set-AzureRmVmLicenseType.PS1 script has to __destroy__ your existing VM and recreate a new VM based on the old machine spec. __DO NOT__ use this on a machine that you have not backed up. 

You should check your boot diagnostic account on the VM. If it is ZRS somehow, the script won't be able to recreate your VM.

Should now work with Managed Disk VMs.

## Instructions

Log in to your Azure account and select a subscription. If you need the AzureRm Cmdlets, run 'Install-Module AzureRm'

    PS> Login-AzureRmAccount
    
    PS> Select-AzureRmSubscriptionName -SubscriptionName MySubscription

Get a list of VMs and their current license type - Windows\_Server is the hybrid use license type.

    PS> .\Get-AzureRmVmLicenseType.PS1
	
Set a VM to hybrid use benefit

    PS> . .\Set-AzureRmVmLicenseType.PS1 -VmName testvm1 -LicenseType Hybrid -Force
	
Set a VM to regular licensing

    PS> . .\Set-AzureRmVmLicenseType.PS1 -VmName testvm1 -LicenseType Standard -Force
