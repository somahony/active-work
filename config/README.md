# Configuration examples

Everything here is optional and is an example to adapt, not a file to copy blindly. Check each against your tool's current documentation: settings formats change.

## `claude-code/settings.example.json`

Permission rules for Claude Code so that starting and closing the day doesn't prompt for every file. It allows reading and editing inside `~/ActiveWork`, allows the `date` command (the rules take times from the clock), and denies reading SSH keys and `.env` files.

To use it, merge the `permissions` block into `<your workspace>/.claude/settings.json` (applies in that folder only) and change the path if your workspace isn't at `~/ActiveWork`. It grants nothing outside the workspace, so anything else still asks you first. Two limits: settings in the workspace folder apply only to sessions opened there, and the `date` rule may not cover a command that sets a time zone first (`TZ=… date`), which will then ask once.

## `scheduled/`

For Level 3 only (an always-on machine). Read [docs/always-on.md](../docs/always-on.md) first.

- `overnight-check.md`: the prompt for one scheduled job. It reads your waiting items, checks connected sources read-only, and writes one file to `inputs/`. Copy it to `<your workspace>/jobs/overnight-check.md`.
- `com.example.activework.overnight-check.plist`: a macOS launchd job that runs it at 05:30. Replace `AGENT_COMMAND` with your agent's non-interactive command (for example `claude -p` or `codex exec`), rename the label, put the file in `~/Library/LaunchAgents/` and load it with `launchctl load`. Run the command by hand first and read the file it writes.
- On Linux, the same command works from cron: `30 5 * * * cd "$HOME/ActiveWork" && AGENT_COMMAND "$(cat jobs/overnight-check.md)" >> /tmp/activework-overnight-check.log 2>&1`

A scheduled agent runs with whatever access you gave it and nobody watching. Give it read-only access, and use a different model from your daytime one if you can: a second model catches what the first one misses.
