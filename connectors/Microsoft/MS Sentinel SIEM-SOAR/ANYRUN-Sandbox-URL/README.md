<p align="center">
    <a href="#readme">
        <img alt="ANY.RUN logo" src="https://raw.githubusercontent.com/anyrun/anyrun-sdk/b3dfde1d3aa018d0a1c3b5d0fa8aaa652e80d883/static/logo.svg">
    </a>
</p>

______________________________________________________________________

# Microsoft Sentinel Connector for automated URL analysis via ANY.RUN Interactive Malware Sandbox

## Overview

This playbook extracts URL from incidents and submit it for analysis in the ANY.RUN Sandbox to enrich the incident with a verdict using a single Azure Logic App.

## Requirements:
- ANY.RUN API-Key
- Microsoft Sentinel
- Azure Logic App (Flex Consumption plan) 

## Deployment

### Import Azure Logic App template

- Click below to deploy Azure Logic App with **Flex Consumption plan**

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Frollehfoh%2FANY.RUN%2Fmain%2Fconnectors%2FMicrosoft%2FMS%2520Sentinel%2520SIEM-SOAR%2FANYRUN-Sandbox-URL%2FANYRUN-Sandbox-URL.json)

- Enter the parameters required for deploying the Logic App.

*deployment image*

| Parameter Name                  | Description                                                                 |
|---------------------------------|-----------------------------------------------------------------------------|
| workflows_ANYRUN_Sandbox_URL_name | Workflow name         |
| logicAppLocation                | Region for Logic App (for example, eastus or australiaeast). Adapt for your tenant or leave the default value for automatic determination based on your Resource Group. |
| AzureTenantId                   | Tenant ID for authentication in connections.                                |
| AzureClientId                   | Client ID for authentication.                                               |
| azureClientSecret               | Client Secret for authentication.                                           |
| sentinelWorkspaceId             | Workspace ID for Azure Sentinel.                                            |
| keyVaultName                    | Key Vault name.                                                             |

- *Sentinel and Key Vault API connections configuration*
