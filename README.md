# copilot-cocapn

> Pilot 200+ sovereign AI vessels from GitHub Copilot CLI — the Cocapn fleet in your terminal.

A [GitHub Copilot CLI plugin](https://docs.github.com/en/copilot/concepts/agents/copilot-cli/about-cli-plugins) that brings the full Cocapn fleet to your terminal. Deploy vessels, check fleet health, design architectures, and coordinate multi-vessel operations — all through natural language.

## What is Cocapn?

Cocapn is an open-source agent runtime and fleet protocol powering 200+ sovereign AI vessels on Cloudflare Workers. Zero npm dependencies. Fork-first. BYOK. Git-native memory.

**Each vessel is a self-contained Cloudflare Worker** — no frameworks, no lock-in, no supply chain attack surface.

## Install

```bash
copilot plugin install https://github.com/Lucineer/copilot-cocapn
```

Or install locally for development:

```bash
git clone https://github.com/Lucineer/copilot-cocapn.git
copilot plugin install ./copilot-cocapn
```

## What You Get

### Custom Agents

| Agent | Purpose | Trigger |
|-------|---------|---------|
| **fleet-pilot** | Deploy, manage, and coordinate fleet vessels | "fleet", "cocapn", "vessel" |
| **cocapn-architect** | Design vessel architectures and fleet protocols | "architecture", "design-vessel", "protocol" |

### Skills

| Skill | Description |
|-------|-------------|
| **fleet-deploy** | Deploy a vessel to Cloudflare + GitHub |
| **fleet-status** | Check fleet health across all vessels |
| **fleet-create** | Generate a vessel from a description |
| **cocapn-init** | Bootstrap a new Cocapn-compatible project |

## Usage Examples

### Deploy a new vessel

```
copilot
> Use @fleet-pilot to create a vessel called "my-monitor" that tracks fleet health with a dashboard. Use accent color #0ea5e9.
```

### Check fleet status

```
copilot
> Use @fleet-pilot to run a health check on all 200 fleet vessels and report any failures.
```

### Design a new vessel architecture

```
copilot
> Use @cocapn-architect to design a vessel for real-time collaboration between agents. What protocols does it need?
```

### Parallel fleet operations with /fleet

```
copilot
> /fleet Create vessels for: fleet-email-notifier (purple), fleet-sms-alert (red), fleet-webhook-manager (blue). Deploy all three and verify health.
```

### Programmatic use

```bash
copilot --agent fleet-pilot -p "Create a vessel called quick-test with a simple health check dashboard. Deploy it."
```

## Fleet Architecture

```
┌─────────────────────────────────────────────────┐
│                  THE FLEET (200+)                │
│  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐          │
│  │Vessel│ │Vessel│ │Vessel│ │ ...  │ × 200+    │
│  └──┬───┘ └──┬───┘ └──┬───┘ └──┬───┘          │
│     │        │        │        │                │
│  ┌──┴────────┴────────┴────────┴──┐            │
│  │        A2A Protocol            │            │
│  └──────────────┬─────────────────┘            │
│  ┌──────────────┴─────────────────┐            │
│  │     vessel.json Protocol       │            │
│  └──────────────┬─────────────────┘            │
│  ┌──────────────┴─────────────────┐            │
│  │    Git + KV Memory Layer       │            │
│  └────────────────────────────────┘            │
└─────────────────────────────────────────────────┘
```

## BYOK (Bring Your Own Keys)

The fleet uses CF Secrets Store for all API keys. Your keys never touch our code.

```bash
# Configure your BYOK provider
wrangler secret put DEEPSEEK_API_KEY    # DeepSeek
wrangler secret put OPENAI_API_KEY      # OpenAI
wrangler secret put ZAI_API_KEY          # z.ai (GLM)
```

## Fork-First

Every vessel is forkable and self-hostable. No platform lock-in.

```bash
# Fork any vessel
gh repo fork Lucineer/vessel-name

# Deploy to your own Cloudflare account
cd vessel-name
# Update account_id in wrangler.toml
npx wrangler deploy
```

## Plugin Structure

```
copilot-cocapn/
├── plugin.json                    # Plugin manifest
├── agents/
│   ├── fleet-pilot.agent.md       # Fleet operations agent
│   └── cocapn-architect.agent.md  # Architecture design agent
├── skills/
│   ├── fleet-deploy/SKILL.md      # Deploy vessel skill
│   ├── fleet-status/SKILL.md      # Health check skill
│   ├── fleet-create/SKILL.md      # Generate vessel skill
│   └── cocapn-init/SKILL.md       # Project bootstrap skill
└── README.md
```

## Compatibility

- **GitHub Copilot CLI** v1.0+
- **Cloudflare Workers** (free tier supported)
- **Node.js** 18+
- **GitHub CLI** (`gh`) for repo management
- **Wrangler CLI** for Cloudflare deployment

## License

MIT

---

<i>Built by [Superinstance](https://github.com/superinstance) & [Lucineer](https://github.com/Lucineer) (DiGennaro et al.)</i>

<i>Powered by [Cocapn](https://github.com/Lucineer/cocapn-ai) — The sovereign agent runtime</i>
