---
name: deploy-staging
description: Deploy the current project to Timeweb Cloud (staging or default environment) using MCP tools.
---

# Deploy to Timeweb Cloud

1. Ensure TIMEWEB_TOKEN is set and the Timeweb MCP server is enabled in Cursor.
2. Run project validation and tests if applicable.
3. Use MCP tools: e.g. add VCS provider if needed, then create or update the app with `create_timeweb_app` (or follow create_app_prompt).
4. After deploy, remind the user to set environment variables in the Timeweb Cloud console.
5. Run smoke checks and report status.
