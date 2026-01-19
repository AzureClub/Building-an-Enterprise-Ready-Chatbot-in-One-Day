# Entra ID Authentication

## Goal

- Track who uses the chatbot, for what, and what data they access.
- Optional: Entra-based document ACL (more complex).

**Important:** In Azure, your account must be allowed to manage applications in Microsoft Entra.

## 1) Update environment settings

```sh
azd env set AZURE_USE_AUTHENTICATION true
azd env set AZURE_AUTH_TENANT_ID b9b9ed6c-c954-45a5-8579-af886f036194
```
(replace with your tenant ID)

## 2) Ask Copilot where these are used

```text
show where AZURE_USE_AUTHENTICATION and AZURE_AUTH_TENANT_ID are used
```

## 3) Reconfigure the pipeline and deploy

Because configuration changed, rerun:

```shell
azd pipeline config
```

Then commit + push.

## (Optional) Run locally

```shell
@tomasz_mhent ➜ /workspaces/tomasz-base-app (main) $ chmod +x ./app/start.sh
@tomasz_mhent ➜ /workspaces/tomasz-base-app (main) $ ./app/start.sh
```

If you see this error:

![alt text](20251213-22-56-a7dnLz58W5.png)

Add an extra redirect URI for your application registration.

Codespaces runs locally and exposes a public URL.

Open:

<https://entra.microsoft.com/?culture=en-us&country=us#home>

Find your app registration GUID:

![alt text](image-1.png)

Add the redirect URI from Codespaces:

![alt text](image-2.png)

![alt text](image.png)

Example format:

<https://friendly-enigma-g4jrqvw6r9gphp4j6-50505.app.github.dev/**redirect**>
