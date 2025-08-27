<p align="center">
    <a href="#readme">
        <img alt="ANY.RUN logo" src="https://raw.githubusercontent.com/anyrun/anyrun-sdk/b3dfde1d3aa018d0a1c3b5d0fa8aaa652e80d883/static/logo.svg">
    </a>
</p>

______________________________________________________________________

# Microsoft Sentinel Connector for automated File and URL analysis via ANY.RUN Interactive Malware Sandbox and Microsoft Defender for Endpoint

## Overview

This template makes the incident enrichment process in Microsoft Sentinel even more automated if you are also using Microsoft Defender for Endpoint (MDE). 
In this case, the entire automation mechanism can be combined into a single Azure Logic App, leveraging MDE's capabilities to extract files from endpoints via API.

## Requirements:
- ANY.RUN API-Key
- Microsoft Sentinel
- Azure Logic App (Flex Consumption plan)
- Azure Blob Storage
- Microsoft Defender for Endpoint

## Deployment

### Import Azure Logic App template

- Click below to deploy Azure Logic App with **Flex Consumption plan**

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Frollehfoh%2FANY.RUN%2Fmain%2Fconnectors%2FMicrosoft%2FMS%2520Sentinel%2520SIEM-SOAR%2FANYRUN-Sandbox-Defender%2FANYRUN-Sandbox-Defender.json)

- Enter the parameters required for deploying the Logic App.

*deployment image*
