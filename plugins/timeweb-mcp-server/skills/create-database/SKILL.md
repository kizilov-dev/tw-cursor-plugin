---
name: create-database
description: Create a new database in Timeweb Cloud with the desired preset and parameters. Use when the user wants to create a DB in Timeweb.
---

# Create database in Timeweb Cloud

## When to use

- User asks to create a database in Timeweb Cloud
- User wants to add a database for their application
- User asks for available database presets or how to create a DB

## Instructions

1. Ensure **TIMEWEB_TOKEN** is set in Cursor MCP settings (API key from [Timeweb Cloud](https://timeweb.cloud/my/api-keys)).
2. Use **get_database_presets** to get the list of available database configuration presets (IDs and options).
3. Call **create_database** with the required parameters: preset id and any other fields required by the MCP server (e.g. name, region). Use the presets from step 2 to guide the user or choose a sensible default.
4. After creation, tell the user how to connect the app to the new database (connection string in Timeweb Cloud console, env vars, etc.).

## MCP tools

- `get_database_presets` — list available database presets
- `create_database` — create the database with the chosen preset and parameters
