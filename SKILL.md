---
name: which-skill
description: >-
  which-skill — quote-backed intent match over installed agent skills;
  recommend 2–3, never autoload. Use when asking which skill to use, how to
  pick a skill, what tool fits a job, or describing a task without naming a
  skill — including paraphrases that miss trigger words (color-blind UI →
  accessibility). Also use to run the paraphrase harness. Do not use when a
  skill is already named, or to search/install from the ecosystem (find-skills).
---

# which-skill

**Intent match, not keyword match.**

Recommend-only · quote-backed · live-catalog.

Ranks **already installed** skills and **stops at the recommendation**. Never silently load or run another skill.

Not `find-skills` (ecosystem install). Not a hardcoded domain→skill table.

Demos: [examples.md](examples.md) · Harness: [references/paraphrase-cases.md](references/paraphrase-cases.md)

## Steps

### 1. Gate — negative space

| Signal | Action |
|--------|--------|
| User already named a skill | Stop — router not needed |
| Trivial one-shot, no specialized workflow | **No skill needed** — just do the task |
| Needs a skill that is clearly **not installed** | Hand off to `find-skills` |

**Done when:** you exited with a clear reason, or you proceed knowing a local skill may exist.

### 2. Extract intent

One sentence: **job** (outcome) · **object** (artifact) · **constraints**.

Pick **altitude**:

| Altitude | Meaning |
|----------|---------|
| **atomic** | One skill |
| **combo** | 2–3 skills in sequence |
| **flow** | Multi-session pipeline (only if those skills are installed) |

**Done when:** a restatement without the user's wording still picks the same family and altitude.

### 3. Load the live catalog

Single source of truth = **this session's descriptions**. No memorized tables.

1. Prefer the in-context skill catalog (`name` + `description`).
2. If missing / thin / stale: scan skill roots and read each `SKILL.md` **frontmatter only**. Paths: [references/scan-roots.md](references/scan-roots.md). Follow symlinks; **skip broken**; optionally report `reachable / broken`.
3. Skip `which-skill`, `skill-router`, and non-actionable meta docs.

**Done when:** you have `{name, description}` for every reachable install — not a memory guess.

### 4. Semantic rank (quote-backed)

Score against the intent sentence (not surface keywords):

| Axis | Strong | Weak |
|------|--------|------|
| Job | description's action = outcome | same domain, different action |
| Object | right artifact kind | adjacent domain only |
| Scope | altitude matches | too broad or too narrow |

- **Paraphrase test:** phrasing would miss the skill's triggers, intent still matches → still a hit.
- **Quote rule:** every keep binds intent to a **verbatim** phrase from that skill's description. No "sounds related."

Return top **2–3**. Combos count toward the cap. Specific beats generic; atomic beats flow when one skill suffices.

**Done when:** each candidate has intent ↔ quote; altitude is decided.

### 5. Present (recommend-only)

Reply in the user's language. Do **not** open or run a recommended skill until they confirm.

```text
**{name}** — {one-line what it does}
- Quote: "{verbatim from description}"
- Why: {intent ↔ that quote}
- Altitude: atomic | combo step N | flow
- Invoke: {how to attach — wait for OK}
```

Weak but paraphrase-solid → still recommend, then step 6.

**Done when:** 2–3 picks with quotes, or an explicit no-match / no-skill-needed path. No catalog dump. No autoload.

### 6. Description feedback (weak / empty only)

When the best match is weak, or paraphrase would work but the description is too narrow:

```text
Description feedback for `{name}`:
- Missed paraphrase: "{user phrasing}"
- Suggested trigger branch: "{one Use when… clause}"
```

At most **one** feedback block. For skill authors — optional for the user.

No local fit → offer bare help → `find-skills` only if they may want an **uninstalled** skill.

**Done when:** feedback emitted for a real gap, or skipped because quotes were strong.

## Hard rules

1. **Recommend-only** — never autoload another skill  
2. **Quote-backed** — no quote → no recommend  
3. **Live catalog** — never hardcode domain→skill maps  
4. Never invent a skill name absent from the loaded catalog  
5. Prefer specific over generic; atomic over flow when one skill suffices  

## Paraphrase harness

When the user says "run paraphrase cases" / self-check / after editing this skill: load [references/paraphrase-cases.md](references/paraphrase-cases.md) and score **every** case against the **current** catalog.

**Done when:** each case is `hit | miss | skipped-not-installed` + name + quote used.
