# Microsoft Sentinel Azure Connectors for ANY.RUN Interactive Malware Sandbox

## Overview

Данный репозиторий содержит необходимые ресурсы для интеграции Microsoft Sentinel и ANY.RUN Sandbox.
Коннектор осуществляет обогащение инцидентов Microsoft Sentinel на основе анализа URL или файлов, содержащихся в инциденте, в ANY.RUN Sandbox.
В конечном итоге инцидент в вашем Microsoft Sentinel будет содержать вердикт, Threat score и ссылку на анализ объекта в UI ANY.RUN, где вы можете более детально ознакомиться с тем, что происходит при использовании объекта в реальной инфраструктуре.
Также ваш Threat Intelligence портал в Sentinel будет обогащаться IoC's, извлеченнымии в процессе анализа в Sandbox.

## Analyze URL's from Microsoft Sentinel incidents via ANY.RUN Sandbox

Данный сценарий извлекает URL's from incidents и отпрвляет его на анализ в ANY.RUN Sandbox, для обогащения вердиктом.

[Open connector page](https://github.com/rollehfoh/ANY.RUN/tree/main/connectors/Microsoft/MS%20Sentinel%20SIEM-SOAR/ANYRUN-Sandbox-URL)

## Analyze files from Microsoft Sentinel incidents via ANY.RUN Sandbox

Данный сценарий позволяет отправлять файлы, содержащиеся в инциденте, на анализ в ANY.RUN Sandbox. 
Сценарий осуществляет отправку файла с эндпоинта в Azure Blob Storage и его дальнейшую передачу в ANY.RUN Sandbox для анализа с помощью Azure Logic App.

Шаблоны предусмотрены для эндпоинтов со следующими ОС:
 - Windows
 - UNIX (Ubuntu, Debian)

[Open connector page](https://github.com/rollehfoh/ANY.RUN/tree/main/connectors/Microsoft/MS%20Sentinel%20SIEM-SOAR/ANYRUN-Sandbox-File)

## Analyze all entities from Microsoft Sentinel incidents via ANY.RUN Sandbox and Microsoft Defender for Endpoint

Данный шаблон позволит сделать процесс обогащения инцидентов Microsft Sentinel еще более автоматизированным, если вы также используете Microsoft Defender for Endpoint (MDE). 
В таком случае, весь механизм автоматизации можно объединить в одном Azure Logic App, благодаря возможностям MDE, который сможет извлекать файлы с эндпоинтов по API.

[Open connector page](https://github.com/rollehfoh/ANY.RUN/tree/main/connectors/Microsoft/MS%20Sentinel%20SIEM-SOAR/ANYRUN-Sandbox-Defender)


### Request support or access to ANY.RUN’s products 

Feel free to reach out to us for help with integration, a quote, or demo via the [contact us form](https://app.any.run/contact-us/?utm_source=anyrungithub&utm_medium=documentation&utm_campaign=opencti_main&utm_content=linktocontactus). 
