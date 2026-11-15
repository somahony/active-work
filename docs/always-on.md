# Level 3: always-on

Level 3 is Level 2 plus a machine that stays on and runs agents on a schedule: an overnight check of what you're waiting on, a job that drafts while you sleep, a weekly count of what got finished. You don't need it to get the benefit of the method. Run Level 2 for a month first.

## What it involves

- **A machine that stays on** and holds the one true copy of the workspace. Other devices read it over a private network or a synced folder. Decide which copy is the real one and make the others read-only; two writable copies will diverge.
- **Scheduled jobs.** Each is a prompt run by an agent's non-interactive command on a timer (launchd on macOS, cron or systemd on Linux). [config/scheduled/](../config/scheduled/) has one worked example.
- **One channel that can interrupt you,** and only for things that can't wait. Everything else goes into `inputs/` for the next session to read. Pull, not push.
- **A second model.** Have a different model from your daytime one run the overnight check or review the day's work. It catches what the first one misses.

## The rules, and why

The rules for scheduled jobs are in `workbench.md`. The reasons:

- **A job writes only its own file.** A job that edits the daily file collides with the session running the day.
- **Each job is told its period and reads the clock.** Otherwise a late run reports on the wrong day.
- **Revise a question; never ask it again.** An overnight job that can't see what it already asked will ask it every night, and the list of things waiting on you grows until you stop reading it.
- **Say what happens when a run is missed.** After the machine was off, some jobs should skip (yesterday's weather) and some should catch up (the weekly count). Decide per job and write it next to the schedule.
- **Say where a failure shows.** A heartbeat that reports "ok" over a failed job is worse than none. Each job writes its failure as the first line of its file, and the morning start reads it.
- **Turn off automatic updates** for the agent tools on that machine, or pin versions. An overnight update that changes a tool's behaviour is the outage you won't see until morning.

## What it costs

More than the other two levels put together. The upkeep is almost all here: credentials, scheduled jobs, and tools changing under them. Count that before you build it.

## Security

A scheduled agent has your access and nobody watching. Read-only access, its own narrowly scoped credentials kept outside the workspace, and no ability to send. If your work data is involved, this is your employer's decision, not yours.
