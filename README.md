# MotionViz Skills System

**stop re-explaining your standards to AI. teach it once.**

Skills are instruction files that tell AI coding tools (Antigravity, Cursor, Claude Code) exactly how to build things *your way* — every time, without revision loops.

instead of prompting and praying, you prompt with context.

---

## what's inside

| Skill | What It Does |
|---|---|
| **`cro-landing-page`** | 9-section conversion-first page structure. hero clarity → trust signals → friction elimination → final CTA. based on Unbounce benchmark data (57M conversions). |
| **`component-architecture`** | naming conventions, file structure, prop patterns, and composition rules so every component ships consistent. |
| **`design-system`** | brand tokens (colors, type scale, spacing), Swiss Brutalist aesthetic defaults, and design constraint enforcement. |
| **`responsive-patterns`** | mobile-first responsive layouts. 44px touch targets, thumb-zone CTA placement, sticky nav patterns, no horizontal scroll — ever. |
| **`seo-meta`** | auto-generates meta titles, descriptions, OG tags, and structured data following brand guidelines. no more manual SEO. |

---

## quick start

### 1. clone the repo

```bash
git clone https://github.com/YOUR_USERNAME/motionviz-skills.git
```

### 2. install a skill

drop the skill folder into your AI tool's skills directory:

- **Antigravity**: `/mnt/skills/user/`
- **Cursor**: `.cursor/skills/`
- **Claude Code**: reference in your project prompt

### 3. prompt normally

the AI now follows your system automatically. no re-explaining brand colors. no "make it more like this." no revision #47.

---

## how skills work

each skill is a `SKILL.md` file — plain markdown that defines:

```
what the task is
when to trigger it
rules and constraints
examples of correct output
```

that's it. the AI reads the file before writing any code and follows your standards instead of improvising.

---

## create your own skill

```markdown
# SKILL.md

## name
your-skill-name

## description
what this skill does and when to use it

## rules
- rule 1: always do X
- rule 2: never do Y
- rule 3: follow this structure

## examples
[show the AI what good output looks like]
```

save it. install it. never repeat yourself again.

**anything you explain to AI more than once should be a skill:**

- client onboarding checklist → skill
- QA testing protocol → skill
- content structure → skill
- API patterns → skill
- deployment config → skill

---

## the difference

| without skills | with skills |
|---|---|
| "make the CTA red... no, darker... no, #B5121C" | CTA is #B5121C automatically |
| "use mobile-first... I said mobile FIRST" | every component starts mobile |
| "the hero needs headline + sub + single CTA" | 9-section structure every time |
| 5 revision rounds | ships correct on first prompt |

---

## built by

**[@Motion_Viz](https://x.com/Motion_Viz)** — AI-powered web design studio specializing in conversion-optimized landing pages for SaaS founders and course creators.

if these skills save you time, ⭐ the repo and [follow me on GitHub](https://github.com/YOUR_USERNAME) — new skills dropping regularly.

---

## license

MIT — use them, fork them, make them yours.
