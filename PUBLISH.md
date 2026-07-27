# Publish guide (maintainers)

Standalone Agent Skill package. Push **this directory only** as its own public GitHub repo.

High-star skill repos ([vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills), [anthropics/skills](https://github.com/anthropics/skills)) nail three things:

1. One-line install above the fold (`npx skills add owner/repo`)
2. Multi-agent install paths
3. Public repo + `SKILL.md` at **root** → [skills.sh](https://skills.sh) via install telemetry (no registry form)

## Pre-flight

- [ ] No secrets, `.env`, tokens, customer data, personal absolute paths
- [ ] `pwd` is this repo root; `SKILL.md` is at root
- [ ] Not pushing a parent monorepo by mistake
- [ ] Git author name/email look human (not `you@MacBook-Pro.local`)
- [ ] Replace `karina-yjm` in README after the remote exists — or leave the placeholder until you know the username
- [ ] GitHub “Create repository”: Public, **no** auto README / license / gitignore

## Create + push

```bash
cd /path/to/which-skill

# optional: gh
# gh repo create which-skill --public --source=. --remote=origin --push

git remote add origin git@github.com:karina-yjm/which-skill.git
# or: https://github.com/karina-yjm/which-skill.git  (HTTPS needs a PAT, not password)

git branch -M main
git push -u origin main
```

## About box

| Field | Value |
|-------|--------|
| Description | `Intent-match installed agent skills — recommend-only, quote-backed, no autoload.` |
| Topics | `agent-skills`, `cursor`, `claude-code`, `codex`, `skill-router`, `llm-agents` |
| Issues | On (paraphrase misses = growth loop) |

## Post-push

```bash
npx skills add karina-yjm/which-skill -g
npx skills add karina-yjm/which-skill -g -a cursor -a claude-code -a codex
```

Share:

> Your agent has 100+ skills. Users don't speak trigger words.  
> **which-skill** — quote-backed, recommend-only.  
> `npx skills add karina-yjm/which-skill -g`

## Don't

- Don't bury or rename `SKILL.md`
- Don't add hardcoded domain→skill tables
- Don't claim autoload
- Don't force-push `main` after others may have cloned
