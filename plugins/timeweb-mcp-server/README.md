# Timeweb Cloud MCP Server — плагин для Cursor

Официальный плагин Cursor: подключает **Timeweb Cloud MCP Server**, чтобы управлять облачной инфраструктурой прямо из редактора.

## Что делает плагин

- Добавляет **Timeweb Cloud MCP Server** в Cursor в один клик (без ручного редактирования `mcp.json`).
- Использует npm-пакет [`timeweb-mcp-server`](https://www.npmjs.com/package/timeweb-mcp-server); плагин отвечает только за интеграцию с Cursor и маркетплейсом.

## Доступные MCP-инструменты

| Категория          | Инструменты                                                                                                    |
| ------------------ | -------------------------------------------------------------------------------------------------------------- |
| **Приложения**     | `create_timeweb_app` — создание и деплой приложений с автоопределением фреймворка и настроек                   |
| **VCS**            | `add_vcs_provider`, `get_vcs_providers`, `get_vcs_provider_repositories`, `get_vcs_provider_by_repository_url` |
| **Конфигурация**   | `get_allowed_presets`, `get_deploy_settings`                                                                   |
| **Инфраструктура** | `create_floating_ip`, `create_vpc`                                                                             |
| **Базы данных**    | `create_database`, `get_database_presets`                                                                      |
| **Промпты**        | `create_app_prompt`, `add_vcs_provider_prompt`                                                                 |

## Установка и настройка

1. Установите плагин из Cursor Marketplace.
2. Получите API-токен в [Timeweb Cloud](https://timeweb.cloud/my/api-keys).
3. При запросе (или в настройках MCP в Cursor) укажите `TIMEWEB_TOKEN` — ваш токен.
4. При необходимости перезапустите Cursor.

Плагин настраивает сервер так:

- **Command:** `npx`
- **Args:** `["timeweb-mcp-server"]`
- **Env:** `TIMEWEB_TOKEN` (ваш API-токен)

## Использование

В чате Cursor можно написать, например:

- _«Задеплой моё приложение в Timeweb Cloud»_
- _«Создай приложение в Timeweb из этого репо»_
- _«Добавь мой GitHub-репозиторий как VCS-провайдер в Timeweb»_

MCP-сервер по вашему проекту (фреймворк, репозиторий) создаст и задеплоит приложение в Timeweb Cloud.

## Важно

После создания приложения задайте переменные окружения в [панели Timeweb Cloud](https://timeweb.cloud); MCP-сервер не имеет доступа к локальному файлу `.env`.

## Ссылки

- **MCP-сервер (npm):** [timeweb-mcp-server](https://www.npmjs.com/package/timeweb-mcp-server)
- **MCP-сервер (исходники):** [github.com/timeweb-cloud/mcp-server](https://github.com/timeweb-cloud/mcp-server)
- **Timeweb Cloud:** [timeweb.cloud](https://timeweb.cloud)
