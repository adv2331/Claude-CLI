# Claude CLI

A custom Claude CLI with file operation permissions and per-message token tracking.

## Features

- 💬 **Persistent conversation** — full message history kept in-session
- 📁 **File tools** — read, create, edit, delete, list directory
- 🔐 **Permission prompts** — every write/delete asks for your approval before executing
- 📊 **Token tracking** — input/output/total tokens shown after each response, session total on exit

## Setup

```bash
npm install
npm run build
export ANTHROPIC_API_KEY=sk-ant-...
node dist/index.js
```

Or run without building:
```bash
npx ts-node src/index.ts
```

## Commands

| Command    | Description               |
|------------|---------------------------|
| `/clear`   | Clear conversation history |
| `/history` | Show conversation history  |
| `/quit`    | Exit (shows session totals)|

## File Tools Claude Can Use

| Tool            | Permission Required |
|-----------------|---------------------|
| `read_file`     | No — reads only     |
| `list_directory`| No — reads only     |
| `create_file`   | ✅ Yes              |
| `edit_file`     | ✅ Yes              |
| `delete_file`   | ✅ Yes              |

## Token Display

After each response:
```
📊 Tokens — in: 1,234  out: 456  total: 1,690
```

On exit:
```
📈 Session total (5 exchanges) — in: 8,234  out: 2,100  total: 10,334
```
