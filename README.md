# Copilot Cocapn

> GitHub Copilot CLI plugin for Cocapn. Custom agents, fleet skills, BYOK model routing.

Bring the Cocapn fleet into your terminal via GitHub Copilot CLI.

## Features

- 2 custom agents: Cocapn Architect (system design) and Fleet Pilot (deployment)
- 4 skills: cocapn-init, fleet-create, fleet-deploy, fleet-status
- BYOK model routing — per-agent model selection via YAML frontmatter

## Install

```bash
copilot plugin install Lucineer/copilot-cocapn
```

## Agents

**Cocapn Architect** — Designs agent systems, suggests vessel compositions, generates cocapn.yaml configs.

**Fleet Pilot** — Manages fleet operations: deploy vessels, check health, coordinate multi-vessel tasks.

## Skills

- `cocapn-init` — Initialize a new Cocapn project in current directory
- `fleet-create` — Generate a new vessel from a template
- `fleet-deploy` — Deploy vessels to Cloudflare Workers
- `fleet-status` — Check health of all fleet vessels

## BYOK Model Config

Set per-agent models in YAML frontmatter:

```yaml
---
name: my-agent
model: deepseek-chat
---
```

## Ecosystem

- [Deckboss](https://github.com/Lucineer/deckboss) — Build-phase AI assistant
- [Cocapn](https://github.com/Lucineer/cocapn-ai) — Agent runtime
- [The Fleet](https://github.com/Lucineer/the-fleet) — 200+ vessels

## License

MIT — Built by [Superinstance](https://github.com/superinstance) and [Lucineer](https://github.com/Lucineer) (DiGennaro et al.)
