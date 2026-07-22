# 🚀 Setup Guide

Инструкции по импорту и запуску воркфлоу.

## Требования

- **n8n** ≥ 1.0 (self-hosted или Cloud)
- Для Make-воркфлоу: аккаунт **Make** (make.com)

## Общие шаги для n8n

1. **Скопируйте JSON** нужного воркфлоу из `workflows/n8n/`
2. В n8n: **Import from File** (или Ctrl+O → Paste JSON)
3. Настройте **Credentials** (см. таблицу ниже)
4. Активируйте workflow

## Необходимые Credentials по проектам

| Проект | Credentials |
|---|---|
| **Telegram + МойСклад (CV)** | Telegram Bot Token, МойСклад API token |
| **RAG AI Agent** | OpenAI API key, Google Drive OAuth, Pinecone/Qdrant API key |
| **TG Travel Consultant** | Telegram Bot Token, OpenRouter API key, PostgreSQL |
| **SWOT Analysis (Make)** | Make Google Drive connection, OpenAI/Anthropic |
| **AI Sales Manager** | Локальный llama.cpp сервер, Telegram Bot Token |
| **AI Product Descriptions** | Telegram Bot Token, LLM API key |
| **Candidate Examination** | Slack Bot Token, Database (PostgreSQL) |
| **Google Calendar Assistant** | Telegram Bot Token, Google Calendar OAuth |
| **RAG + ngrok** | ngrok auth token, OpenAI API key, Vector DB |

## Переменные окружения

Создайте `.env` или настройте в n8n:

```env
# API Keys
OPENAI_API_KEY=sk-...
OPENROUTER_API_KEY=sk-or-...

# Telegram
TELEGRAM_BOT_TOKEN=123456:ABC...

# МойСклад
MOYSKLAD_TOKEN=...
MOYSKLAD_ORG_ID=...

# Database
PG_HOST=localhost
PG_PORT=5432
PG_USER=n8n
PG_PASSWORD=...
PG_DB=n8n

# ngrok
NGROK_AUTH_TOKEN=...
```

## Self-hosted LLM (для AI Sales Manager)

Запуск llama.cpp сервера:

```bash
docker run -p 1234:1234 ghcr.io/ggerganov/llama.cpp:server \
  -m /models/model.gguf \
  --host 0.0.00 --port 1234
```

## Импорт Make blueprint

1. В Make: **Create a new scenario**
2. Три точки → **Import Blueprint**
3. Выберите `workflows/make/swot-call-analysis.json`
4. Переподключите Google Drive connection
