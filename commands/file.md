File this conversation to the vault. Perform all steps below in order.

## Voice
Write everything in the first person, from the user's perspective — as if they wrote these notes themselves. Use "I" and "we", not "the user", "<YOUR NAME HERE>", or "Claude". Action items, decisions, and next steps should read as the user's own intentions, not observations about them.

Good: "Confirm recency-handling approach with <COLLABORATOR NAME> before next sprint"
Bad: "<YOUR NAME HERE> should confirm their proposal with <COLLABORATOR NAME>"

Good: "10:00 [{Category}/{ProjectName}] Reviewed sandbox implementation — pausing dev pending gap analysis"
Bad: "Claude reviewed the transcript showing <YOUR NAME HERE> decided to pause development"

---

## 1. Confirm the project and type
If a project was identified earlier in this conversation, confirm it.
If not, infer from the conversation and confirm with the user before proceeding.
If no project applies, log under [General] in the daily log only.

Determine whether the project is **lightweight** (single `.md` file under a category) or **structured** (folder containing `summary.md`).

---

## Lightweight project filing

### L1. Update the status line
Update the status line at the top of `{Category}/{ProjectName}.md` to reflect where things stand after this session.

### L2. Update the category file
If any style, persona, or preference decisions were made — anything that applies to the category broadly, not just this project — update `{Category}/{Category}.md` accordingly.

### L3. Append to the daily log
File: `Logs/YYYY-MM-DD.md` (create if it doesn't exist)
```markdown
- **HH:MM** [claude / {Category}/{ProjectName}] (1 sentence on what was discussed and outcome)
```

Once done, confirm: _"Filed to {Category}/{ProjectName}."_

---

## Structured project filing

### S1. Save the AI chat summary
File: `{Category}/{ProjectName}/ai-chats/YYYY-MM-DD-HH-MM-claude.md`
```markdown
# Claude Conversation — YYYY-MM-DD HH:MM

## What We Discussed
(2–4 sentence summary of the main topics)

## Key Outcomes
(bullet list of conclusions, answers, things resolved)

## Open Questions / Next Steps
(anything left unresolved or flagged for follow-up)
```

### S2. Update `summary.md`
Rolling feedback loop: blend the existing `summary.md` with this conversation to produce a new summary. Rewrite the whole file:
```markdown
# {ProjectName} — Project Summary
_Last updated: YYYY-MM-DD_

## What This Project Is
(1–2 sentences)

## Current Status
(where things stand right now)

## Key Context & Background
(important facts, constraints, history)

## Open Questions & Next Steps
(what needs to happen next)
```

### S3. Update `decisions.md`
Extract any decisions made in this conversation — technical choices, strategic calls, things explicitly agreed upon. Append new entries only. Never delete old ones:
```markdown
| YYYY-MM-DD | (what was decided) | (why, and any trade-offs noted) |
```

### S4. Append to the daily log
File: `Logs/YYYY-MM-DD.md` (create if it doesn't exist)
```markdown
- **HH:MM** [claude / {Category}/{ProjectName}] (1 sentence on what was discussed and outcome)
```

Once done, confirm: _"Filed to {Category}/{ProjectName}. Summary updated, N decisions recorded."_
