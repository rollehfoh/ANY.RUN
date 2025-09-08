<p align="center">
    <a href="#readme">
        <img alt="ANY.RUN logo" src="https://raw.githubusercontent.com/anyrun/anyrun-sdk/b3dfde1d3aa018d0a1c3b5d0fa8aaa652e80d883/static/logo.svg">
    </a>
</p>

______________________________________________________________________

# Microsoft Defender for Endpoint Connector for ANY.RUN Malware Sandbox

This repository provides an integration of Microsoft Defender for Endpoint (MDE) with [ANY.RUN](https://any.run/?utm_source=anyrungithub&utm_medium=documentation&utm_campaign=opencti_main&utm_content=linktolanding)'s services:  

* [Interactive Sandbox](https://any.run/features/?utm_source=anyrungithub&utm_medium=documentation&utm_campaign=opencti_main&utm_content=linktosandboxlanding)
* [Threat Intelligence Feeds](https://any.run/threat-intelligence-feeds/?utm_source=anyrungithub&utm_medium=documentation&utm_campaign=opencti_main&utm_term=310725&utm_content=linktofeedslanding) 

The connector automates threat analysis from MDE alerts by retrieving up-to-date data from sandbox detonations of associated objects, enriching alerts with relevant intelligence to optimize investigations.

## Connector capabilities

### Malware Sandbox

The connector triggers automatically on new MDE alerts, extracting entities like URLs or files for submission to the ANY.RUN Interactive Sandbox. It retrieves comprehensive reports—including verdict, threat score, malware tags—adding them as comments to the alert. This provides SOC teams with real-time insights into evasive threats, enabling faster triage, reduced false positives, and proactive response to minimize remedation time.

[Open connector page](https://github.com/rollehfoh/ANY.RUN/tree/main/connectors/Microsoft/Microsoft%20Defender%20for%20Endpoint/ANYRUN-Sandbox-MDE)

### Threat Intelligence Feeds

The connector imports high-fidelity Indicators of Compromise (IoCs) such as IPs, domains, URLs, and hashes from ANY.RUN's real-time sandbox detonations directly into MDE's local Threat Intelligence lists. Continuously updated with indicators from new sandbox analyses of active threats in the wild, this feed expands coverage and empowers SOC teams to detect emerging attacks earlier, update defenses proactively, and correlate alerts with contextual data for more effective hunting and remediation.

[Open connector page](https://github.com/rollehfoh/ANY.RUN/tree/main/connectors/Microsoft/Microsoft%20Defender%20for%20Endpoint/ANYRUN-TI-Feeds-MDE)

### Request support or access to ANY.RUN’s products 

Feel free to reach out to us for help with integration, a quote, or demo via the [contact us form](https://app.any.run/contact-us/). 
