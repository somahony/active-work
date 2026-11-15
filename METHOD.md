# The method

## The problem

AI agents are capable and forgetful. Each session starts blank. Each tool keeps its own history, so what you told ChatGPT this morning is unknown to Claude this afternoon. And the best model changes every few months.

The usual workarounds (long chat threads, pasting yesterday's summary, a tool's built-in memory) tie your working memory to one product and one conversation. When the thread gets long, the tool changes, or the model is swapped, the memory goes with it.

## The idea: two memories, kept outside the model

| | Short-term memory | Long-term memory |
|---|---|---|
| **Holds** | What's happening now: today's plan, what's in progress, what's waiting on whom, what was done and the proof | What should still be true next month: decisions and why, standing rules, people, where things live, lessons |
| **Lives in** | `daily/YYYY-MM-DD.md` + `carry-forward.md` | `memory.md`, or a memory database |
| **Written** | Continuously, by the agent, as work happens | Deliberately, a few times a week, when something durable is learned |
| **Read** | At the start of every session | When context is needed: "what did we decide about X?" |

Both are plain files or a plain database **you** own. Any agent that can read files can use them. That is the whole trick: **the files are the contract, the model is interchangeable.** One agent on Monday, another on Tuesday, something else next year: same files, same format, no lost context.

## The daily rhythm

**Start** ("Start Active Work for today"). The agent reads the rules (`workbench.md`), your long-term directives, yesterday's file and `carry-forward.md`, then checks live sources you've connected (calendar, task list, email). It creates today's file and gives you a short brief: top priorities, what it can do without you, what needs your approval, one thing to ignore.

**During the day.** You work with the agent as usual. It keeps the daily file current: what it started, what finished (with a link or receipt), what's now waiting on someone. Saying "done" or "sent" is enough for it to update the record. Ask "what's next?" any time; the answer comes from the file, not from the agent's memory of the conversation.

**Close** ("Close out Active Work for today"). The agent checks nothing is falsely marked in progress, updates `carry-forward.md` (each open item once, with an owner, a date and when to look at it again), saves anything durable to long-term memory, and lists what still needs your approval.

Tomorrow, any agent picks up from those files.

**Other sessions.** Only one session runs the day. Any other agent session that does work for you leaves a short log in `inputs/sessions/`, and the day's session folds it in. That is how work done elsewhere still reaches the record without two agents writing the same file.

## The rules that make it work

These are in `workspace/workbench.md`. They came from what went wrong without them.

1. **Pull, not push.** The system answers when you ask ("what's next?") instead of sending you briefings you'll learn to ignore. Background jobs, if you have them, put their findings into the files for the next session to read; they don't message you.
2. **Machine-readable, not a journal.** Fixed headings and fields in the daily file, so the next agent (or a script) can read the state reliably. Prose notes go in `work/`, with a one-line pointer.
3. **Every open item lives once.** `carry-forward.md` is the single list. Copying yesterday's list into today's file is how files bloat and stale items survive.
4. **Every item has a lane.** `my_action`, `agent_action`, `waiting_external`, `parked`, `scheduled`. Only the first two belong on today's agenda; the rest stay quiet until their date or a change.
5. **Done means proven.** An item is `completed` only with a receipt: a link, a message ID, a file, a commit. "I'll handle it" is not a state; the agent must say "queued, not started" unless work has actually begun.
6. **Unread is not empty.** A source the agent couldn't reach is recorded as `could_not_access`, never as "nothing new".
7. **Approval gates.** The agent prepares; you decide. Anything that sends, pays, books, deletes, or touches credentials or other people's calendars needs your explicit yes. It prepares everything up to that point so the decision is one word.
8. **Roles, not products.** Rules name roles ("the Workbench agent", "the scheduled job"), never a specific model, so you can switch tools without rewriting anything. If a tool is missing in one agent, it records `could_not_access` and carries on.
9. **Capture long-term memory deliberately.** Save decisions, rules, people and lessons, not daily summaries or routine completions. Search before saving and update rather than duplicate.
10. **Times come from the clock.** An agent's sense of time is a guess. Every time written to a file is read from the system clock or from the source it describes.
11. **"Sent" needs proof from this session.** Each completion says whether a tool result proved it, the owner said so, or the agent inferred it. Only the first can say "sent".
12. **One writer for the day.** Other sessions leave logs; they don't edit the daily file or the list.

## Long-term memory

Start with `memory.md`: a file with sections for standing rules, decisions, people, and where things live. It's enough for months.

Move to a database when the file gets too big to read every session, or when you want several agents and devices to search it. See `long-term-memory/README.md` for the options.

A lesson from running it: automatic import of email and tasks into long-term memory was tried and switched off, because it filled the memory with noise. Deliberate capture works better.

## What it costs

- **Time.** A start and a close each day. Each takes the agent some minutes and takes you one line. The close is the step people skip.
- **Upkeep.** Levels 1 and 2 need very little. Level 3 adds an always-on machine, scheduled jobs and more credentials, and all three need looking after.
- **Drift.** The rules file grows, and standing rules pile up and start to contradict each other. Review them monthly and prune.

## What it is not

- Not a task manager. If you use a task manager, keep using it; `carry-forward.md` references those IDs rather than copying tasks.
- Not a substitute for judgement. The agent proposes; the approval gates keep you in charge of anything that leaves your machine.
- Not tied to one AI company. That's the point.
