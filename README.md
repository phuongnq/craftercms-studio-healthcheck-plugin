# CrafterCMS Studio Health Check Plugin

This plugin check if Studio is up and running.

# Installation

Install the plugin via Studio's Plugin Management UI under `Site Tools` > `Plugin Management`.

## Install based on this repository

You can also install this plugin by cloning this repository and using the Studio API.

1. Create a Studio JWT Token.
2. Execute the following CURL command a terminal

```bash
curl --location --request POST 'http://SERVER_AND_PORT/studio/api/2/marketplace/copy' \
--header 'Authorization: Bearer THE_JWT_TOKEN_FOR_STUDIO' \
--header 'Content-Type: application/json' \
--data-raw '{
  "siteId": "editorial",
  "path": "/home/pnguyen/craftercms/plugins/craftercms-studio-healthcheck-plugin"
}'
```

## Usage

```bash
curl http://SERVER_AND_PORT/studio/api/2/plugin/script/plugins/org/craftercms/plugin/healthcheck/monitoring/status.json?siteId=SITE_ID \
--header 'Authorization: Bearer THE_JWT_TOKEN_FOR_STUDIO'
```

Where

* SITE_ID: the site where this plugin is installed
* THE_JWT_TOKEN_FOR_STUDIO: JWT token for Studio

Sample response:

```json
{
  "response": {
    "code": 0,
    "message": "OK",
    "remedialAction": "",
    "documentationUrl": ""
  },
  "result": { "uptime": 834, "startup": "2024-06-13T06:40:30.097Z" }
}
```

**Note**: The response `uptime` and `startup` values are for Studio system-wide. It is not limited to the site where the plugin is installed.