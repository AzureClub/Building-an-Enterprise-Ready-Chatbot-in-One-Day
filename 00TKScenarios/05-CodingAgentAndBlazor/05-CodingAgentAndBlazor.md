# Ask GitHub Coding Agent to build a new UI

## 1) Enable Issues in your fork

![alt text](image.png)

## 2) Register an MCP server (so Copilot can create GitHub issues)

### Create a PAT (required for MCP to act as you)

- Go to: <https://github.com/settings/profile> → Dev → PAT
- Copy the PAT.
- Grant access for the ORGANIZATION (where the repo lives).

![alt text](image-1.png)

![alt text](image-2.png)

### Add `mcp.json` (or configure GitHub MCP Server via Marketplace)

`mcp.json`:

```json
{
  "servers": {
    "io.github.github/github-mcp-server": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/",
      "headers": {
        "Authorization": "${input:Authorization}"
      },
      "gallery": "https://api.mcp.github.com",
      "version": "0.24.1"
    },
    "microsoft/playwright-mcp": {
      "type": "stdio",
      "command": "npx",
      "args": [
        "@playwright/mcp@latest"
      ],
      "gallery": "https://api.mcp.github.com",
      "version": "0.0.1-seed"
    }
  },
  "inputs": [
    {
      "id": "Authorization",
      "type": "promptString",
      "description": "Authentication token (PAT or App token)",
      "password": true
    }
  ]
}
```

### Start the server using your PAT

### Example instruction to the agent

```text
Using github mcp server create issue for building blazor ui for that application. As an additonal folder. Reuse the same backend, so add api on top of existing python app to be called from blazor app
```

If MCP doesn’t work, create the issue manually and then assign Copilot.

## 3) Wait and review the result
