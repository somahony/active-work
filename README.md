# Active Work

A way of working with AI agents that survives the end of a chat, a change of tool and a change of model.

Every agent forgets. Close the session and the context is gone; switch from one AI to another and you start from zero. Active Work keeps your working memory in plain files you own, so any agent can pick up where the last one stopped:

- **Short-term memory.** One daily file per day plus one living list of everything unresolved (`carry-forward.md`). The agent reads them at the start of a session and writes them as it works.
- **Long-term memory.** Decisions, standing rules, people and lessons that should still be true next month. Start with a file (`memory.md`); move to a database when it outgrows that.

The files are the contract. The model is interchangeable.

## Set it up

Paste the prompt in **[SETUP-PROMPT.md](SETUP-PROMPT.md)** into the AI you want to use. It works out what it can do, asks you a short [questionnaire](QUESTIONNAIRE.md) so the system fits the way you work, shows you its plan, and installs it. Allow 15 to 20 minutes.

Prefer to do it by hand? Follow [INSTALL.md](INSTALL.md).

Then, every working day, two phrases:

> **Start Active Work for today**
>
> **Close out Active Work for today**

## Pick a level

| Level | You need | What you get | Setup |
|---|---|---|---|
| **1. Method only** | A Project in Claude, ChatGPT, Gemini or similar | The daily habit, with two files you update by hand | 10 min |
| **2. Your computer** | An agent that can use files: Claude Code, Codex, Claude Cowork, Gemini CLI | The agent keeps the files itself; start, close and log shortcuts | 15–20 min |
| **3. Always-on** | A machine that stays on | Level 2 plus scheduled jobs that read and prepare while you sleep | Weeks; see [docs/always-on.md](docs/always-on.md) |

Start at Level 2 if you already use an agent on your computer. Most people never need Level 3.

## What's here

```
SETUP-PROMPT.md         paste this into your AI to set everything up
QUESTIONNAIRE.md        the questions that personalise it
INSTALL.md              the same setup by hand, per tool
METHOD.md               how the method works, the rules, and what it costs
SECURITY.md             what to give an agent access to, and what never to
TRIAL.md                a two-week trial: plan, check-ins, how to judge it
workspace/              copy this; it becomes your Active Work folder
  AGENTS.md             entry point every agent reads first; your answers go here
  CLAUDE.md, GEMINI.md  one line each: tell those tools to read AGENTS.md
  workbench.md          the rules: daily rhythm, file format, approvals
  carry-forward.md      every unresolved item, once
  memory.md             long-term memory
  templates/            the daily file and the side-session log formats
  daily/ work/ outputs/ inputs/
skills/                 aw-start, aw-close, aw-log for Claude Code and Codex
instructions/           paste-in instructions for chat Projects and Cowork
config/                 optional examples: permissions, a scheduled job
checks/                 16 test cases to run before you trust a model or switch tool
long-term-memory/       when memory.md is enough and when it isn't
docs/always-on.md       what Level 3 involves
```

## Is this the right method for you?

Active Work is one way of managing knowledge work with AI agents. There are others, including products that keep the state for you. Don't shoehorn your work into this method: use one that fits the way you work. Whatever you choose, ask where the state lives, whether you can read and correct it, and whether you can take it with you when a better tool arrives.

This one was created by Sean O'Mahony, who has run it every working day since July 2026 across several models and tools. [METHOD.md](METHOD.md) explains how it works and what it costs. It is one person's experience so far; [TRIAL.md](TRIAL.md) is how to find out whether it works for you.

## Licence

Copyright © 2026 Sean O'Mahony. Released under the MIT licence; see [LICENSE](LICENSE).
