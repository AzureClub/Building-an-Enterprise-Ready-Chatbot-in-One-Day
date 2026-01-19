# GitHub Actions: run `azd pipeline config`

## Goal

Automate deployments using GitHub Actions.

## Prereqs

- You are working in GitHub Codespaces for your **fork**.
- Entra ID: **Application Developer**.
- Azure: **Contributor** on the target resource group.
- You know the target resource group name.
- Preferred regions: Sweden Central / West Europe.
- Subscription: ME-MngEnvMCAP263417-edbartko-2 (589ff257-94b5-4699-bcdf-ce867938ac4d)

Codespaces already includes `azd` and `az`.

```shell
azd version
az version
```

## 1) Sign in to Azure (from the Codespaces terminal)

```shell
azd auth login
```

If browser login fails, use device code:

![alt text](image.png)

![alt text](image-1.png)

```shell
azd auth login --use-device-code
```

## 2) Create your `azd` environment

One environment per participant/team.

```shell
azd env new
```

Use the resource group name as the environment name.

![alt text](image-8.png)

**Important:** Set the correct resource group explicitly. Otherwise `azd` may deploy to the wrong place or create a new resource group based on the environment name.

```shell
azd env set AZURE_RESOURCE_GROUP rg-azureclubworkshopchat-50
```

`main.bicep` uses `targetScope = 'resourceGroup'`.

![alt text](image-10.png)

![alt text](image-9.png)

## 3) Run a one-time manual deploy (required before the pipeline)

```shell
azd up
```

![alt text](image-2.png)

![alt text](image-3.png)

![alt text](image-4.png)

![alt text](image-5.png)

![alt text](image-6.png)

Expected result:

![alt text](image-7.png)

## (Optional) Run locally

```shell
@tomasz_mhent ➜ /workspaces/tomasz-base-app (main) $ chmod +x ./app/start.sh
@tomasz_mhent ➜ /workspaces/tomasz-base-app (main) $ ./app/start.sh
```

![alt text](image-26.png)

![alt text](image-27.png)

![alt text](image-28.png)

## 4) Configure GitHub Actions via `azd pipeline config`

Role required: **User Access Administrator**.

```shell
azd pipeline config
```

![alt text](image-11.png)

![alt text](image-12.png)

New work profile:

![alt text](image-13.png)

![alt text](image-14.png)

![alt text](image-15.png)

![alt text](image-16.png)

![alt text](image-17.png)

Watch for this step:

![alt text](image-18.png)

Service principal + OIDC:

![alt text](image-29.png)

![alt text](image-19.png)

![alt text](image-20.png)

![alt text](image-21.png)

![alt text](image-22.png)

Enable workflows on your fork:

![alt text](image-23.png)

Manual option:

![alt text](image-24.png)

Critical final step:

![alt text](image-25.png)

## Notes

- The workflow is in `.github/workflows/azure-dev.yml` and uses GitHub **Variables** (not Secrets) for most configuration.
- Run `azd pipeline config` after `azd up` so `azd` can persist the environment values.
- If you are not using `main`/`master`, update `on.push.branches` or run the workflow manually.

