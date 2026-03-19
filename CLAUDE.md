# Claude Instructions for This Vault

## Vault Structure

This is an Obsidian vault. Projects are organized by category:

```
{Category}/{ProjectName}/          ← e.g. {Category}/{ProjectName}
  notes by me (any .md files)
  summary.md                       ← synthesized project context, always up to date
  decisions.md                     ← key decisions made, with dates and rationale
  resources.md                     ← links, tools, contacts, and anything you want Claude to remember
  ai-chats/
    YYYY-MM-DD-HH-MM-{model}.md    ← one file per AI conversation (e.g. claude, chatgpt, gemini)
  conversations/
    YYYY-MM-DD-{type}-{title}.md   ← meetings, emails, chats, transcripts, etc.
Logs/
  YYYY-MM-DD.md                    ← daily log across all activity
```

---

## Step 1 — Identify the Project at the Start of Every Session

- Read the conversation and **infer** the most likely Category/ProjectName based on what's discussed.
- **Confirm with the user** before proceeding: _"It sounds like this is about [Category/ProjectName] — is that right?"_
- If no project is relevant (e.g. a general question), skip all filing steps below.
- If the project folder doesn't exist yet, create it along with `summary.md`, `decisions.md`, `resources.md`, `ai-chats/`, and `conversations/`.

---

## Step 2 — Load Context at the Start of a Project Conversation

Once the project is confirmed, **always read** these files before responding:

1. `{Category}/{ProjectName}/summary.md` — the single source of truth for all prior history
2. `{Category}/{ProjectName}/decisions.md`
3. `{Category}/{ProjectName}/resources.md` — links, tools, contacts, and explicit memory
4. Any `.md` files written directly in `{Category}/{ProjectName}/` (excluding `summary.md`, `decisions.md`, `resources.md`, `ai-chats/`, and `conversations/`)

Both `ai-chats/` and `conversations/` are **archives only** — never read them to load context. `summary.md` already contains their distilled content.

**Category-level files** (e.g. files sitting directly in `{Category}/` rather than in a specific project subfolder) are **not mandatory to load upfront**, but Claude is free to browse and read them at any point during the conversation when they seem relevant — for background, shared context, or cross-project knowledge. Don't hesitate to look there if something in the conversation suggests it would help.

Briefly acknowledge what context you loaded (e.g. _"I've read your project summary and notes."_), then proceed.

---

## Step 3 — Filing

Filing is **never automatic**. It is always triggered explicitly by the user via one of these commands: `/file`, `/wrapup`, `/record`, `/save`

These all do the same thing — run the full filing sequence for the current conversation. During a conversation, Claude should focus on the work. The only exception is `resources.md` — write to it immediately whenever the user says "remember this", "save this link", or similar.

When a filing command is invoked, refer to `.claude/commands/file.md` for the full sequence.

---

## Step 4 — Processing an External Input

When the user pastes something that happened outside Claude — a meeting transcript, email, chat export, video transcript, or any other external record — treat it as a filing task.

### Supported input types

- `meeting` — any recorded or transcribed meeting
- `email` — single email or thread
- `chat` — Slack, WhatsApp, or any messaging export
- `transcript` — video, podcast, or call recording
- `doc` — article, brief, or document to file against the project

### 4a. Identify the project

- Same as Step 1 — infer from content and confirm before doing anything.
- Also identify the **input type** from the list above. If unclear, ask.

### 4b. Save the record

- File: `{Category}/{ProjectName}/conversations/YYYY-MM-DD-{type}-{title}.md`
    - e.g. `2026-03-05-meeting-kickoff.md`, `2026-03-05-email-client-feedback.md`, `2026-03-05-chat-standup.md`
- Derive the date from the content if mentioned, otherwise use today.
- Format:

    ```markdown
    # {Type} — {Title} — YYYY-MM-DD## Participants / From(attendees, sender, or parties involved — if mentioned)## Summary(2–4 sentences — the distilled essence, not a transcript recap)## Key Outcomes & Agreements(bullet list — firm conclusions only, not maybes or passing comments)## Action Items(bullet list with owner if mentioned)## Decisions(explicit calls made — distinguish from action items)## Open Questions(anything unresolved)
    ```


### 4c. Handling back-and-forth content

For inputs with conversational structure (meetings, chats, email threads), apply extra care:

- **Resolve contradictions** — if something was debated and then settled, capture only the final agreed position, not the debate.
- **Filter noise** — "we should probably look into that sometime" is not an action item or decision. Only capture firm commitments and explicit agreements.
- **Attribute when it matters** — if a decision or action item belongs to a specific person, note who. Not every statement needs attribution.
- **Prefer the end of the thread** — in long exchanges, later messages often supersede earlier ones. Weight conclusions over opening positions.

### 4d. Update `summary.md`

- Same rolling feedback loop: blend the existing `summary.md` with the new input.
- Give particular weight to action items, decisions, and any shift in project status.

### 4e. Update `decisions.md`

- Extract any explicit decisions or firm agreements and append them with the input date.
- Do not add speculative or tentative statements.

### 4f. Update the Daily Log

- Append a one-line entry to `Logs/YYYY-MM-DD.md` using the input's date.
- Format: `- **{Type}** [{Category}/{ProjectName}] {title} — (1 sentence on outcome)`

> After filing, external inputs are never re-read for context. They are fully absorbed into `summary.md` and that is the only place they live going forward.

---

## General Behaviour

- **Use wikilinks wherever possible** — when referencing any note, project file, person, or concept that exists (or could exist) as a note in the vault, use `[[wikilink]]` syntax rather than plain text or markdown links. This applies in all written content: `summary.md`, `decisions.md`, `resources.md`, `ai-chats/`, `conversations/`, and daily logs. For example, reference a project as `[[ProjectName]]`, a person as `[[PersonName]]`, or a related note as `[[decisions]]`. When the display text should differ from the note name, use the alias form: `[[NoteFile|Display Text]]`.
- **Write all notes from the user's perspective** — first person ("I", "we"), as if the user wrote them. Never write from Claude's perspective ("Claude suggested...", "the user decided...") or as a third-party observer ("<YOUR NAME HERE> should...", "confirm with <COLLABORATOR NAME>"). Decisions, action items, and next steps should read as the user's own notes, not a report about the user.
- **Always confirm the project** before loading context or filing anything.
- **Never guess a project silently** — if you're unsure between two, ask.
- **Create folders and files** if they don't exist yet. Never skip filing because a folder is missing.
- When updating `summary.md` or `decisions.md`, **rewrite the whole file** rather than appending, so it stays clean and coherent.
- If the user asks mid-conversation to file or save something, do it immediately without waiting for end of session.
- When the user says "remember this", "save this link", "add this to the project", or similar — append it to `resources.md` immediately. Use a sensible heading if one fits (e.g. `## Links`, `## Tools`, `## Contacts`, `## Notes`). Create the file if it doesn't exist. Never wait for end of session to do this.
