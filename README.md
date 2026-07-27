# which-skill

> Your agent has 100+ skills.  
> Users don't speak trigger words.

**which-skill** matches what people *actually say* to skills you **already installed**, then recommends **2–3** options — each backed by a **verbatim quote** from that skill's `description`. It never silently autoloads anything.

[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-compatible-0a7ea4.svg)](https://agentskills.io/)
[![skills.sh](https://img.shields.io/badge/skills.sh-install-black.svg)](https://skills.sh)

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="docs/assets/hero.svg">
  <img src="docs/assets/hero.svg" alt="which-skill matches intent, not keywords — quote-backed recommendations from installed skills" width="100%">
</picture>

```text
You:  "Is my page friendly to color-blind users?"

Keyword trigger:  ✗  (skill only listens for "audit a11y")
which-skill:      ✓  accessibility-review
                  Quote: "…"  ← from that skill's description
                  (recommend-only — waits for your OK)
```

**中文：** 你这话没对上触发词也没关系。我会从你「已安装」的 skills 里按意图推荐 2–3 个，并且每个推荐都会引用 description 的原句；绝不在你没确认前偷偷加载别的 skill。

## Install

```bash
npx skills add karina-yjm/which-skill -g
```

Target agents (Cursor / Claude Code / Codex / …):

```bash
npx skills add karina-yjm/which-skill -g -a cursor -a claude-code -a codex
npx skills add karina-yjm/which-skill -g -a opencode -a github-copilot -a gemini-cli -a trae
```

Project install (share with the team via git):

```bash
npx skills add karina-yjm/which-skill
```

Compatible with the [Agent Skills](https://agentskills.io/) format and [70+ agents](https://github.com/vercel-labs/skills#supported-agents) via the Skills CLI. First install helps listing on [skills.sh](https://skills.sh).

<details>
<summary><strong>Manual install paths</strong> (Claude · Codex · Cursor · …)</summary>

Copy this folder so the path ends with `which-skill/SKILL.md`.

| Agent | Global | Project |
|-------|--------|---------|
| Cursor | `~/.cursor/skills/which-skill/` | `.agents/skills/which-skill/` |
| Claude Code | `~/.claude/skills/which-skill/` | `.claude/skills/which-skill/` |
| Codex | `~/.codex/skills/which-skill/` | `.agents/skills/which-skill/` |
| OpenCode | `~/.config/opencode/skills/which-skill/` | `.agents/skills/which-skill/` |
| GitHub Copilot | `~/.copilot/skills/which-skill/` | `.agents/skills/which-skill/` |
| Gemini CLI | `~/.gemini/skills/which-skill/` | `.agents/skills/which-skill/` |
| Trae | `~/.trae/skills/which-skill/` | `.trae/skills/which-skill/` |
| Windsurf | `~/.codeium/windsurf/skills/which-skill/` | `.windsurf/skills/which-skill/` |

```bash
cp -R which-skill ~/.claude/skills/which-skill   # Claude Code
cp -R which-skill ~/.codex/skills/which-skill    # Codex
cp -R which-skill ~/.cursor/skills/which-skill   # Cursor
```

Full scan roots used by the skill: [references/scan-roots.md](references/scan-roots.md).

</details>

## Try it

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="docs/assets/example.svg">
  <img src="docs/assets/example.svg" alt="Example prompts in English and Chinese with quote-backed skill recommendations" width="100%">
</picture>

```text
which skill should I use — my landing page looks like every other AI template?
帮我选 skill：网页对色盲友好吗？
run which-skill paraphrase cases
```

More transcripts → [examples.md](examples.md)

## Why this exists

Skill triggers are **keyword lists**. Same job, different words → miss:

| You say | Skill only listens for |
|---------|------------------------|
| color-blind friendly? | `audit accessibility`, `a11y` |
| reads like ChatGPT | `humanize`, `de-AI` |
| idea isn't ready — don't code | `grill`, `brainstorm` |

That's not one broken skill — it's how keyword triggers work. **which-skill** matches by **intent** against your **live** installed catalog.

## Three hard rules

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="docs/assets/rules.svg">
  <img src="docs/assets/rules.svg" alt="Recommend-only, quote-backed, live catalog" width="100%">
</picture>

| Rule | Promise |
|------|---------|
| **Recommend-only** | Never autoload. You confirm. |
| **Quote-backed** | No quote from `description` → no recommend. |
| **Live catalog** | Scan installs *now*. No rotting domain→skill tables. |

Also: **negative space** (sometimes no skill), **altitude** (atomic / combo / flow), and **description feedback** when a skill should have matched but its triggers are too narrow.

## Paraphrase harness

Shipped eval set: [references/paraphrase-cases.md](references/paraphrase-cases.md) — bilingual prompts that share **zero tokens** with common triggers.

| Result | Meaning |
|--------|---------|
| `hit` | Right family + quote-backed |
| `miss` | Wrong or empty |
| `skipped-not-installed` | Expected skill not in *your* catalog |

Easiest PR: add a real miss. See [CONTRIBUTING.md](CONTRIBUTING.md).

## vs other tools

| | **which-skill** | Typical skill-router | `find-skills` |
|--|-----------------|----------------------|---------------|
| Source | Live installed descriptions | Fixed routing table | skills.sh |
| On match | Recommend + wait | Often autoload | Install new |
| Proof | Must quote description | Optional | — |
| Eval harness | Yes | Rare | — |

- Use **which-skill** when you already have too many skills and phrasing drifts.  
- Use **find-skills** when nothing local fits and you want to install something new.

## Agent contract

The runnable instructions are in [`SKILL.md`](SKILL.md). Keep it lean; long lists live under `references/`.

## License

MIT © karina-yjm — [LICENSE](LICENSE)

---

Maintainer publish notes (first GitHub upload): [PUBLISH.md](PUBLISH.md)
