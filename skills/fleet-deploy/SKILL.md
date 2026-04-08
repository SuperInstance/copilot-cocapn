---
name: fleet-deploy
description: Deploy a new vessel to the Cocapn fleet — creates Cloudflare Worker, pushes to GitHub, runs health check
---

# Fleet Deploy Skill

Deploy a new vessel to the Cocapn fleet from your terminal.

## Prerequisites

- Node.js 18+ with `npx` available
- GitHub CLI (`gh`) authenticated, or GitHub PAT in environment
- Cloudflare Wrangler CLI (`npx wrangler`) with API token set

## Steps

1. **Create vessel directory**:
   ```bash
   mkdir -p /tmp/vessel-name/src
   cd /tmp/vessel-name
   ```

2. **Create worker.ts** following the standard template:
   - Dark `#0a0a0f` theme with accent color
   - Inter font from Google Fonts
   - CSP + X-Frame-Options headers
   - `/health` endpoint returning `{ status: "ok" }`
   - Fleet footer with Cocapn attribution
   - Double quotes in HTML only
   - Complete `export default { async fetch() {} }` block

3. **Create supporting files**:
   - `README.md` with description + fleet link + attribution
   - `.gitignore` containing `node_modules/`
   - `wrangler.toml` with `account_id = "049ff5e84ecf636b53b162cbb580aae6"`

4. **Initialize git and push**:
   ```bash
   git init && git add -A && git commit -m "vessel-name v0.1"
   git branch -M master
   git remote add origin https://github.com/Lucineer/vessel-name.git
   git push -u origin master
   ```

5. **Deploy to Cloudflare**:
   ```bash
   CLOUDFLARE_API_TOKEN="your-token" npx wrangler deploy
   ```

6. **Verify**:
   ```bash
   curl https://vessel-name.casey-digennaro.workers.dev/health
   # Expected: {"status":"ok"}
   ```

## Notes

- Zero npm dependencies — never run `npm install`
- Use `printf` not `echo` for wrangler.toml (trailing newline corruption)
- If build fails with unterminated string literal, hand-write a clean minimal worker
- GitHub repo creation may need API call if `gh` is not configured
