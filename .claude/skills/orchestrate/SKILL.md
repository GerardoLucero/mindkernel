---
name: orchestrate
description: Run a structured review of your current situation. Use /orchestrate daily for a morning check-in, /orchestrate weekly for a full weekly review, or /orchestrate focus to get a quick answer on what to work on right now.
---

# Orchestrate

Read `kernel/state.md` before starting.

Detect the mode from the argument:

- `/orchestrate daily` → Daily check-in
- `/orchestrate weekly` → Weekly review
- `/orchestrate focus` → Quick focus answer
- No argument → Ask which mode

---

## Daily (5-10 minutes)

Ask these three questions in order. Wait for the answer before continuing.

1. "How is your energy today? (high / medium / low)"
2. "Anything urgent that was not planned?"
3. "Can you protect at least 1 hour for your top focus today?"

Then deliver:

```
TODAY'S FOCUS: [one concrete thing based on state.md priorities + declared energy]
ALERT: [if there is a risk — otherwise: none]
REMINDER: [this week's focus from state.md]
```

---

## Weekly (20-30 minutes)

Guide through four sections. One at a time, wait for responses.

**Section 1 — Last week**
- What went well?
- What did you not execute?
- What consumed energy without value?

**Section 2 — Three areas**
- Work: any progress on your professional goal?
- Money: any relevant financial movement?
- Life: balance score this week (1-10)?

**Section 3 — KPIs**
Ask for any metrics the user tracks. Record answers.

**Section 4 — Next week**
- Define up to 3 focuses for next week
- Any risks or blockers to name?

At the end, update `kernel/state.md` with the new focuses and save a report to `log/YYYY-MM-DD-weekly.md`.

---

## Focus (2 minutes)

Read `kernel/state.md`. Ask one question:

"How much time do you have right now — more than an hour, or less?"

- More than 1 hour → highest-impact task from current focuses
- Less than 1 hour → small but strategic task that moves something forward
- If they mentioned low energy → maintenance task, not construction
