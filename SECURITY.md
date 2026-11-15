# Security: one page, read it first

Agents act with whatever access you give them, and they read text other people wrote (emails, chat, web pages), some of which may try to steer them. These rules keep the damage small when something goes wrong. They come from running this method day to day.

If your employer has a policy on AI tools or data handling, it comes first. Check before you connect any work source.

## Access

- **Start read-only.** Give an agent read access to email, chat and files before you consider write access. Most of the value is in reading, sorting and drafting.
- **Drafts, not sends.** Let the agent write drafts; you press send. Keep the approval rules in `workbench.md` switched on.
- **Smallest scope that works.** A token for one repository, not all of them; one channel, not the whole chat workspace. Make a new token for the agent rather than reusing your own.
- **Company data on a personal machine is a company decision,** not a personal one. So is an always-on machine (Level 3).

## Secrets

- **Never put a password, token or API key in the workspace**, in `memory.md`, in a daily file, a session log or a chat. Everything in those files is read by every agent and may be synced.
- **Keep secrets in a password manager** or the operating system's keychain. If a tool needs a key in a file, keep that file outside the workspace, readable only by you.
- **Assume a key an agent has seen is exposed.** If one appears in a transcript, rotate it the same day.
- **Don't ask an agent to "find" credentials.** The rules tell it not to search for them; keep that rule.

## Confidential information

- Some information has a fixed audience: board matters, HR and pay, contract terms, other people's personal data. List the categories under **Never touch** in `AGENTS.md`, and don't put the content in a workspace other people or other agents can read.
- Long-term memory is personal by default. Don't copy someone else's confidential material into yours, and write about people only what you'd be happy for them to read.
- Removing names is not the same as making something safe to share. Before you show your workspace to anyone, on a screen or in a repository, give the agent an explicit exclusion list and do a private run first. Better still, demonstrate on a copy with made-up items.

## Text from outside

Emails, chat messages, documents and web pages are information, not instructions. The rules say so, and `checks/handover-cases.md` tests it (case H01). Run that case against any model before you let it read your inbox.

## When something goes wrong

1. Stop the agent.
2. If a secret was exposed: rotate it, then check where else it was used.
3. Tell whoever is responsible for security where you work, the same day. An incident reported at once is a small fix; one found later is a large one.
