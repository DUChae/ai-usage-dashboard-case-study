# AI Usage Dashboard

Case study for a Redis-backed AI usage dashboard that aggregates usage and cost data from OpenAI, Gemini, Cursor, ChatGPT Web, and Figma.

This repository is sanitized for public portfolio use. It does not include company source code, private endpoints, or secrets.

## What This Project Does

- Syncs browser-captured session state through a Chrome Extension
- Resolves session data through Redis-first lookup
- Normalizes provider-specific usage payloads into a shared response model
- Renders aggregate and per-service usage, cost, and trend views

## Architecture

```text
Chrome Extension
  -> /api/session-sync
  -> Next.js API
  -> Upstash Redis
  -> Provider fetchers
  -> Dashboard UI
```

## Tech Stack

- Next.js 16
- React 19
- TypeScript
- Tailwind CSS
- Recharts
- Zod
- Upstash Redis
- Vercel
- Chrome Extension
- Plasmo

## Implementation Notes

- `app/api/session-sync/route.ts` receives extension payloads and writes session data to Redis after validation.
- Provider fetchers resolve stored session state before falling back to environment-based configuration.
- The dashboard uses shared types for service status, token counts, request counts, and cost metrics.
- Figma receives a dedicated project/file breakdown view for recent activity.

## Repository Contents

- Public case-study README
- Project outcome and resume templates
- Portfolio and Git README templates
- Capture / diagram checklist

## Screenshots and Diagrams

See [portfolio-assets.md](./portfolio-assets.md) for the recommended capture order.

Suggested screenshot set:

- Dashboard overview
- Service detail view
- Extension popup
- Session sync success state

Suggested diagram set:

- Browser capture to Redis sync flow
- Usage normalization flow
- Dashboard rendering flow
- High-level deployment flow

## Local Setup

```bash
corepack pnpm install
cp .env.example .env.local
corepack pnpm dev
```

## Chrome Extension Build

```bash
cd extension/ai-auto
npm run build
```

## Public Portfolio Notes

- Use screenshots only for non-sensitive screens
- Keep architecture diagrams high level
- Avoid internal hostnames, private keys, and company identifiers
