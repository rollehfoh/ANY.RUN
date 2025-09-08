<p align="center">
    <a href="#readme">
        <img alt="ANY.RUN logo" src="https://raw.githubusercontent.com/anyrun/anyrun-sdk/b3dfde1d3aa018d0a1c3b5d0fa8aaa652e80d883/static/logo.svg">
    </a>
</p>

______________________________________________________________________

# Microsoft Defender for Endpoint Connector for ANY.RUN Malware Sandbox

## Overview

This connector integrates Microsoft Defender for Endpoint (MDE) with the ANY.RUN Sandbox to enrich MDE alerts through automated malware analysis. It triggers automatically upon the registration of a new alert in MDE, extracting and analyzing entities such as URLs or files associated with the alert.

The enrichment process adds valuable context directly to the alert: comments include the ANY.RUN verdict, threat score, a link to the detailed analysis report, and any Indicators of Compromise (IoCs) discovered during the sandbox detonation. Extracted IoCs are also imported into MDE's local Threat Intelligence lists for enhanced detection and response.

This integration empowers SOC teams with deeper insights into potential threats, accelerating triage, reducing false positives, and enabling proactive hunting — all while leveraging ANY.RUN's interactive sandbox capabilities for real-time behavioral analysis.

## Requirements
- Microsoft Defender for Endpoint
- ANY.RUN API Key
- Microsoft Azure resources:
  - Logic App with Flex Consumption plan
  - Function App Flex Consumption plan
  - Blob Storage

## Solution Overview
 
## Deployment

### Deploy Azure Function App

- Click below to deploy Azure Function App with **Flex Consumption plan**
 
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Frollehfoh%2FANY.RUN%2Fmain%2Fconnectors%2FMicrosoft%2FMicrosoft%2520Defender%2520for%2520Endpoint%2FANYRUN-Sandbox-MDE%2FFunction%2520App%2FANYRUN-Sandbox-MDE-FA.json)

### Deploy Azure Logic App

- Click below to deploy Azure Logic App with **Flex Consumption plan**
 
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Frollehfoh%2FANY.RUN%2Fmain%2Fconnectors%2FMicrosoft%2FMicrosoft%2520Defender%2520for%2520Endpoint%2FANYRUN-Sandbox-MDE%2FLogic%2520App%2FANYRUN-Sandbox-MDE-LA.json)

![logic_app_deployment](images/001.png)

- Description of the required parameters:

| Parameter Name                  | Description                                                                 |
|---------------------------------|-----------------------------------------------------------------------------|
| logicAppName                    | Workflow name.                                                              |
| azureTenantId                   | Tenant ID for authentication in connections.                                |
| azureClientId                   | Client ID for authentication (ID of the App Registration created before).   |
| azureClientSecret               | Client Secret for authentication.                                           |
| functionAppName                 | Name of the Function App deplyed before.                                    |


## Microsoft Defender for Endpoint Configuration

> **Note:** To allow the connector to extract all files of interest from endpoints (including potentially dangerous ones), we recommend setting `Quarantine` as the default action for your MDE. **!ATTENTION!** Be careful when configuring antivirus policies, as this can be potentially dangerous. See:
>
> - [Configure remediation for Microsoft Defender Antivirus detections](https://learn.microsoft.com/en-us/defender-endpoint/configure-remediation-microsoft-defender-antivirus)
>
> - [Settings for Microsoft Defender Antivirus policy in Microsoft Intune for Windows devices](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-windows)

### Enable Live Response Sessions

- Open your [MDE portal](https://security.microsoft.com).

- Navigate to **System** > **Settings** > **Endpoints** > **General** > **Advanced features**.

- Enable the following settings: **Live Response**, **Live Response for Servers**, and **Live Response unsigned script execution**.

![enable_live_response](images/002.png)

## Logic App Configuration (Optional)
