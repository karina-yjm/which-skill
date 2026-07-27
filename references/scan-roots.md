# Skill scan roots

Used when the in-session skill catalog is missing, thin, or stale. Read each `SKILL.md` **frontmatter only** (`name`, `description`). Follow symlinks; **skip broken links**; optionally report `reachable / broken`.

## Global (user-level)

| Agent family | Path |
|--------------|------|
| Cursor | `~/.cursor/skills/` |
| Claude Code | `~/.claude/skills/` |
| Codex | `~/.codex/skills/` |
| GitHub Copilot | `~/.copilot/skills/` |
| Gemini CLI | `~/.gemini/skills/` |
| Trae | `~/.trae/skills/` · `~/.trae-cn/skills/` |
| OpenCode | `~/.config/opencode/skills/` |
| Universal / Amp | `~/.agents/skills/` · `~/.config/agents/skills/` |
| Windsurf | `~/.codeium/windsurf/skills/` |

## Project-level

| Path | Notes |
|------|-------|
| `.agents/skills/` | Common fallback (Cursor, Codex, Copilot, Gemini, OpenCode, …) |
| `.claude/skills/` | Claude Code |
| `.cursor/skills/` | Cursor (legacy / project) |
| `.trae/skills/` | Trae |
| `.windsurf/skills/` | Windsurf |

Skip `which-skill` and deprecated `skill-router` stubs when ranking.
