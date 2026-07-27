# Contributing

Highest-value contribution: a **paraphrase miss** — real user wording that should have hit a skill but didn't.

## Add a paraphrase case

1. Open [references/paraphrase-cases.md](references/paraphrase-cases.md).
2. Add a row: user phrasing (avoid the skill's trigger words) → expected skill family.
3. Prefer **zero token overlap** with that skill's published `description` triggers.
4. Bilingual (EN / 中文) is ideal; one language is fine.
5. PR title: `case: <short intent> → <skill-family>`

## Change the agent contract

Edits to `SKILL.md` should stay lean:

- Sharpen **completion criteria** instead of adding prose
- Never add domain→skill lookup tables (against the product)
- Put long lists under `references/` (see `scan-roots.md`)

## Run the harness

With which-skill installed, in any agent session:

```text
run which-skill paraphrase cases
```

If you changed ranking behavior, paste the hit/miss table in the PR.
