---
name: fleet-create
description: Generate a new vessel from a description — uses AI to create the full worker.ts, README, and config
---

# Fleet Create Skill

Generate a complete new vessel from a natural language description.

## Usage

Tell the agent:
> "Create a vessel called `my-vessel` that does [description]. Use accent color #hex."

## What Gets Generated

1. **`src/worker.ts`** — Complete Cloudflare Worker with:
   - Inline HTML landing page (dark #0a0a0f theme, Inter font)
   - Feature cards describing capabilities
   - API endpoints section
   - CSP + X-Frame-Options security headers
   - `/health` endpoint
   - Fleet footer with attribution

2. **`README.md`** — Documentation with:
   - Vessel name and description
   - Fleet link
   - Cocapn attribution

3. **`.gitignore`** — `node_modules/`

4. **`wrangler.toml`** — With correct account_id

## Design Guidelines

- **Hero section**: Large title in accent color, subtitle in gray
- **Features grid**: 2-4 cards with colored left border
- **Endpoints list**: Monospace code blocks showing API routes
- **Footer**: Fleet link, Cocapn link, attribution
- **Responsive**: `auto-fit, minmax(250px, 1fr)` grid
- **Font**: Inter (weights 400, 500, 600, 700)
- **Background**: `#0a0a0f`, card bg: `#1e293b`, text: `#f8fafc`

## Quality Checklist

After generation, verify:
- [ ] Code ends with complete `export default { async fetch() {} };`
- [ ] No single quotes in HTML (double quotes only)
- [ ] CSP header includes `frame-ancestors 'none'`
- [ ] X-Frame-Options: DENY
- [ ] `/health` returns JSON with `status: "ok"`
- [ ] Content-Type: `text/html;charset=UTF-8`
- [ ] Fleet footer present
- [ ] No npm dependencies
- [ ] TypeScript (no `any` types if possible)
