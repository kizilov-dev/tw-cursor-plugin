# Timeweb Cloud MCP Server — Cursor Plugin

[![Cursor Marketplace](https://img.shields.io/badge/Cursor-Marketplace-6d28d9)](https://cursor.com/marketplace)
[![npm version](https://img.shields.io/npm/v/timeweb-mcp-server)](https://www.npmjs.com/package/timeweb-mcp-server)

Official Cursor Marketplace plugin that adds the **Timeweb Cloud MCP Server** to Cursor so you can manage [Timeweb Cloud](https://timeweb.cloud) infrastructure from the editor.

## What you get

- **One-click setup** — install from Cursor Marketplace; the plugin registers the MCP server (no manual `mcp.json` editing).
- **Deploy from Cursor** — create apps, add VCS providers, create databases, floating IPs, and VPCs via MCP tools.
- **Natural language** — e.g. _"Deploy my app to Timeweb Cloud"_ or _"Create an app from this repo"_ in Cursor chat.

## Quick start

1. Install the plugin from **Cursor Marketplace** (or add this repo as a plugin source).
2. Get an API token: [Timeweb Cloud → API keys](https://timeweb.cloud/my/api-keys).
3. In Cursor MCP settings, set **TIMEWEB_TOKEN** to your token (the plugin uses `npx timeweb-mcp-server` with this env var).
4. Restart Cursor and use the MCP tools or chat.

## MCP tools (from timeweb-mcp-server)

| Category       | Tools                                                                                                          |
| -------------- | -------------------------------------------------------------------------------------------------------------- |
| Apps           | `create_timeweb_app`                                                                                           |
| VCS            | `add_vcs_provider`, `get_vcs_providers`, `get_vcs_provider_repositories`, `get_vcs_provider_by_repository_url` |
| Config         | `get_allowed_presets`, `get_deploy_settings`                                                                   |
| Infrastructure | `create_floating_ip`, `create_vpc`                                                                             |
| Databases      | `create_database`, `get_database_presets`                                                                      |
| Prompts        | `create_app_prompt`, `add_vcs_provider_prompt`                                                                 |

Full list and details: [github.com/timeweb-cloud/mcp-server](https://github.com/timeweb-cloud/mcp-server).

## Important

After creating an app, set environment variables in the [Timeweb Cloud console](https://timeweb.cloud); the MCP server cannot read your local `.env`.

## Repository structure

This repo is the **Cursor Marketplace wrapper** for the Timeweb MCP server:

- **Plugin definition:** `plugins/timeweb-mcp-server/` (manifest, MCP config, rules, skills, agents, commands).
- **MCP server (runtime):** npm package [timeweb-mcp-server](https://www.npmjs.com/package/timeweb-mcp-server), source: [timeweb-cloud/mcp-server](https://github.com/timeweb-cloud/mcp-server).

## Submission checklist (for Cursor team)

- [x] Valid `.cursor-plugin/plugin.json` and `.cursor-plugin/marketplace.json`.
- [x] Plugin name `timeweb-mcp-server` is unique, lowercase, kebab-case.
- [x] Marketplace entry points to plugin folder under `plugins/`.
- [x] Frontmatter present in all rule, skill, agent, and command files.
- [x] Logo at `plugins/timeweb-mcp-server/assets/logo.svg` and referenced in plugin manifest.
- [x] `node scripts/validate-template.mjs` passes.

## Submitting to Cursor Marketplace

When the repo is ready (e.g. on GitHub):

1. Run `node scripts/validate-template.mjs` and fix any errors.
2. Send the **repository link** to the Cursor team via [Slack](https://cursor.com) or **kniparko@anysphere.com** for adding the plugin to the Marketplace.

## License

MIT
