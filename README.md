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
The [script](https://github.com/wicked-design/wazuh-threema-integration/blob/main/threema-integration) is stored in `/var/ossec/integrations`.
## The configuration
The main config file `/var/ossec/etc/ossec.conf` is used to configure the integration. 
You can customize the integration to send alerts based on levels, rule IDs or groups. 
> [!NOTE]  
> Currently the `<api_key>` field is not used. The secret for the Threema Gateway integration is stored in the integrations script itself.  

> [!NOTE]  
> The  `<api_key>` field could be used to further customize the integration of the Threema Gateway by using specific Threema recpient IDs based on each alert.
> For this one could put `<api_key>THREEMA_RECIPIENT_ID:*THREEMA_SENDER_ID:SECRET</api_key>`.
> In the integration script the `<api_key>` argument could be used like this:
> ```
>        credentials = sys.argv[2].split(`:`)
>        if len(credentials) != 3:
>            logging.error("Invalid credential format")
>            sys.exit(1)
>
>        threema_ID, threema_GW_ID, threema_secret = credentials
> ```
