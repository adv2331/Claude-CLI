# Claude CLI v1.0.1
(ANTHROPIC PLEASE DON'T SUE ME😭😭😭)

A custom Claude CLI with file operation permissions, per-message token tracking, and persistent memory.

## Installation

```bash
# 1. Extract the zip
unzip claude-cli.zip
cd claude-cli

# 2. Install (automatically builds too)
npm install

# 3. Set your API key
export ANTHROPIC_API_KEY=sk-ant-...

# 4. Run
node dist/index.js
```

Optionally add to your shell profile so the key persists:
```bash
echo 'export ANTHROPIC_API_KEY=sk-ant-...' >> ~/.bashrc  # or ~/.zshrc
```

## Features

- 💬 **Persistent conversation** — full message history kept in-session
- 📁 **File tools** — read, create, edit, delete, list directory
- 🔐 **Permission prompts** — every write/delete asks for your approval before executing
- 📊 **Token tracking** — input/output/total tokens shown after each response, session total on exit
- 🧠 **Persistent memory** — stored in `~/.claude-cli/memory.md`, loaded at startup each session

## Commands

| Command    | Description                        |
|------------|------------------------------------|
| `/clear`   | Clear conversation history         |
| `/history` | Show conversation history          |
| `/memory`  | Print current memory file contents |
| `/quit`    | Exit (shows session totals)        |

## Memory

Memory lives at `~/.claude-cli/memory.md` and is created automatically on first run.
Claude reads it at the start of every session and can update it mid-conversation.

You can tell Claude things like:
- *"Remember that I prefer TypeScript over JavaScript"*
- *"My name is Cal, remember that"*
- *"Note that this project uses ESM modules"*

Claude will use `append_memory` or `update_memory` to save it for future sessions.
You can also edit `~/.claude-cli/memory.md` directly in any text editor.

## File Tools

| Tool             | Permission Required |
|------------------|---------------------|
| `read_file`      | No — reads only     |
| `list_directory` | No — reads only     |
| `read_memory`    | No — reads only     |
| `create_file`    | ✅ Yes              |
| `edit_file`      | ✅ Yes              |
| `delete_file`    | ✅ Yes              |
| `update_memory`  | No — auto           |
| `append_memory`  | No — auto           |


