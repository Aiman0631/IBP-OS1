# IBP OS

Modern CRM / Lead Management dashboard for WhatsApp-driven sales.

## Current repository

This repository now contains the first production-style frontend shell for IBP OS. It is a static, Netlify-friendly UI with responsive navigation and dashboard views for:

- Dashboard
- Leads
- WhatsApp Inbox
- AI Copilot
- Analytics
- WhatsApp Connection
- Settings

The UI is intentionally built without fake production credentials. Live Supabase, Railway WhatsApp Web, and AI services should be connected through environment variables and backend endpoints.

## Deploy to Netlify

1. Import this GitHub repository into Netlify.
2. Build command: leave empty.
3. Publish directory: `.`
4. Deploy.

`netlify.toml` is already included.

## Frontend environment variables

When the real integrations are added, configure these in Netlify:

```text
VITE_SUPABASE_URL=
VITE_SUPABASE_ANON_KEY=
VITE_WHATSAPP_API_URL=
VITE_AI_API_URL=
```

Never put `SUPABASE_SERVICE_ROLE_KEY` in frontend code.

## Planned backend architecture

```text
Netlify
   ↓
IBP OS frontend
   ↓
Supabase PostgreSQL / Realtime
   ↓
Railway WhatsApp connector
   ↓
WhatsApp Web
```

The WhatsApp connector should use Node.js 22+ and `whatsapp-web.js`, with secrets stored only in Railway. Required connector routes are `/health`, `/qr`, `/send`, and `/logout`.

## Supabase data model

The intended production schema includes `users`, `leads`, `messages`, `conversations`, `notes`, `lead_activities`, and `ai_insights`, with foreign keys and indexes around lead/message/conversation relationships.

## Important

The visible dashboard is functional as a frontend prototype, but live CRM persistence and WhatsApp/AI integrations require their respective service credentials and backend deployment. The repository contains no mock WhatsApp production flow and no secret API keys.
