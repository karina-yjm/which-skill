# Paraphrase cases

Eval harness for **intent match, not keyword match**.

**Expected family** = hint. If that skill is not installed, mark `skipped-not-installed` and note the nearest installed alternative (still quote-backed).

**Report per case:** `hit | miss | skipped-not-installed` · recommended name · quote used.

Prefer user phrasings with **zero token overlap** against the target skill's published trigger words.

## Scoring

| Result | Criteria |
|--------|----------|
| `hit` | Recommended family matches expected (or clear synonym) **and** recommendation includes a verbatim description quote |
| `miss` | Wrong family, empty recommend when a local skill exists, or recommend without a quote |
| `skipped-not-installed` | No installed skill in the expected family — not a miss |

## Accessibility & UX

| # | User phrasing | Expected family |
|---|---------------|-----------------|
| 1 | Is my page friendly to color-blind users? / 我的网页对色盲用户友好吗 | accessibility-review |
| 2 | Can older people even read this button contrast? / 这个按钮的对比度老年人看得清吗 | accessibility-review |
| 3 | Keyboard-only users — can they finish every flow? / 键盘党用不了鼠标，页面能操作完吗 | accessibility-review |

## Writing & voice

| # | User phrasing | Expected family |
|---|---------------|-----------------|
| 4 | This reads like ChatGPT wrote it — make it human / 这段话太像 AI 写的了，帮我改成人话 | humanizer-zh / humanizer |
| 5 | Tone doesn't sound like our company / 品牌语气对不上，读起来不像我们公司 | brand-voice-enforcement / brand-review |

## Product & planning

| # | User phrasing | Expected family |
|---|---------------|-----------------|
| 6 | Idea is still fuzzy — don't write code yet / 想法还不成型，先别写代码 | grill-with-docs / grill-me / brainstorming |
| 7 | This spec is a blob — split into parallel tickets / 需求一大坨，怎么拆成能并行开干的小单 | to-issues / writing-plans |
| 8 | Is this feature even worth doing? How to prioritize? / 这个功能值不值得做，怎么排优先级 | prioritization / space-prioritization-engine |

## Engineering

| # | User phrasing | Expected family |
|---|---------------|-----------------|
| 9 | Prod is on fire and the logs make no sense / 线上炸了但日志看不懂，怎么系统排查 | systematic-debugging / diagnosing-bugs / debug |
| 10 | Tests first, implementation second — no coding ahead / 先写测试再写实现，别直接开码 | tdd / test-driven-development |
| 11 | This PR is huge — carve it into reviewable slices / PR 太大了，帮我按可审的方式切开 | split-to-prs |

## Design & frontend

| # | User phrasing | Expected family |
|---|---------------|-----------------|
| 12 | First viewport looks like every other AI landing page / 落地页第一屏太像通用 AI 模板了 | design-taste-frontend / frontend-design |
| 13 | Recreate this screenshot as working UI / 截图里的界面，照着还原成代码 | image-to-code |

## Research & papers

| # | User phrasing | Expected family |
|---|---------------|-----------------|
| 14 | How would a reviewer tear this survey apart? / 审稿人会怎么砍我这篇综述 | academic-paper-reviewer / paper-writing / peer-review |
| 15 | Has anyone done this already — don't reinvent / 这个方向有没有人做过，别重复造轮子 | deep-research / competitive-intelligence |

## Negative space (must not force a skill)

| # | User phrasing | Expected |
|---|---------------|----------|
| 16 | Translate this sentence to English / 把这句话翻译成英文 | no skill needed |
| 17 | Use tdd to build login / 用 tdd 帮我写登录 | stop — skill already named |
| 18 | Is there a skill for drawing circuit diagrams? *(assume none installed)* / 有没有能画电路图的 skill | no local match → find-skills |

## Add a case

When a real miss happens in the wild: append the paraphrase → skill that should have won. Keep zero-token overlap with that skill's triggers when possible. See [CONTRIBUTING.md](../CONTRIBUTING.md).
