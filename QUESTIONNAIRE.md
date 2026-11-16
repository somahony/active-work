# Setup questionnaire

These questions make Active Work fit the way you work. Your AI asks them during setup (see [SETUP-PROMPT.md](SETUP-PROMPT.md)). You can also fill this file in yourself and hand it to the AI as your answers.

## Rules for the AI asking

- One question at a time. Offer the default in brackets; "skip" takes the default.
- Use plain words. If an answer is unclear, ask one follow-up, then move on.
- Never ask for a password, token, key or account number. If I offer one, tell me not to and carry on.
- Don't read my email, calendar, chat or tasks to answer these for me unless I say so.
- Ask Part A first. Ask Part B only for sources I say I use. Skip Part E at Level 1.
- At the end, read my answers back in a short list and let me correct them before you write any file. Do this even if I gave you a filled-in answers file. Turn relative dates ("Thursday", "the 28th") into full dates and show them to me.
- If something I list in Part F looks as if it falls inside something I ruled out in Part C, ask me where the line is.

The **Goes to** column says which file each answer fills.

## Part A: you

| # | Question | Default | Goes to |
|---|---|---|---|
| A1 | What should the agent call you? | (none; ask) | `AGENTS.md` About me |
| A2 | In a line or two, what do you do, and what kind of work fills your week? | (none; ask) | `AGENTS.md` About me |
| A3 | What is your home time zone? | the computer's time zone | `AGENTS.md` About me |
| A4 | Do you travel across time zones for work? | rarely | `AGENTS.md` About me |
| A5 | What are your working days and hours? | 09:00–17:30, Monday to Friday | `AGENTS.md` About me |

## Part B: where your work lives

For each source you use, ask the two follow-ups: *Is it already connected to this AI tool?* and *May the agent read it?* Record both answers on that source's line. The agent never sends from any of them without approval. Setup connects nothing: to connect a source later, use your AI tool's own connector or integration settings and its documentation, after checking C4.

| # | Question | Default | Goes to |
|---|---|---|---|
| B1 | Which calendar do you use? | not connected | `AGENTS.md` My sources |
| B2 | Where do your tasks live (a task manager, a tracker, paper)? | none; `carry-forward.md` is the list | `AGENTS.md` My sources |
| B3 | Which email do you use for work? | not connected | `AGENTS.md` My sources |
| B4 | Which chat tool (Slack, Teams, other)? | not connected | `AGENTS.md` My sources |
| B5 | Where do your working documents live (a drive, a folder, a wiki)? | none | `memory.md` Where things live |

## Part C: limits

| # | Question | Default | Goes to |
|---|---|---|---|
| C1 | What must the agent never read, mention or write down? Think of topics (pay, health, legal matters), folders, accounts and people. | credentials only | `AGENTS.md` Never touch |
| C2 | Is any of your work confidential to a fixed group (a board, HR, a client)? Name the category, not the content. | none | `AGENTS.md` Never touch |
| C3 | Is there anything the agent may do without asking first, beyond reading, drafting and writing its own files? | nothing | `AGENTS.md` Standing permissions |
| C4 | Does your employer have a policy on AI tools or on company data on personal machines? If yes, have you checked this setup against it? | not sure: check before connecting any work source | tell the owner; nothing is written |

## Part D: how you like to work

| # | Question | Default | Goes to |
|---|---|---|---|
| D1 | How long should the morning brief be? | under 10 lines | `AGENTS.md` How I like to work |
| D2 | What should come first in it: what's urgent, what's important, or what's quick? | urgent | `AGENTS.md` How I like to work |
| D3 | When the agent is unsure, should it ask you or make its best call and say so? | best call for drafts and files; ask for anything else | `AGENTS.md` How I like to work |
| D4 | Any rules you already know you want, and what each covers? ("Never book before 09:30." "Write in British English.") | none | `memory.md` Standing rules, in your words |
| D5 | Who are the three to five people you work with most, and one line on each that you'd be happy for them to read? | none | `memory.md` People |

## Part E: the setup itself (Level 2)

| # | Question | Default | Goes to |
|---|---|---|---|
| E1 | Where should the Active Work folder go? | `~/ActiveWork` | the install path; the shortcuts; `AGENTS.md` This setup |
| E2 | Do you work on more than one computer? If so, is that folder inside something that syncs (iCloud, Google Drive, Dropbox, OneDrive)? | one computer | `AGENTS.md` This setup |
| E3 | Which AI tools will you use with it? | the one running this setup | which shortcuts are installed; `AGENTS.md` This setup |

## Part F: what's on your plate

This is what makes the first morning brief useful.

| # | Question | Default | Goes to |
|---|---|---|---|
| F1 | List up to ten things you have open right now. A few words each is enough. | none | `carry-forward.md`, one entry each |
| F2 | For each: is the next move yours, the agent's, or someone else's (and if someone else's, have you already asked them)? Is there a due date, or a date to check again? If I'm waiting on someone and gave no date, suggest one a week from today. | lane `my_action`, no date | `carry-forward.md` lane, `next_action`, `target_date`, `review_after` |
| F3 | Which one matters most this week? | the first | that entry's first `history` line: "top priority this week" |

## After the questions

The AI reads the answers back, then shows the plan of files it will write (step 4 of the setup prompt). To change an answer later, edit `AGENTS.md` or `memory.md`: they are plain text and they are yours.
