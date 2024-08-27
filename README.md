# TG_chatGPT

# Конфигурация

### Основные настройки

| KEY                       | Name                      | Default  | Description                               |
|---------------------------|---------------------------|----------|-------------------------------------------|
| LANGUAGE                  | Language                  | `en-us`  | Язык Приложения                           |
| CHAT_COMPLETE_API_TIMEOUT | Chat complete API timeout | `0`      | Таймаут API (секунды)                     |

### Конфигурация Telegram

| KEY                       | Name                           | Default                                    | Description                                                                                                   |
|---------------------------|--------------------------------|--------------------------------------------|---------------------------------------------------------------------------------------------------------------|
| TELEGRAM_API_DOMAIN       | Telegram API Domain            | `https://api.telegram.org/`                | Telegram API домен                                                                                            |
| TELEGRAM_AVAILABLE_TOKENS | Available Telegram tokens.     | `''`(array string)                         | Telegram Tokens разрешенные для доступа, разделенные запятыми при установке.                                  |
| DEFAULT_PARSE_MODE        | Default parsing mode.          | `Markdown`                                 | Default message parsing mode.                                                                                 |
| I_AM_A_GENEROUS_PERSON    | Allow everyone to use.         | `false`                                    | Доступ всем пользователям (осторожно!)                                                                        |
| CHAT_WHITE_LIST           | Chat whitelist                 | `''`(array string)                         | Белый список по Telegram ID                                                                                   |
| LOCK_USER_CONFIG_KEYS     | Locked user configuration key. | The default value is the URL for all APIs. | Ключ конфигурации для предотвращения утечки токенов в результате замены                                       |
| TELEGRAM_BOT_NAME         | Telegram bot name              | `''`(array string)                         | Имя бота, соответствующее токену Telegram, к которому разрешен доступ, при установке разделяется запятыми     |
| CHAT_GROUP_WHITE_LIST     | Group whitelist                | `''`(array string)                         | Белый список разрешенных идентификаторов групп                                                                |
| GROUP_CHAT_BOT_ENABLE     | Whether to enable group bots.  | `true`                                     | Включить групповых ботов                                                                                      |
| GROUP_CHAT_BOT_SHARE_MODE | Group robot sharing mode       | `true`                                     | После открытия люди в одной группе используют один и тот же контекст чата.                                    |

> ВАЖНО: Вы должны добавить ID группы в белый список `CHAT_GROUP_WHITE_LIST`, чтобы использовать ее, иначе любой может добавить вашего бота в группу и израсходовать вашу квоту.

> ВАЖНО: В связи с политикой конфиденциальности и безопасности Telegram, если ваша группа является публичной или имеет более 2000 участников, пожалуйста, установите для бота статус `administator`, иначе бот не будет отвечать на сообщения в чате с `@bot`.

> ВАЖНО: Вы должны установить `/setprivacy` на `Disable` в botfather, иначе бот не будет отвечать на сообщения с `@bot`.

### Конфигурация истории

| KEY                | Name                                  | Default | Description                                                                  |
|--------------------|---------------------------------------|---------|------------------------------------------------------------------------------|
| AUTO_TRIM_HISTORY  | Automatic trimming of message history | `true`  | Автоматически обрезать сообщения, чтобы избежать ограничения в 4096 символов |
| MAX_HISTORY_LENGTH | Maximum length of message history     | `20`    | Максимальное количество записей истории сообщений для хранения               |
| MAX_TOKEN_LENGTH   | Maximum token length                  | `20480` | Максимальная длина токена для истории сообщений                              |

### Конфигурация функций

| KEY                   | Name                    | Default            | Description                                                     |
|-----------------------|-------------------------|--------------------|-----------------------------------------------------------------|
| HIDE_COMMAND_BUTTONS  | Hide command buttons    | `''`(array string) | Необходимо повторно инициировать после изменения                |
| SHOW_REPLY_BUTTON     | Show quick reply button | `false`            | Отображать ли кнопку быстрого ответа                            |
| EXTRA_MESSAGE_CONTEXT | Extra message context   | `false`            | Ссылающееся сообщение также будет включено в контекст           |
| STREAM_MODE           | Stream mode             | `true`             | Режим печатной машинки                                          |
| SAFE_MODE             | Safe mode               | `true`             | Если включено, ID последнего сообщения будет сохранен           |
| DEBUG_MODE            | Debug mode              | `false`            | Если включено, будет сохранено последнее сообщение              |
| DEV_MODE              | Development mode        | `false`            | Если включено, будет отображаться больше отладочной информации  |

## Пользовательские настройки

Пользовательская конфигурация каждого пользователя может быть изменена только путем отправки сообщения через Telegram. Формат сообщения - `/setenv KEY=VALUE`. Пользовательские конфигурации имеют более высокий приоритет, чем системные. Если вы хотите удалить конфигурацию, используйте `/delenv KEY`. Для пакетной установки переменных используйте `/setenvs {«KEY1»: «VALUE1», «KEY2»: «VALUE2»}`.

### OpenAI

| KEY                     | Name                    | Default                     | 
|-------------------------|-------------------------|-----------------------------|
| OPENAI_API_KEY          | OpenAI API Key          | `''`(array string)          |
| OPENAI_CHAT_MODEL       | OpenAI Model            | `gpt-4o-mini`               |
| OPENAI_API_BASE         | OpenAI API BASE         | `https://api.openai.com/v1` |
| OPENAI_API_EXTRA_PARAMS | OpenAI API Extra Params | `{}`                        |
| DALL_E_MODEL            | DALL-E model name.      | `dall-e-2`                  |
| DALL_E_IMAGE_SIZE       | DALL-E Image size       | `512x512`                   |
| DALL_E_IMAGE_QUALITY    | DALL-E Image quality    | `standard`                  |
| DALL_E_IMAGE_STYLE      | DALL-E Image style      | `vivid`                     |

## Command

| Command    | Description                                                             | Example                                         |
|:-----------|:------------------------------------------------------------------------|:------------------------------------------------|
| `/help`    | Помощь                                                                  | `/help`                                         |
| `/new`     | Новая диалог                                                            | `/new`                                          |
| `/start`   | Получить ID и начать диалог                                             | `/start`                                        |
| `/img`     | Сгенирировать картинку                                                  | `/img Image Description`                        |
| `/version` | Текущая версия бота                                                     | `/version`                                      |
| `/setenv`  | Выставить пользовательскую конфигурацию в формате KEY=VALUE             | `/setenv KEY=VALUE`                             |
| `/setenvs` | Batch setting user configuration, see "User Configuration" for details. | `/setenvs {"KEY1": "VALUE1", "KEY2": "VALUE2"}` |
| `/delenv`  | Удалить пользовательскаую конфигурацию                                  | `/delenv KEY`                                   |
| `/system`  | Системная информация                                                    | `/system`                                       |
| `/redo`    | Изменить прошлый запрос                                                 | `/redo Modified content.` or `/redo`            |
