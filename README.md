# IBP OS

IBP OS is a clean CRM / lead-management dashboard designed for WhatsApp-driven sales.

## What is already included

- Dashboard with KPI cards
- Lead activity and lead status views
- Recent leads table
- WhatsApp Inbox UI
- AI Copilot UI
- Analytics UI
- WhatsApp Connection screen
- Settings screen
- Responsive desktop / tablet / mobile layout
- Netlify configuration
- No production secrets committed to GitHub

## Important: no coding is required from the owner

The project is intentionally a static frontend at this stage. You do **not** need to write code in VS Code to use the current dashboard.

The remaining production integrations are:

1. Supabase Auth + PostgreSQL + Realtime
2. Real lead CRUD
3. Railway WhatsApp connector
4. WhatsApp QR connection and messaging
5. AI lead analysis / suggested replies
6. Netlify deployment

These integrations require the relevant service accounts and permissions. Secrets must stay outside the public frontend.

## Current Netlify settings

Because the current dashboard is a static HTML/CSS/JavaScript app:

- Build command: leave empty
- Publish directory: `.`
- `netlify.toml` is already included

## Security

Never put a Supabase service-role key, WhatsApp session secret, or AI provider secret inside `index.html` or any public frontend file.

## Planned architecture

```text
Netlify
   ↓
IBP OS frontend
   ↓
Supabase Auth / PostgreSQL / Realtime
   ↓
Railway WhatsApp connector
   ↓
WhatsApp Web
```

The WhatsApp connector will use Node.js 22+ and `whatsapp-web.js`, with private credentials stored only on the backend.
