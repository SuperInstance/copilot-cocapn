---
name: fleet-status
description: Check health and status of Cocapn fleet vessels
---

# Fleet Status Skill

Check the health and operational status of vessels in the Cocapn fleet.

## Quick Health Check (Single Vessel)

```bash
curl -s https://vessel-name.casey-digennaro.workers.dev/health
```

Expected response: `{"status":"ok"}`

## Fleet-Wide Health Scan

```bash
# Scan all known vessels (serial to avoid OOM on constrained hosts)
for v in fleet-orchestrator-v2 fleet-analytics fleet-tls fleet-onboarding; do
  code=$(curl -s -o /dev/null -w "%{http_code}" --connect-timeout 3 \
    "https://${v}.casey-digennaro.workers.dev/health")
  if [ "$code" = "200" ]; then echo "✅ $v"; else echo "❌ $v ($code)"; fi
done
```

## GitHub Repo Status

```bash
# Check if a vessel repo exists and is healthy
gh repo view Lucineer/vessel-name --json name,description,url

# Check recent commits
gh api repos/Lucineer/vessel-name/commits --jq '.[0:3] | .[] | .commit.message'
```

## Cloudflare Worker Status

```bash
# List workers (requires CF API token)
CLOUDFLARE_API_TOKEN="your-token" npx wrangler deployments list --name vessel-name

# Check worker logs
CLOUDFLARE_API_TOKEN="your-token" npx wrangler tail vessel-name
```

## Fleet Metrics

Key metrics to report:
- **Vessel count**: 200+ deployed
- **Health rate**: Target 100% /health 200 responses
- **Average cold start**: Sub-200ms on Cloudflare Workers
- **Total deployments**: Track via GitHub commits per vessel
- **Repo state**: Check for uncommitted changes, stale branches
