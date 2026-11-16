# Install

The quickest way is to paste [SETUP-PROMPT.md](SETUP-PROMPT.md) into your AI and let it do this for you. These are the same steps by hand.

Read [SECURITY.md](SECURITY.md) before giving any agent access to work sources.

## Level 2: an agent that can use files on your computer

Works with Claude Code, Codex, Claude Cowork, Gemini CLI, GrokBot, Muse and anything else that reads a folder.

1. **Get the files.**

   ```bash
   git clone https://github.com/somahony/active-work.git
   ```

2. **Copy the workspace** to where you want it. Use a folder that syncs if you work on more than one computer. Don't copy over an existing folder.

   ```bash
   cp -R active-work/workspace ~/ActiveWork
   ```

3. **Personalise it.** Answer [QUESTIONNAIRE.md](QUESTIONNAIRE.md) and fill in `~/ActiveWork/AGENTS.md`: replace every `[[placeholder]]` and delete lines that don't apply. Put your open items in `carry-forward.md` (the format is in the file) and any rules, people and locations in `memory.md`.

4. **Install the shortcuts for your tool.** If your workspace isn't at `~/ActiveWork`, replace every `~/ActiveWork` in each `SKILL.md` with its path.

   | Tool | What to do |
   |---|---|
   | Claude Code | `mkdir -p ~/.claude/skills && cp -R active-work/skills/aw-start active-work/skills/aw-close active-work/skills/aw-log ~/.claude/skills/` |
   | Codex | `mkdir -p ~/.codex/skills && cp -R active-work/skills/aw-start active-work/skills/aw-close active-work/skills/aw-log ~/.codex/skills/` |
   | Claude Cowork | Point Cowork at the workspace folder and paste `instructions/cowork.md` into its instructions |
   | Gemini CLI and others | No shortcut needed. Open the tool in the workspace folder; it reads `GEMINI.md` or `AGENTS.md`. Say the phrases in full |

   The skills are plain instruction files. They add no process of their own: `workbench.md` in your workspace is the rulebook.

5. **Optional: fewer permission prompts** in Claude Code. See [config/README.md](config/README.md).

6. **Start.** Open your tool in the workspace folder and say **"Start Active Work for today"** (or `/aw-start`). At the end of the day: **"Close out Active Work for today"** (or `/aw-close`). In any other session that does work for you, finish with `/aw-log` so the work reaches the record.

## Level 1: a chat app with no file access

Works with a Project in Claude, ChatGPT, Gemini or similar.

1. Create a Project called "Active Work".
2. Paste the text between the lines in `instructions/chat-project.md` into the Project's instructions. Add a short "About me" from your questionnaire answers underneath it.
3. Fill in `workspace/carry-forward.md` and `workspace/memory.md` and upload both as Project files.
4. Each morning say "Start Active Work for today". At the end of the day say "Close out", then replace the two Project files with the updated versions it gives you.

Level 1 is manual, because the chat can't save files. It teaches the habit, and the files carry straight over to Level 2.

## A model that runs on your own computer

Nothing leaves your machine. Run an agent tool against a local model from the workspace folder, with a clean configuration so the model isn't buried under other tools' instructions. For example, with Codex and Ollama:

```bash
CODEX_HOME=<an empty folder> codex exec --oss --local-provider ollama -m <model> "Start Active Work for today."
```

Small local models may describe what they would do and not do it. Run the checks below before trusting any model.

## Check a model before you rely on it

`checks/handover-cases.md` has 16 made-up situations with what the agent must and must not do. Run them by hand in a fresh chat, or with the script:

```bash
python3 checks/run_checks.py --agent "codex exec --skip-git-repo-check -" --grader "claude -p"
```

Use a different model family to mark the answers from the one being tested.

## Updating

Your workspace is yours and this repository never writes to it. To take a newer `workbench.md`, compare it with yours and copy across what you want. Keep your own changes.

## Uninstalling

Delete the shortcut folders you copied (`aw-start`, `aw-close`, `aw-log`). Your workspace folder is plain files; keep it or delete it.
