# 🟧 MOBAREZAN — OPENWEBUI RAILWAY

## OPENWEBUI INSTALLER SERVER

نسخه مخصوص Deploy مستقیم Open WebUI روی Railway با Docker.

### نصب

Repository را به GitHub بفرست و سپس در Railway:

```text
New Project
↓
Deploy from GitHub Repo
↓
انتخاب Repository
↓
Deploy
```

ساختار Repository:

```text
MOBAREZAN-OPENWEBUI-RAILWAY/
├── Dockerfile
├── railway.toml
├── .env.example
├── README.md
├── .gitignore
└── LICENSE
```

Docker Image:

```text
ghcr.io/open-webui/open-webui:main
```

پورت:

```text
8080
```

### PostgreSQL

در همان Project یک PostgreSQL Service بساز و در Variables سرویس Open WebUI قرار بده:

```env
DATABASE_URL=${{Postgres.DATABASE_URL}}
```

### Redis

یک Redis Service بساز:

```env
REDIS_URL=${{Redis.REDIS_URL}}
WEBSOCKET_REDIS_URL=${{Redis.REDIS_URL}}
```

### Variables

```env
WEBUI_AUTH=True
ENABLE_SIGNUP=True
ENABLE_OLLAMA_API=False
ENABLE_WEBSOCKET_SUPPORT=True
WEBSOCKET_MANAGER=redis
DATA_DIR=/app/backend/data
```

### Secretها

در Railway این دو Secret را بساز:

```text
WEBUI_SECRET_KEY
OAUTH_SESSION_TOKEN_ENCRYPTION_KEY
```

مقدار Secretها را با Generate Secret خود Railway تولید کن و داخل GitHub قرار نده.

### Volume

برای Open WebUI یک Volume با Mount Path زیر بساز:

```text
/app/backend/data
```

### Domain

بعد از Deploy:

```text
Open WebUI
↓
Settings
↓
Networking
↓
Generate Domain
```

### آپدیت

```bash
git add .
git commit -m "Update Open WebUI"
git push
```

> این نسخه برای Deploy مستقیم یک Open WebUI Service روی Railway آماده شده است. برای ساخت همزمان Open WebUI + PostgreSQL + Redis با یک کلیک، باید Project نهایی Railway به Template تبدیل شود.

# 🟧 MOBAREZAN

## OPENWEBUI INSTALLER SERVER

Dockerized • Railway Ready • GitHub Ready
