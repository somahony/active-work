You are a scheduled job for the Active Work workspace in the current folder. No one is watching this run. Read `workbench.md`, section "Scheduled jobs", and follow it exactly.

Period covered: since the last file named `*-overnight-check.md` in `inputs/`, or the last 24 hours if there is none. Take the current time from the system clock.

1. Read `AGENTS.md`, `carry-forward.md` and the most recent file in `daily/`. Do not edit any of them.
2. For each item in the `waiting_external` lane whose `review_after` date has arrived, check the connected sources (read-only) for a reply or change. For a source you can't read, record `could_not_access`. Never guess.
3. Write one file, `inputs/YYYY-MM-DD-overnight-check.md`, with: `period:`, `checked_at:`, `sources_checked:` (each `ok` or `could_not_access`), then one line per item that changed, with its `id` and the evidence. If an item is already waiting on the owner as a question, refer to it by its `id`; do not raise it again as a new question.
4. If nothing changed, say so in one line. If you failed part-way, say what failed as the first line of the file.

Do not send, post, reply, book, pay, delete, or change any other system. Do not write anywhere except that one file.
