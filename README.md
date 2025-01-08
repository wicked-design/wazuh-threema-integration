# wazuh-threema-integration
Integration of secure messaging app [Threema](https://threema.ch/) with [Wazuh](https://wazuh.com/).

# Intro
This integration enables Wazuh to send alerts to Threema recipients via the [Threema Gateway](https://gateway.threema.ch/en/developer/api).

> [!NOTE]  
> Usage of the Threema Gateway requires paid credits.

The integration is based on the official [Wazuh integration guide](https://documentation.wazuh.com/current/user-manual/manager/integration-with-external-apis.html#custom-integration).

# Implementation
The integration is done in two parts:
## The integration script
The script is stored in /var/ossec/integrations
## The configuration
The main config file /var/ossec/etc/ossec.conf is used to configure the integration. 
You can customize the integration to send alerts based on levels, rule IDs or groups. 
