<p align="center">
    <a href="#readme">
        <img alt="ANY.RUN logo" src="https://raw.githubusercontent.com/anyrun/anyrun-sdk/b3dfde1d3aa018d0a1c3b5d0fa8aaa652e80d883/static/logo.svg">
    </a>
</p>

______________________________________________________________________

# Microsoft Sentinel Connectors for ANY.RUN Interactive Malware Sandbox

## Overview

This repository contains the necessary resources for integrating Microsoft Sentinel with the ANY.RUN Sandbox. The connectors enrich Microsoft Sentinel incidents by analyzing URLs or files associated with them in the ANY.RUN Sandbox.

As a result, your Microsoft Sentinel incidents will include a verdict, threat score, malware tags and a link to the detailed analysis in the ANY.RUN UI, allowing you to explore the object's behavior in a real infrastructure environment. Additionally, your Threat Intelligence portal in Sentinel will be enriched with Indicators of Compromise (IoCs) extracted during the sandbox analysis.

## Analyze URLs from Microsoft Sentinel Incidents via ANY.RUN Sandbox

This playbook extracts URL from incidents and submit it for analysis in the ANY.RUN Sandbox to enrich the incident with a verdict using a single Azure Logic App.

[Open connector page](https://github.com/rollehfoh/ANY.RUN/tree/main/connectors/Microsoft/MS%20Sentinel%20SIEM-SOAR/ANYRUN-Sandbox-URL)

## Analyze Files from Microsoft Sentinel Incidents via ANY.RUN Sandbox

This playbook allows you to send files from incidents for analysis in the ANY.RUN Sandbox. It uploads the file from the endpoint to Azure Blob Storage and then forwards it to the ANY.RUN Sandbox using an Azure Logic App.

Templates are provided for endpoints running the following operating systems:
- Windows
- UNIX (Ubuntu, Debian)

[Open connector page](https://github.com/rollehfoh/ANY.RUN/tree/main/connectors/Microsoft/MS%20Sentinel%20SIEM-SOAR/ANYRUN-Sandbox-File)

## Analyze All Entities from Microsoft Sentinel Incidents via ANY.RUN Sandbox and Microsoft Defender for Endpoint

This template makes the incident enrichment process in Microsoft Sentinel even more automated if you are also using Microsoft Defender for Endpoint (MDE). In this case, the entire automation mechanism can be combined into a single Azure Logic App, leveraging MDE's capabilities to extract files from endpoints via API.

[Open connector page](https://github.com/rollehfoh/ANY.RUN/tree/main/connectors/Microsoft/MS%20Sentinel%20SIEM-SOAR/ANYRUN-Sandbox-Defender)

## Request Support or Access to ANY.RUN’s Products

Feel free to reach out to us for help with integration, a quote, or a demo via the [contact us form](https://app.any.run/contact-us/?utm_source=anyrungithub&utm_medium=documentation&utm_campaign=opencti_main&utm_content=linktocontactus).
