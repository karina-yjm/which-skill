# Example sessions

Illustrative shapes. In a real run, **Quote** must be copied verbatim from the live skill's `description` — never invented.

## 1. Paraphrase hit (color-blind)

**User:** Is my landing page friendly to color-blind users?

**which-skill:**

**accessibility-review** — Reviews UI for accessibility issues  
- Quote: `"(verbatim from that skill's description — e.g. accessibility / a11y / contrast)"`  
- Why: intent = inclusive color perception → accessibility audit  
- Altitude: atomic  
- Invoke: attach `accessibility-review`, or say "audit this page for a11y"  
- *Waiting for your OK — not loading it*

## 2. Combo altitude

**User:** Idea is fuzzy and I don't want code yet — later I'll need tickets.

**which-skill:**

1. **grill-with-docs** / **brainstorming** — sharpen the idea first  
   - Quote: `…`  
   - Altitude: combo step 1  
2. **to-issues** / **writing-plans** — split into parallel work  
   - Quote: `…`  
   - Altitude: combo step 2  

*Waiting for your OK before loading either.*

## 3. Already named → exit

**User:** Use tdd to build the login form.

**which-skill:** You already named `tdd`. No routing needed — run that skill.

## 4. No skill needed

**User:** Translate this sentence to English.

**which-skill:** No skill needed — one-shot translation. Want me to just do it?

## 5. Weak description → author feedback

**User:** Make this copy sound less like a robot.

Nearest install only says it rewrites marketing emails:

**humanizer-zh** — …  
- Quote: `"…"`  
- Why: intent = de-AI the prose  
- Altitude: atomic  

```text
Description feedback for `humanizer-zh`:
- Missed paraphrase: "sound less like a robot"
- Suggested trigger branch: "Use when prose feels AI-generated or robotic."
```

## 6. Nothing local → find-skills

**User:** Is there a skill for drawing circuit diagrams? *(none installed)*

**which-skill:** Nothing in the live catalog fits. I can help directly, or we can search installs with `find-skills`.
