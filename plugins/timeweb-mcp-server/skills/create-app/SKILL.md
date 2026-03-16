---
name: create-app
description: Create and deploy an application in Timeweb Cloud from the current project or a Git repo. Use when the user wants to deploy an app, create a new app in Timeweb, or connect a repository for deployment.
---

# Create app in Timeweb Cloud

## When to use

- User asks to deploy an app to Timeweb Cloud
- User wants to create a new application from the current project
- User wants to connect a Git repository to Timeweb for deployment

## Instructions

1. Ensure **TIMEWEB_TOKEN** is set in Cursor MCP settings (user needs an API key from [Timeweb Cloud](https://timeweb.cloud/my/api-keys)).
2. If the repo is not yet connected: use **add_vcs_provider** (or **add_vcs_provider_prompt**) to add the Git repository; for private repos, ask the user for login and token/password if auth fails.
3. Use **get_vcs_provider_by_repository_url** with the repo URL to find the provider, or **get_vcs_providers** to list existing ones.
4. Use **get_allowed_presets** and **get_deploy_settings** to choose a preset and deploy settings for the app (framework is often auto-detected from the project).
5. Call **create_timeweb_app** with: provider_id, repository_id, repository_url, preset_id, framework, commit_sha, branch_name, name, build_cmd, run_cmd, envs, and other required fields. Get commit_sha from the repo (e.g. current commit), branch_name from the user or current branch.
6. After creation, remind the user to set environment variables in the [Timeweb Cloud](https://timeweb.cloud/my); the MCP server cannot read the project's `.env`.

## MCP tools

- `create_timeweb_app` — create the app
- `add_vcs_provider`, `get_vcs_providers`, `get_vcs_provider_repositories`, `get_vcs_provider_by_repository_url` — VCS
- `get_allowed_presets`, `get_deploy_settings` — presets and framework settings
