# Timeweb Cloud MCP Server — плагин для Cursor

[![Cursor Marketplace](https://img.shields.io/badge/Cursor-Marketplace-6d28d9)](https://cursor.com/marketplace)
[![npm version](https://img.shields.io/npm/v/timeweb-mcp-server)](https://www.npmjs.com/package/timeweb-mcp-server)

Официальный плагин для Cursor Marketplace: подключает **Timeweb Cloud MCP Server** и позволяет управлять инфраструктурой [Timeweb Cloud](https://timeweb.cloud) прямо из редактора.

## Что даёт плагин

- **Установка в один клик** — ставится из Cursor Marketplace, MCP-сервер подключается без ручного правления `mcp.json`.
- **Деплой из Cursor** — создание приложений и баз данных через MCP-инструменты.
- **Обычные фразы в чате** — например: _«Задеплой моё приложение в Timeweb Cloud»_ или _«Создай приложение из этого репо»_.

## Быстрый старт

1. Установите плагин из **Cursor Marketplace** (или добавьте этот репозиторий как источник плагинов).
2. Получите API-токен: [Timeweb Cloud → API-ключи](https://timeweb.cloud/my/api-keys).
3. В настройках MCP в Cursor укажите **TIMEWEB_TOKEN** — ваш токен (плагин запускает `npx timeweb-mcp-server` с этой переменной).
4. Перезапустите Cursor и пользуйтесь MCP-инструментами или чатом.

## MCP-инструменты (из timeweb-mcp-server)

| Категория      | Инструменты                                                                                                    |
| -------------- | -------------------------------------------------------------------------------------------------------------- |
| Приложения     | `create_timeweb_app`                                                                                           |
| VCS            | `add_vcs_provider`, `get_vcs_providers`, `get_vcs_provider_repositories`, `get_vcs_provider_by_repository_url` |
| Конфигурация   | `get_allowed_presets`, `get_deploy_settings`                                                                   |
| Инфраструктура | `create_floating_ip`, `create_vpc`                                                                             |
| Базы данных    | `create_database`, `get_database_presets`                                                                      |
| Промпты        | `create_app_prompt`, `add_vcs_provider_prompt`                                                                 |

Полный список и описание: [github.com/timeweb-cloud/mcp-server](https://github.com/timeweb-cloud/mcp-server).

## Важно

После создания приложения задайте переменные окружения в [панели Timeweb Cloud](https://timeweb.cloud/my) — MCP-сервер не имеет доступа к вашему локальному `.env`.

## Структура репозитория

Этот репозиторий — **обёртка для Cursor Marketplace** вокруг Timeweb MCP Server:

- **Описание плагина:** `plugins/timeweb-mcp-server/` (манифест, конфиг MCP, rules, skills, agents, commands).
- **MCP-сервер (рантайм):** npm-пакет [timeweb-mcp-server](https://www.npmjs.com/package/timeweb-mcp-server), исходники: [timeweb-cloud/mcp-server](https://github.com/timeweb-cloud/mcp-server).

## Проверка плагина локально

Перед отправкой в маркетплейс можно убедиться, что всё работает.

### 1. Валидация сборки плагина

Из корня репозитория:

```bash
node scripts/validate-template.mjs
```

В конце должно быть сообщение **Validation passed.**

### 2. Проверка MCP-сервера (то, что устанавливает плагин)

Плагин только настраивает **Timeweb MCP Server** в Cursor. Эту часть можно проверить вручную:

1. **Получите API-токен** в [Timeweb Cloud → API-ключи](https://timeweb.cloud/my/api-keys).
2. **Добавьте сервер вручную** в Cursor:
   - Откройте **Настройки** (например, `Ctrl+,` / `Cmd+,`) → **Features** → **Model Context Protocol**.
   - Добавьте новый MCP-сервер:
     - **Name:** `timeweb-mcp-server`
     - **Command:** `npx`
     - **Arguments:** `timeweb-mcp-server`
     - **Env:** `TIMEWEB_TOKEN` = ваш токен
3. **Перезапустите Cursor** (или обновите список MCP).
4. В любом чате проверьте, что доступны инструменты Timeweb (например, `get_vcs_providers`, `get_allowed_presets`) и они отвечают.

Если так всё работает, после установки из маркетплейса поведение будет таким же — плагин только подставляет этот MCP-конфиг.

### 3. Проверка плагина целиком (по желанию)

- **Тариф Team:** добавьте этот репозиторий как [Team marketplace](https://cursor.com/docs/plugins#add-a-team-marketplace) (Dashboard → Settings → Plugins → Add marketplace → вставьте URL репо). Установите плагин из этого маркетплейса и убедитесь, что подтягиваются rules, skills и MCP.
- **Без Team:** откройте этот репо в Cursor и выполните `node scripts/validate-template.mjs`. Для проверки основной функциональности достаточно ручной проверки MCP-сервера (п. 2 выше).

## Чеклист для отправки (для команды Cursor)

- [x] Корректные `.cursor-plugin/plugin.json` и `.cursor-plugin/marketplace.json`.
- [x] Имя плагина `timeweb-mcp-server` уникально, в нижнем регистре, kebab-case.
- [x] В маркетплейсе указана папка плагина в `plugins/`.
- [x] Во всех rule, skill, agent и command есть фронтматтер.
- [x] Логотип в `plugins/timeweb-mcp-server/assets/logo.svg` и указан в манифесте плагина.
- [x] `node scripts/validate-template.mjs` завершается успешно.

## Отправка в Cursor Marketplace

Когда репозиторий готов (например, на GitHub):

1. Запустите `node scripts/validate-template.mjs` и исправьте ошибки, если появятся.
2. Отправьте **ссылку на репозиторий** команде Cursor (Slack или **kniparko@anysphere.com**) для добавления плагина в маркетплейс.

## Лицензия

MIT
