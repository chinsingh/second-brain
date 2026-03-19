Graduate the current lightweight project to a structured one. Run the sequence below.

---

## Upgrade sequence

1. **Confirm with the user** before doing anything: _"This will convert `{Category}/{ProjectName}.md` into a full project folder. Proceed?"_

2. **Create the folder** `{Category}/{ProjectName}/`

3. **Move the notes file** into the folder, keeping the filename:
   `{Category}/{ProjectName}.md` → `{Category}/{ProjectName}/{ProjectName}.md`

4. **Scaffold the following files:**

   `summary.md` — synthesize from the existing notes file:
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

   `decisions.md`:
   ```markdown
   # Decisions — {ProjectName}

   | Date | Decision | Rationale |
   |------|----------|-----------|
   ```

   `resources.md`:
   ```markdown
   # Resources — {ProjectName}
   ```

   Empty folders: `ai-chats/`, `conversations/`

5. **Append to daily log** — `Logs/YYYY-MM-DD.md`:
   ```markdown
   - **HH:MM** [upgrade / {Category}/{ProjectName}] Graduated from lightweight to structured project
   ```

Confirm: _"Upgraded {Category}/{ProjectName} to a structured project. Notes file preserved, summary scaffolded."_
