# Active Work {{YYYY-MM-DD}}

## meta
status: open
date: {{YYYY-MM-DD}}
timezone: {{TIMEZONE}}
opened_at:
opened_by:            # model and tool, e.g. Claude in Claude Code, or a local model in Codex
closed_at:
closure_mode:         # closeout | next_open

## sources_checked
- source:
  checked_at:
  result:             # ok | could_not_access
  notes:

## live_queue
updated_at:
now:
  - item:
    reason:
next:
  - item:
    reason:
agent_can_progress:
  - item:
    next_action:
ignore_today:
  - item:
    reason:

## execution_ledger
- id:
  item:
  state: queued       # queued | active | delegated | waiting | completed | failed
  owner:
  started_at:
  completion_criteria:
  latest_update:
  receipt:
  proof:              # tool | owner | inferred (required when state is completed)
  blocker:
  resurface_when:

## decisions
- time:
  decision:
  why:
  saved_to_memory: false

## approvals
- time:
  action:
  ready_now: false
  approved: false
  receipt:

## log
<!-- Dated one-line entries for work done during the day. Long notes go to work/ with a pointer here. -->

## carry_forward
Today's changes only. The full list lives in carry-forward.md.
- added:
- closed:
- changed:
Full list: carry-forward.md (N items)

## closeout
status:
closed_at:
done:
  planned:
  unplanned:
waiting:
blocked:
decisions_to_make:
approvals_ready_now:
saved_to_memory:
