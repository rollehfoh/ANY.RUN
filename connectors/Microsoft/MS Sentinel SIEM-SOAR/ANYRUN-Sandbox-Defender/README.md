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

### Article 1

Click below to deploy Azure Logic App

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Frollehfoh%2FANY.RUN%2Fmain%2Fconnectors%2FMicrosoft%2FMS%2520Sentinel%2520SIEM-SOAR%2FANYRUN-Sandbox-URL%2FANYRUN-Sandbox-URL.json)


Коннектор реализован с помощью Azure Logic App и Azure Blob Storage
 1. Генерация инцидента в Microsoft Sentinel, который содержит сущность вида file или URL.
 2. Срабатывание триггера Logic App, который извлекает данные из инцидента (информация об инциденте, о конечной точке, о сущности алерта).
 3. Logic App инциирует анализ URL из инцидента в ANY.RUN Sandbox.
 4. Logic App инициирует Live Response session к конечной точке (через MDE API).
 5. В рамках Live Response session осуществляется извлечение файла из карантина и отправка в Blob Storage с помощью ps1/bash-скрипта.
 6. Logic App отслеживает появление файла в контейнере Blob Storage и отправляет его в ANY.RUN Sandbox через API с параметрами, соответствующими типу объекта и конечной точки.
 7. Logic App обогащает алерт результатами анализа (threatLevelText, threatLevel, score, iocs, task_link), обновляет теги алерта, а также добавляет IoC в список TI.
