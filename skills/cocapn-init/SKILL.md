---
name: cocapn-init
description: Initialize a new Cocapn-compatible project with standard structure, configs, and fleet integration
---

# Cocapn Init Skill

Bootstrap a new Cocapn-compatible vessel project from scratch.

## Quick Start

```bash
copilot --agent fleet-pilot -p "Create a new vessel called my-vessel following the Cocapn fleet standard template"
```

## Standard Project Structure

```
my-vessel/
├── src/
│   └── worker.ts      # Main Cloudflare Worker (inline HTML)
├── README.md           # Documentation
├── .gitignore          # node_modules/
├── wrangler.toml       # CF Worker config
└── package.json        # Optional (for types only, no deps)
```

## wrangler.toml Template

```toml
name = "my-vessel"
main = "src/worker.ts"
compatibility_date = "2024-01-01"
account_id = "049ff5e84ecf636b53b162cbb580aae6"
```

## Git Init + Push

```bash
git init
git add -A
git commit -m "my-vessel v0.1"
git branch -M master
git remote add origin https://github.com/Lucineer/my-vessel.git
git push -u origin master
```

## Deploy

```bash
CLOUDFLARE_API_TOKEN="your-token" npx wrangler deploy
```

## Verify

```bash
curl https://my-vessel.casey-digennaro.workers.dev/health
```

## Notes

- Always use `master` branch (not `main`) for fleet vessels
- Never use `echo` for wrangler.toml — trailing newline corrupts TOML
- GitHub PAT needs `repo` scope for push, `public_repo` for visibility
- CF token needs `Workers Scripts:Edit` permission
