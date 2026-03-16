# Timeweb Cloud MCP Server — Cursor Plugin

Official Cursor plugin that connects the **Timeweb Cloud** MCP server so you can manage cloud infrastructure from the editor.

## What this plugin does

- Adds the **Timeweb Cloud MCP Server** to Cursor with one click (no manual `mcp.json` editing).
- Uses the npm package [`timeweb-mcp-server`](https://www.npmjs.com/package/timeweb-mcp-server); the plugin only provides the Cursor/Marketplace integration.

## MCP tools included

| Category           | Tools                                                                                                          |
| ------------------ | -------------------------------------------------------------------------------------------------------------- |
| **Apps**           | `create_timeweb_app` — create and deploy apps with auto-detected framework and settings                        |
| **VCS**            | `add_vcs_provider`, `get_vcs_providers`, `get_vcs_provider_repositories`, `get_vcs_provider_by_repository_url` |
| **Config**         | `get_allowed_presets`, `get_deploy_settings`                                                                   |
| **Infrastructure** | `create_floating_ip`, `create_vpc`                                                                             |
| **Databases**      | `create_database`, `get_database_presets`                                                                      |
| **Prompts**        | `create_app_prompt`, `add_vcs_provider_prompt`                                                                 |

## Setup

1. Install the plugin from Cursor Marketplace.
2. Get an API token from [Timeweb Cloud](https://timeweb.cloud/my/api-keys).
3. When prompted (or in Cursor MCP settings), set `TIMEWEB_TOKEN` to your token.
4. Restart Cursor if needed.

The plugin configures the server as:

- **Command:** `npx`
- **Args:** `["timeweb-mcp-server"]`
- **Env:** `TIMEWEB_TOKEN` (your API token)

## Usage

In Cursor chat you can say, for example:

- _"Deploy my app to Timeweb Cloud"_
- _"Create an app in Timeweb from this repo"_
- _"Add my GitHub repo as a VCS provider in Timeweb"_

The MCP server will use your project (framework, repo) to create and deploy the app in Timeweb Cloud.

## Important

After creating an app, set environment variables in the [Timeweb Cloud console](https://timeweb.cloud/my); the MCP server cannot read your local `.env`.

## Links

- **MCP server (npm):** [timeweb-mcp-server](https://www.npmjs.com/package/timeweb-mcp-server)
- **MCP server (source):** [github.com/timeweb-cloud/mcp-server](https://github.com/timeweb-cloud/mcp-server)
- **Timeweb Cloud:** [timeweb.cloud](https://timeweb.cloud)
