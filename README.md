# openclaw-vercel-skill

Teaches AI agents to deploy, manage, and configure projects on Vercel using the Vercel CLI. No code, no API keys -- the agent uses CLI commands directly.

Compatible with [Finch](https://github.com/mattstvartak/finch-core), [OpenClaw](https://github.com/openclaw), and any agent platform that loads SKILL.md files.

## What This Skill Covers

| Area | Commands |
|------|----------|
| **Deployments** | Preview deploys, production deploys, deploy specific directories |
| **Environment Variables** | List, add, remove, pull to local .env |
| **Domains** | Add, remove, inspect DNS, configure custom domains |
| **Project Management** | Link projects, list deployments, inspect deployment details |
| **Rollback** | Promote previous deployments to production |
| **Logs** | View real-time deployment logs and build logs |

## Prerequisites

The user must install and authenticate the Vercel CLI before the agent can use it:

```bash
npm i -g vercel
vercel login
```

The agent does not need an API key. It runs `vercel` commands directly through the shell, using the user's authenticated session.

## Install

### Finch

```bash
git clone https://github.com/mattstvartak/openclaw-vercel-skill.git
cp -r openclaw-vercel-skill ~/.finch/skills/vercel-cli/
finch gateway restart
```

### OpenClaw

```bash
git clone https://github.com/mattstvartak/openclaw-vercel-skill.git
cp -r openclaw-vercel-skill ~/.agents/skills/vercel-cli/
```

Or place in any skills directory your agent scans.

## How It Works

This is a **SKILL.md file** (declarative, no code). It teaches the agent:

- The exact CLI commands for each Vercel operation
- Common workflows (deploy a Next.js app, fix a broken deploy, add a custom domain)
- Best practices (always preview before production, check status after deploying)
- Important gotchas (env vars require redeployment, DNS can take 48 hours)

The agent reads this skill and knows how to use the Vercel CLI. It runs commands via its shell execution tool.

## Skill Format

```yaml
---
name: vercel-cli
description: Deploy, manage, and configure projects on Vercel using the Vercel CLI...
---
```

The `description` field tells the agent when to load this skill. Any message about deploying, Vercel, environment variables, domains, or hosting will trigger it.

## What the Agent Can Do With This Skill

- Deploy your project to Vercel (preview and production)
- Manage environment variables without you touching the Vercel dashboard
- Add and configure custom domains
- Roll back to a previous deployment if something breaks
- Check deployment status and view logs
- Link a local project to a Vercel project

## What the Agent Cannot Do

- Create a Vercel account (you do this)
- Authenticate (you run `vercel login`)
- Access billing or team management
- Modify Vercel infrastructure settings

## License

MIT
