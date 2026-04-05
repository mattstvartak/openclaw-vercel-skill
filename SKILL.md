---
name: vercel-cli
description: Deploy, manage, and configure projects on Vercel using the Vercel CLI. Use when deploying web apps, managing environment variables, configuring domains, checking deployment status, rolling back, or any Vercel-related task. The user has authenticated via the CLI -- Finch has direct access to the vercel command.
---

# Vercel CLI

Manage deployments, environment variables, domains, and projects via the `vercel` CLI. The user has already logged in -- you have full access.

## Deploying

```bash
# Deploy from current directory (production)
vercel --prod

# Preview deployment (not production)
vercel

# Deploy a specific directory
vercel ./dist --prod

# Deploy with a specific project name
vercel --prod --name my-project
```

Always confirm with the user before deploying to production. Preview deployments are safe to run freely.

## Environment Variables

```bash
# List all env vars
vercel env ls

# Add an env var (interactive -- specify target: production/preview/development)
vercel env add VARIABLE_NAME

# Add non-interactively
echo "value" | vercel env add VARIABLE_NAME production

# Remove an env var
vercel env rm VARIABLE_NAME production

# Pull env vars to local .env file
vercel env pull .env.local
```

After changing env vars, redeploy for changes to take effect.

## Domains

```bash
# List domains
vercel domains ls

# Add a domain to current project
vercel domains add example.com

# Remove a domain
vercel domains rm example.com

# Inspect domain DNS
vercel domains inspect example.com
```

## Project Management

```bash
# Link current directory to a Vercel project
vercel link

# List recent deployments
vercel ls

# Inspect a specific deployment
vercel inspect <deployment-url>

# View project settings
vercel project ls
```

## Rollback

```bash
# Promote a previous deployment to production
vercel promote <deployment-url>

# List deployments to find the one to roll back to
vercel ls
```

Always list deployments first to identify the correct one before promoting.

## Logs

```bash
# View deployment logs (real-time)
vercel logs <deployment-url>

# View build logs
vercel logs <deployment-url> --build
```

## Common Workflows

**Deploy a Next.js app:**
1. `vercel link` (first time only)
2. `vercel env pull .env.local` (get env vars)
3. Make changes, test locally
4. `vercel` (preview deploy)
5. Verify preview URL works
6. `vercel --prod` (production deploy)

**Fix a broken production deploy:**
1. `vercel ls` (find last working deployment)
2. `vercel promote <working-deployment-url>`
3. Fix the issue locally
4. `vercel` (preview), verify, then `vercel --prod`

**Add a custom domain:**
1. `vercel domains add yourdomain.com`
2. Follow DNS configuration instructions
3. Wait for DNS propagation (can take up to 48 hours)
4. `vercel domains inspect yourdomain.com` to verify

## Important

- Always preview before production deploys
- Check `vercel ls` after deploying to confirm status
- Environment variables require redeployment to take effect
- Use `vercel --help` or `vercel <command> --help` for full flag reference
