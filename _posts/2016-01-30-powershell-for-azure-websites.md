---
layout: post
title: Powershell For Azure Websites
tags: azure powershell website beginners
---

I was thinking of noting down few PowerShell commandlets, as I use them  either during try and test or general practice. Hopefully, this may help the newbies who are trying their hands too.

###### HOW DO I GET STARTED?
I assume you have Windows PowerShell already installed on your box. If you want to know the version, open PowerShell command window and type the following command.

    $PSVersionTable.PSVersion

Now, you can use the Web Platform Installer to install Microsoft Azure Power Shell module.

<img src="/public/image/posts/wpi.png" />

###### HOW DO I START USING AZURE COMMANDLETS?

*I assume, you are going to use ARM (Azure Resource Manager) for all operations.* 

As the first thing, you need to add Azure account so that . simply use this command -

    Add-AzureRmAccount

It'll ask you to provide your login id/password. Upon successful login you should see the output like below


	Environment           : AzureCloud
	Account               : user@domain.com
	TenantId              : 658e8e9a-7e67-4670-aa77-a678102f2852
	SubscriptionId        : 153d8300-85ee-4b3d-bf32-275bff51f1ea
	SubscriptionName      : Subscription 1
	CurrentStorageAccount : 
	

When you are starting a new PowerShell session, you need to login to your Azure account, in order to be able to start issues commands:

	Login-AzureRmAccount   

###### HOW DO I SEE THE LIST OF SUBSCRIPTIONS ON MY ACCOUNT?

    Get-AzureRmSubscription

you should see a list of subscriptions like below

    
    SubscriptionName : Subscription 1
    SubscriptionId   : 153d8300-85ee-4b3d-bf32-275bff51f1ea
    TenantId 		 : 658e8e9a-7e67-4670-aa77-a678102f2852
    State			 : Enabled
    
    SubscriptionName : Subscription 2
    SubscriptionId   : 153d8300-85ee-4b3d-bf32-275bff51f1ea
    TenantId 		 : 658e8e9a-7e67-4670-aa77-a678102f2852
    State			 : Enabled


###### HOW DO I CHOOSE A SUBSCRIPTION TO WORK ON?
If you have multiple subscriptions, 
Use 

	Select-AzureRmSubscription -SubscriptionName "Subscription 1"
	OR
	Select-AzureRmSubscription -SubscriptionId "153d8300-85ee-4b3d-bf32-275bff51f1ea"


###### HOW DO I CREATE A NEW WEBSITE?
First, get the list of locations available to website

	Get-AzureWebsiteLocation

Second, check if the website name is already present.

    Test-AzureName -Website "yourwebsitename"

Third, create the website on a specified location
    
    New-AzureWebsite -Location "Central US" -Name "yourwebsitename"

> your web site should be created as *yourwebsitename.azurewebsites.com*. Please note that, when you create a new website in Azure RM, a new slot is created which is known as production slot.


###### HOW DO I CREATE A NEW DEPLOYMENT SLOT?
At first, make a note that deployment slots are **only available in standard and premium tiers**.
Given that you are using standard tier, use this command to create a new slot:

    New-AzureWebsite -Location "Central US" -Name "yourwebsitename" -Slot "staging"

> Please note that, a deployment slot is nothing but a new copy of your existing website linked to your production slot. In this case, it should be accessible at *yourwebsitename-staging.azurewebsites.com*

###### HOW DO I PUBLISH MY WEBSITE CODE TO AZURE?
To publish your package (say, `C:\Website-Packge.zip`) to a particular slot, use the following command

    Publish-AzureWebsiteProject -Name "yourwebsitename" -Slot "staging" -Package "C:\Website-Packge.zip"

If you ignore the `-Slot` option, you package will be deployed to production slot by default.

###### HOW DO I SWAP TWO SLOTS?
Use the following command

    Switch-AzureWebsiteSlot -Name "yourwebsitename" -Slot1 "staging" -Slot2 "production"

> To know details about each command, use `Get-Help`.
> 
> ex : Get-Help Add-AzureAccount