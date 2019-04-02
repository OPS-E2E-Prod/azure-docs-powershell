---
title: Overview of Azure Stack Admin PowerShell | Microsoft Docs
description: An overview of Azure Stack Admin PowerShell with instructions for installation and configuration.
author: sijuman 
ms.author: sijuman
manager: knithinc
ms.devlang: powershell
ms.topic: conceptual
ms.manager: knithinc
ms.date: 02/06/2019
---
# Azure Stack Module 1.7.1

## Requirements:

Minimum supported Azure Stack version is 1901.

Note: For earlier versions of Azure Stack check [Install Azure Stack Powershell](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-install#install-azure-stack-powershell)

## Install

```powershell
# Remove previous versions of AzureStack and AzureRM modules
Get-Module -Name Azs.* -ListAvailable | Uninstall-Module -Force -Verbose
Get-Module -Name Azure* -ListAvailable | Uninstall-Module -Force -Verbose

# Install and import the API Version Modules required by Azure Stack into the current PowerShell session.
Install-Module -Name AzureRM -RequiredVersion 2.4.0

# Install Azure Stack Admin Module
Install-Module -Name AzureStack -RequiredVersion 1.7.1
```

## Release Notes

* Supported with 1901 update
* This a breaking change release. For details on the breaking changes, refer to <https://aka.ms/azspshmigration170>
* Azs.Backup.Admin Module
        * Breaking change: Backup changes to cert-based encryption mode. Support for symmetric keys is deprecated.
* Azs.Fabric.Admin Module
        * Deprecation
            * Get-AzsInfrastructureVolume has been deprecated, we provide new cmdlet Get-AzsVolume
            * Get-AzsStorageSystem has been deprecated, we provide new cmdlet Get-AzsStorageSubSystem
            * Get-AzsStoragePool has been deprecated, the StorageSubSystem object has the capacity property
* Azs.Compute.Admin Module
            * BugFix: Add-AzsPlatformImage, Get-AzsPlatformImage : Calling ConvertTo-PlatformImageObject only in the success path
            * BugFix: Add-AzsVmExtension, Get-AzsVmExtension : Calling ConvertTo-VmExtensionObject only in the success path
* Azs.Storage.Admin Module
            * Bug fix - New Storage Quota uses defaults if none provided.'
