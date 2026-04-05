# openclaw-vercel-skill

Teaches AI agents to deploy, manage, and configure projects on Vercel using the Vercel CLI.

## What It Does

This is a SKILL.md file (declarative, no code) that gives agents knowledge of Vercel CLI commands for:

- Deploying to production and preview environments
- Managing environment variables
- Configuring custom domains
- Rolling back deployments
- Viewing logs and deployment status

## Prerequisites

The user must authenticate via the Vercel CLI before the agent can use it:

```bash
npm i -g vercel
vercel login
```

## Install

### Finch

```bash
cp -r . ~/.finch/skills/vercel-cli/
finch gateway restart
```

### OpenClaw

```bash
cp -r . ~/.agents/skills/vercel-cli/
```

Or place in any skills directory your agent scans.

## Compatibility

- Finch (SKILL.md format with YAML frontmatter)
- OpenClaw (AgentSkills spec)
- Any agent platform that loads SKILL.md files

## License

MIT
