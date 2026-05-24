# Mindkernel

Your life, structured. Zero code. Pure protocol.

[![Ko-fi](https://img.shields.io/badge/Ko--fi-FF5E5B?style=flat&logo=ko-fi&logoColor=white)](https://ko-fi.com/gerardolucero)
[![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-FFDD00?style=flat&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/lucerorios0)
[![GitHub Stars](https://img.shields.io/github/stars/GerardoLucero/mindkernel?style=social)](https://github.com/GerardoLucero/mindkernel)

Mindkernel turns Claude Code into a personal Chief of Staff. You fill in one file with your context. Claude routes every question to the right expert, enforces your priorities, and always delivers a concrete recommendation — never just analysis.

No app. No API. No deployment. Open the directory in Claude Code and start.

---

## The model

Your life has three areas. Every question you have belongs to one of them.

| Area | Covers |
|---|---|
| Work | Career, job decisions, skills, freelance, positioning |
| Money | Finances, savings, debt, investments, cash flow |
| Life | Energy, health, habits, balance, relationships, direction |

Each area has a lead agent with a defined role, a workflow, and a specific output format. When you ask something, the Chief of Staff routes it to the right lead, gets a structured answer, and surfaces any risk before anything else.

---

## Getting started

### 1. Clone

```bash
git clone https://github.com/GerardoLucero/mindkernel.git
cd mindkernel
```

### 2. Open in Claude Code

```bash
claude
```

Claude Code reads `CLAUDE.md` on startup and assumes the Chief of Staff role automatically.

### 3. Fill in your state

Edit `kernel/state.md`. Replace every placeholder with your actual context:

- Who you are and what you do
- Your current priorities (keep it to 3)
- Your active focus this week
- Your current situation across work, money, and life

This file is what makes the system useful. The more honest and specific you are, the better the responses.

### 4. Fill in your area context

Each area has a context file with the relevant fields:

- `areas/work/context.md` — role, target, skill gaps, active opportunities
- `areas/money/context.md` — income, expenses, debts, goals
- `areas/life/context.md` — energy, habits, balance, what drains and restores you

Fill these in once, update them when things change.

### 5. Run your first check-in

```
/orchestrate daily
```

---

## How it works

Every request you send goes through a routing protocol defined in `CLAUDE.md`:

1. Identify which area owns the question
2. Activate the lead agent for that area
3. Deliver output in a fixed format:

```
[Area: work | money | life]
Situation: what is happening
Recommendation: what to do — specific and actionable
Risk: any balance or financial risk flagged first
Next step: one action, by when
```

The system always gives you a recommendation. Never just an observation. And it always flags a balance or financial risk before addressing anything else.

---

## Slash commands

| Command | What it does | Time |
|---|---|---|
| `/orchestrate daily` | Morning check-in — energy, urgency, one focus for today | 5-10 min |
| `/orchestrate weekly` | Full weekly review — what happened, what is next, KPIs | 20-30 min |
| `/orchestrate focus` | Quick answer: what should I work on right now | 2 min |
| `/daily-focus` | Minimal version of daily — one question, one answer | 2 min |

---

## File structure

```
mindkernel/
├── CLAUDE.md                    The kernel — routing protocol and principles
├── kernel/
│   └── state.md                 Your context, priorities, and current focus
├── areas/
│   ├── work/context.md          Work area details
│   ├── money/context.md         Money area details
│   └── life/context.md          Life area details
├── .claude/
│   ├── agents/
│   │   ├── work-lead.md         Work area lead agent
│   │   ├── money-lead.md        Money area lead agent
│   │   └── life-lead.md         Life area lead agent
│   └── skills/
│       ├── orchestrate/         /orchestrate command
│       └── daily-focus/         /daily-focus command
└── log/                         Weekly review logs (gitignored)
```

---

## Extending the system

### Add a specialist agent

Create a file in `.claude/agents/`. The frontmatter `description` field controls when Claude Code invokes the agent automatically:

```markdown
---
name: contract-reviewer
description: Reviews contracts and identifies risky clauses. Use when the user needs to evaluate a job offer, consulting agreement, or any legal document.
---

# Contract Reviewer

## Mission
...
```

### Add a slash command

Create a directory in `.claude/skills/your-skill/` with a `SKILL.md` file. It becomes the prompt that runs when the user types `/your-skill`.

### Add a new area

Copy one of the existing `areas/` directories, rename it, and add a corresponding lead agent in `.claude/agents/`. Then update `CLAUDE.md` to include the new area in the routing table.

---

## Principles

**The system serves your life — not the other way around.** If a ritual creates friction, remove it. If an agent gives bad answers, rewrite it. The goal is better decisions, not a complete system.

**Concrete outputs always.** Every agent ends with a recommendation or an action. Analysis without a recommendation is not useful.

**Maximum 3 active focuses.** The system resists the instinct to do everything. If `kernel/state.md` has more than 3 priorities, something needs to be removed.

**Balance risk is surfaced first.** If a response involves a risk to your health, energy, or relationships, that gets flagged before any work or money answer.

---

## Privacy

Everything runs locally inside Claude Code. Your `kernel/state.md` and `areas/*/context.md` files contain personal information — keep them private. The `.gitignore` excludes `log/` from version control. The context files are committed because they are templates — replace them with your real data only in a private fork.

---

## License

MIT
