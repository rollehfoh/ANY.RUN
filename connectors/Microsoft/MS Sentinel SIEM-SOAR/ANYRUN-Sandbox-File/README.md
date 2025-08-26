<p align="center">
    <a href="#readme">
        <img alt="ANY.RUN logo" src="https://raw.githubusercontent.com/anyrun/anyrun-sdk/b3dfde1d3aa018d0a1c3b5d0fa8aaa652e80d883/static/logo.svg">
    </a>
</p>

______________________________________________________________________

# Microsoft Sentinel Connector for automated File analysis via ANY.RUN Interactive Malware Sandbox

## Overview

This playbook allows you to send files from incidents for analysis in the ANY.RUN Sandbox. 
It uploads the file from the endpoint to Azure Blob Storage and then forwards it to the ANY.RUN Sandbox using an Azure Logic App.

Templates are provided for endpoints running the following operating systems:
- Windows
- UNIX (Ubuntu, Debian)

## Requirements:
- ANY.RUN API-Key
- Microsoft Sentinel
- Azure Logic App (Flex Consumption plan)
- Azure Blob Storage
- Microsoft Defender for Endpoint (**Optional**)

## Solution overview

The connector consists of two Azure Logic Apps: 
- Parent workflow (varies depending on the host operating system):
  - [ANYRUN-Sandbox-File-Windows](https://github.com/rollehfoh/ANY.RUN/blob/main/connectors/Microsoft/MS%20Sentinel%20SIEM-SOAR/ANYRUN-Sandbox-File/Logic%20Apps/ANYRUN-Sandbox-File-Windows.json)
  - [ANYRUN-Sandbox-File-Ubuntu](https://github.com/rollehfoh/ANY.RUN/blob/main/connectors/Microsoft/MS%20Sentinel%20SIEM-SOAR/ANYRUN-Sandbox-File/Logic%20Apps/ANYRUN-Sandbox-File-Ubuntu.json)
  - [ANYRUN-Sandbox-File-Debian](https://github.com/rollehfoh/ANY.RUN/blob/main/connectors/Microsoft/MS%20Sentinel%20SIEM-SOAR/ANYRUN-Sandbox-File/Logic%20Apps/ANYRUN-Sandbox-File-Debian.json)
- Child workflow (uniform for all operating systems):
  - [ANYRUN-Submit-File-to-Blob](https://github.com/rollehfoh/ANY.RUN/blob/main/connectors/Microsoft/MS%20Sentinel%20SIEM-SOAR/ANYRUN-Sandbox-File/Logic%20Apps/ANYRUN-Submit-File-to-Blob.json)

## Logic Apps description

### Parent Workflow
This Logic App serves as the main orchestration workflow for the connector. It is triggered by a Microsoft Sentinel incident webhook and processes file entities associated with the incident. The workflow submits files for analysis in ANY.RUN Sandbox obtained from Azure Blob Storage. 

### Child Workflow

 > **Note:** The child playbook in this connector is designed to extract files from the endpoint and upload them to Azure Blob Storage using Microsoft Defender for Endpoint (MDE). If you use a different solution instead of MDE, you can replace this playbook with one adapted for your infrastructure.

This Logic App is a child workflow invoked by the parent to handle file upload from hosts to Azure Blob Storage using Microsoft Defender for Endpoint. It is triggered by an HTTP request from the parent and parses input data. For each file, it initiates MDE live response to execute a script on the host for upload file to Azure Blob Storage.

## Deployment

### Import Azure Logic App template

#### Parent Logic App 

- Click below to deploy Parent Azure Logic App with **Flex Consumption plan**
  - ANYRUN-Sandbox-File-Windows
[![Deploy to Azure]([https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Frollehfoh%2FANY.RUN%2Fmain%2Fconnectors%2FMicrosoft%2FMS%2520Sentinel%2520SIEM-SOAR%2FANYRUN-Sandbox-File%2FLogic%2520Apps%2FANYRUN-Sandbox-File-Windows.json)
  - ANYRUN-Sandbox-File-Ubuntu
[![Deploy to Azure]([https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Frollehfoh%2FANY.RUN%2Fmain%2Fconnectors%2FMicrosoft%2FMS%2520Sentinel%2520SIEM-SOAR%2FANYRUN-Sandbox-File%2FLogic%2520Apps%2FANYRUN-Sandbox-File-Ubuntu.json)
  - ANYRUN-Sandbox-File-Debian
[![Deploy to Azure]([https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Frollehfoh%2FANY.RUN%2Fmain%2Fconnectors%2FMicrosoft%2FMS%2520Sentinel%2520SIEM-SOAR%2FANYRUN-Sandbox-File%2FLogic%2520Apps%2FANYRUN-Sandbox-File-Debian.json)

- Enter the parameters required for deploying the Logic App.

*deployment image*

| Parameter Name                  | Description                                                                 |
|---------------------------------|-----------------------------------------------------------------------------|
| workflows_ANYRUN_Sandbox_File_name | Workflow name       |
| logicAppLocation                | Region for Logic App (for example, eastus or australiaeast). Adapt for your tenant or leave the default value for automatic determination based on your Resource Group. |
| AzureTenantId                   | Tenant ID for authentication in connections.                                |
| AzureClientId                   | Client ID for authentication.                                               |
| azureClientSecret               | Client Secret for authentication.                                           |
| sentinelWorkspaceId             | Workspace ID for Azure Sentinel.                                            |
| keyVaultName                    | Key Vault name.                                                             |
| AzureBlobStorageAccountName             | Azure Blob Storage Account Name.                                           |
| AzureBlobStorageContainerName                    | Azure Blob Storage Container Name.                                                           |

*Sentinel and Key Vault API connections configuration*

#### Child Logic App

- Click below to deploy Child Azure Logic App with **Flex Consumption plan**
  - ANYRUN-Submit-File-to-Blob
 
[![Deploy to Azure]([https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Frollehfoh%2FANY.RUN%2Fmain%2Fconnectors%2FMicrosoft%2FMS%2520Sentinel%2520SIEM-SOAR%2FANYRUN-Sandbox-File%2FLogic%2520Apps%2FANYRUN-Submit-File-to-Blob.json)  

*deployment image*

*Sentinel and Key Vault API connections configuration*

