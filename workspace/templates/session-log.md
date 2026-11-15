# Side session — {{YYYY-MM-DD}}
agent:                # e.g. claude-code, codex
session_started:      # HH:MM, from the clock
generated_at:         # full timestamp with offset, from the clock
machine:

## shipped
- item:               # one-line outcome, past tense
  evidence:           # receipt: link, message ID, file path, commit
  proof:              # tool | owner | inferred

## flagged
- item:               # surfaced but deliberately not acted on
  context:

## waiting_external
- item:               # open loop owned by someone else
  who:
  resurface_when:
