Re-read all project files and update context to reflect any changes made outside this session. Run the sequence below for the current project type.

---

## Structured project sync

1. **Re-read the notes file** — `{Category}/{ProjectName}/{ProjectName}.md` — your file, read-only
2. **Re-read the category file** — `{Category}/{Category}.md` if it exists
3. **Scan daily logs** — read all `Logs/YYYY-MM-DD.md` entries dated after the last modification of `summary.md`. Extract anything relevant to this project.
4. **Update `summary.md`** — blend any new information from steps 1–3 into the existing summary. Rewrite the whole file:
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

Confirm: _"Synced. Summary updated with changes since [date of previous summary]."_

---

## Lightweight project sync

1. **Re-read the project file** — `{Category}/{ProjectName}.md` — read-only
2. **Re-read the category file** — `{Category}/{Category}.md` if it exists
3. **Scan daily logs** — read all `Logs/YYYY-MM-DD.md` entries dated after the last modification of the project file. Extract anything relevant to this project.
4. **Update the status line** at the top of the project file if the log entries indicate a change in status.

Confirm: _"Synced. Status updated with changes since [date of last update]."_
