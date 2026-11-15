---
name: aw-log
description: Write a side-session log for Active Work. Use at the end of any working session that is not today's Workbench session and that changed something or left something waiting, or when the user types /aw-log or $aw-log, or says "log this to Active Work". Writes one file to the Active Work workspace's inputs/sessions/ folder. Never edits daily/ or carry-forward.md.
---

# aw-log: leave a side-session log

Workspace: `~/ActiveWork`. If your workspace is elsewhere, replace every `~/ActiveWork` in this file with its path.

Today's Workbench session (the one that ran "Start Active Work for today") owns `daily/` and `carry-forward.md`. Every other session is a side session and leaves a log instead, so its work still reaches the record. If this session *is* today's Workbench session, don't use this shortcut: write the daily file directly.

1. If `~/ActiveWork/workbench.md` doesn't exist, say so in one line and stop.
2. Read `~/ActiveWork/AGENTS.md` for the **Never touch** list, and the `timezone:` line of the newest file in `~/ActiveWork/daily/` (or the home time zone in `AGENTS.md` if there is none). Read the system clock in that zone (for example `TZ=Europe/London date`) for the file name and every time you write. Never write a time from memory.
3. Write `~/ActiveWork/inputs/sessions/YYYY-MM-DD-<agent>-<HHMM>.md` in the format of `~/ActiveWork/templates/session-log.md`, where `<agent>` is your tool (for example `claude-code` or `codex`) and HHMM is when this session started if you read the clock then, otherwise the time of this first log. If you log again later in the same session, update the same file. Leave out any section with no items.
4. One line per outcome, under `shipped`, `flagged` or `waiting_external`. Every item has a receipt (link, message ID, file path, commit) and a `proof:` of `tool`, `owner` or `inferred`. Write "sent" only with `proof: tool`. No receipt means it isn't an item.
5. Outcomes only: no conversation, no abandoned attempts, nothing from the **Never touch** list in `AGENTS.md`, and never a password, token or key.
6. Tell the owner the file's path and how many items it holds.

A side session may save its own notes and deliverables in `work/` and `outputs/`. It never edits `daily/`, `carry-forward.md`, `memory.md`, `AGENTS.md` or `workbench.md`.
