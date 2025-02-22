---
title: Reset Office activation with Microsoft Support and Recovery Assistant
description: Describes available switches and conditions when using the Enterprise version of Microsoft Support and Recovery Assistant to reset Office activation.
author: helenclu    
ms.author: luche
manager: dcscontentpm
audience: ITPro
ms.topic: troubleshooting
localization_priority: Normal
ms.custom: 
  - CSSTroubleshoot
ms.reviewer: gregmans; zebamehdi
appliesto: 
  - Microsoft 365
search.appverid: MET150
ms.date: 10/25/2022
---
# Scenario: Reset Office Activation

The Reset Office Activation scenario automates all the checks that are described and the scripts that are provided in [Reset activation state for Microsoft 365 Apps for enterprise](/office/troubleshoot/activation/reset-office-365-proplus-activation-state).

> [!NOTE]
> This scenario isn't available in the full version of the Microsoft Support and Recovery Assistant.

**Note:** This scenario requires that you use an elevated Command Prompt window. To do this, select **Start**, enter *cmd*, right-click **Command Prompt** in the results, and then select **Run as administrator**.

## Download the Enterprise version of the Assistant

Select the following button:

> [!div class="nextstepaction"]
> [Download the Assistant](https://aka.ms/SaRA_EnterpriseVersionFiles)

For complete details about how to run the Enterprise version of the Assistant, see [Enterprise version of Microsoft Support and Recovery Assistant](sara-command-line-version.md).

## Available switches for the Reset Office Activation scenario

The following switches are available for this scenario. They aren't case-sensitive. Unless noted as optional, the switches are required to run the scenario. You can use more than one optional switch.

|Switch \<parameter\>|Details|Required/Optional|
|---|---|---|
|`-S <scenarioname>`|Specify this switch and `OfficeSharedComputerScenario` as the value of the `scenarioname` parameter to run this scenario.|Required|
|`-AcceptEula`|Specify this switch to accept the End User License Agreement (EULA) and to run this scenario.|Required|
|`-CloseOffice`|Specify this switch to close all Office apps that are running.|Required|

## Sample commands

Here is a sample combination of switches to run this scenario:

- To reset Office activation, run the following command in an elevated Command Prompt window.

  ```console
  SaRAcmd.exe -S ResetOfficeActivation -AcceptEula -CloseOffice
  ```

## Detected conditions and results

When you run the Reset Office Activation scenario by using the Enterprise version of the Assistant, you don't receive any prompts. The following table describes the actions that the Assistant takes for each condition that's encountered by this scenario, and the corresponding output that's displayed.

> [!div class="mx-tdBreakAll"]
> |Condition|Action taken by the Enterprise version|Output shown in the Command Prompt window|
> |---|---|---|
> |Scan completed successfully|Exit the scenario|80: Successful run. Start any Office app and sign-in to activate.|
> |The user didn't include the `-CloseOffice` switch|Exit the scenario|01: This scenario requires the `-CloseOffice` switch. Note, if Office is running, the `-CloseOffice` switch closes Office applications. For additional information, please visit [https://aka.ms/SaRA_CommandLineVersion](https://aka.ms/SaRA_CommandLineVersion).|
> |Error performing any action|Exit the scenario|71: We ran into a problem. Please run the Office Activation scenario in the full UI version of SaRA. You can download SaRA from [https://aka.ms/SaRA-OfficeActivation-Cmdline](https://aka.ms/SaRA-OfficeActivation-Cmdline). |
> |Command Prompt window not elevated|Exit the scenario|72: The scenario requires an elevated command-prompt.|
> |Failure running the OLicenseCleanup script|Exit the scenario|73: We ran into a problem running OLicenseCleanup.vbs. See [https://learn.microsoft.com/office/troubleshoot/activation/reset-office-365-proplus-activation-state](/office/troubleshoot/activation/reset-office-365-proplus-activation-state) for manual reset steps.|
> |Failure running `Dsregcmd`|Exit the scenario|74: We ran into a problem running Dsregcmd. See [https://learn.microsoft.com/office/troubleshoot/activation/reset-office-365-proplus-activation-state](/office/troubleshoot/activation/reset-office-365-proplus-activation-state) for manual reset steps.|
> |Windows build requirement not met|Exit the scenario|75: Windows is not at least Windows 10 version 1803. See [https://learn.microsoft.com/office/troubleshoot/activation/reset-office-365-proplus-activation-state](/office/troubleshoot/activation/reset-office-365-proplus-activation-state) for manual reset steps|
> |Failure to run the `SignOutOfWamAccounts` script|Exit the scenario|76: We ran into a problem running SignOutOfWamAccounts.ps1. See [https://learn.microsoft.com/office/troubleshoot/activation/reset-office-365-proplus-activation-state](/office/troubleshoot/activation/reset-office-365-proplus-activation-state) for manual reset steps.|
> |`WPJCleanup` script requirements not met|Exit the scenario|78: WorkplaceJoined=True, but Windows 10 is not at least version 1809. See [https://learn.microsoft.com/office/troubleshoot/activation/reset-office-365-proplus-activation-state](/office/troubleshoot/activation/reset-office-365-proplus-activation-state) for manual reset steps.|
> |Failure running the `WPJCleanup` script|Exit the scenario|79: We ran into a problem running WPJCleanup. See [https://learn.microsoft.com/office/troubleshoot/activation/reset-office-365-proplus-activation-state](/office/troubleshoot/activation/reset-office-365-proplus-activation-state) for manual reset steps.|
