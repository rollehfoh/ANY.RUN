# Microsoft Defender for Endpoint Azure Connector for VMRay Advanced Malware Sandbox

## Overview

Данный репозиторий содержит необходимые ресурсы для интеграции Microsoft Sentinel и ANY.RUN Sandbox.
Коннектор осуществляет обогащение инцидентов Microsoft Sentinel на основе анализа URL или файлов, содержащихся в инциденте, в ANY.RUN Sandbox.
В конечном итоге инцидент в вашем Microsoft Sentinel будет содержать вердикт, Threat score и ссылку на анализ объекта в UI ANY.RUN, где вы можете более детально ознакомиться с тем, что происходит при использовании объекта в реальной инфраструктуре.
Также ваш Threat Intelligence портал в Sentinel будет обогащаться IoC's, извлеченнымии в процессе анализа в Sandbox.

## Connector capabilities

### Analyze URL's from Microsoft Sentinel incidents

Данный сценарий извлекает URL's from incidents и отпрвляет его на анализ в ANY.RUN Sandbox, для обогащения вердиктом.

Requirments:
- ANY.RUN API-Key
- Microsoft Sentinel
- Azure Logic App (Flex Consumption plan) 

[Open connector page]

### Analyze files from Microsoft Sentinel incidents

Данный сценарий позволяет извлекать 

- Коннектор реализован с помощью Azure Logic App и Azure Blob Storage
 1. Генерация инцидента в Microsoft Sentinel, который содержит сущность вида file или URL.
 2. Срабатывание триггера Logic App, который извлекает данные из инцидента (информация об инциденте, о конечной точке, о сущности алерта).
 3. Logic App инциирует анализ URL из инцидента в ANY.RUN Sandbox.
 4. Logic App инициирует Live Response session к конечной точке (через MDE API).
 5. В рамках Live Response session осуществляется извлечение файла из карантина и отправка в Blob Storage с помощью ps1/bash-скрипта.
 6. Logic App отслеживает появление файла в контейнере Blob Storage и отправляет его в ANY.RUN Sandbox через API с параметрами, соответствующими типу объекта и конечной точки.
 7. Logic App обогащает алерт результатами анализа (threatLevelText, threatLevel, score, iocs, task_link), обновляет теги алерта, а также добавляет IoC в список TI.

Необходим тарифный план Hunter в ANY.RUN и API-ключ вашей учетной записи. 
Мы рекомендуем сохранять ваш API-ключ во встроенном в Azure ресурсе “Key vaults”. 
Для этого необходимо выбрать ваш Key vault или создать новый. 
Затем перейдите в раздел Objects --> Secrets и создайте новый объект с именем ANYRUN-APIKey 
(ВАЖНО! Имя объекта рекомендуется оставить таким же, иначе его придется менять в дальнейшем в развернутом Logic App) 

### Request support or access to ANY.RUN’s products 

Feel free to reach out to us for help with integration, a quote, or demo via the [contact us form](https://app.any.run/contact-us/?utm_source=anyrungithub&utm_medium=documentation&utm_campaign=opencti_main&utm_content=linktocontactus). 
