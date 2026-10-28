# Hermes for beginners: step by step 🤖

[النسخة العربية](README.md)

Hermes is a free, open-source agent by Nous Research. It codes with you, **remembers you** between sessions, **writes its own skills**, and runs on **any model**, free ones included.

This guide is for people who have never coded. Follow the steps in order. About 15–20 minutes.
Not an official Nous Research repo. Hermes itself: https://github.com/NousResearch/hermes-agent

## 0. Open a terminal
- **Windows:** Start, type `PowerShell`, open it. Paste with a right-click.
- **Mac:** `Cmd` + `Space`, type `Terminal`, Enter.

## 1. Install
Windows (PowerShell):
```powershell
iex (irm https://hermes-agent.nousresearch.com/install.ps1)
```
Mac / Linux:
```bash
curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash
```
Then close and reopen the terminal (Mac: or run `source ~/.zshrc`). If your antivirus flags `uv.exe`, it is a known false positive: allow the Hermes folder.

## 2. Check it
```bash
hermes doctor
```

## 3. Pick a model (pick one free option)
```bash
hermes model
```
- **Nous Portal (easiest):** `hermes setup --portal`. Has free models (such as LongCat) with usage limits.
- **OpenRouter:** make a key at https://openrouter.ai (Keys, then Create Key), choose OpenRouter in `hermes model`, paste the key, and pick a model ending in `:free`.
- **Local, offline (Ollama, strong PCs only):** install https://ollama.com and pull a model. Hermes needs **64K context or more**: start it with `OLLAMA_CONTEXT_LENGTH=65536 ollama serve` (PowerShell: `$env:OLLAMA_CONTEXT_LENGTH=65536; ollama serve`). Then in `hermes model` choose **Custom endpoint** with `http://127.0.0.1:11434/v1`.

> ⚠️ An API key is a password. Never share it, screenshot it or push it to GitHub. Hermes stores it in `~/.hermes/.env`.

## 4. First chat
```bash
hermes
```
Ask: `Introduce yourself in two lines`. Inside a chat, `/new` starts fresh, `/model` switches models, and `Ctrl` + `C` exits.

## 5. First code
```bash
mkdir my-first-site
cd my-first-site
hermes
```
Paste the prompt from [examples/first-task.md](examples/first-task.md), approve the file write, then double-click `index.html`.

## 6. Memory and skills
- Memory: `~/.hermes/memories/MEMORY.md` and `USER.md` (Windows: `%LOCALAPPDATA%\hermes\memories`).
- Skills: `~/.hermes/skills/`. Each skill becomes a `/command` in the chat.

## Troubleshooting
| Problem | Fix |
|---|---|
| `hermes` not found | Reopen the terminal, then restart the PC if it is still missing. |
| `401` / invalid key | Run `hermes model` again and paste the full key. |
| Rate limit on a free model | Wait, or switch with `/model`. |
| Context too small | Use a model with 64K+ context. |
| Anything else | `hermes doctor`, then `hermes update`. |

Next: part 2, a team of agents with their own personalities and skills. Follow [@sharkawyai](https://www.instagram.com/sharkawyai).

Hermes Agent © Nous Research, MIT. This guide: [Project Alpha Tech](https://projectalpha.tech), MIT.
