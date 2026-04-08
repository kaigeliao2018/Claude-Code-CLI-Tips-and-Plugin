---
title: Basic Usage / 基础用法
parent: Tips & Tricks / 技巧
nav_order: 1
---

# Basic Usage / 基础用法

## Starting Claude Code / 启动 Claude Code

```bash
# Start in the current directory / 在当前目录启动
claude

# Start with an initial prompt / 带初始提示启动
claude "explain this codebase"

# Start in a specific directory / 在指定目录启动
claude --dir /path/to/project
```

---

## Common Commands / 常用命令

### Slash Commands / 斜杠命令

| Command / 命令 | Description / 描述 |
|---|---|
| `/help` | Show all available commands / 显示所有可用命令 |
| `/clear` | Clear conversation history / 清除对话历史 |
| `/compact` | Compact conversation to save context / 压缩对话以节省上下文 |
| `/commit` | Generate and create a git commit / 生成并创建 git 提交 |
| `/review` | Review recent changes / 审查最近变更 |
| `/exit` | Exit Claude Code / 退出 Claude Code |

### Keyboard Shortcuts / 快捷键

| Shortcut / 快捷键 | Action / 功能 |
|---|---|
| `Esc` | Cancel current operation / 取消当前操作 |
| `Ctrl + C` | Interrupt and exit / 中断并退出 |
| `↑ / ↓` | Navigate message history / 浏览历史消息 |

---

## Running Shell Commands / 运行 Shell 命令

Prefix a command with `!` to run it directly in the terminal without asking Claude.

在提示符中以 `!` 开头可直接在终端执行命令，无需经过 Claude。

```
! git status
! npm test
! ls -la
```

---

## Permission Modes / 权限模式

Claude Code has three permission modes / Claude Code 有三种权限模式：

- **Default**: Asks before executing potentially destructive actions / 默认：执行危险操作前询问
- **Auto-approve (`--yes` / `-y`)**: Automatically approves safe tool calls / 自动批准：自动批准安全的工具调用
- **Manual**: Manually approve every tool call / 手动：手动批准每个工具调用

---

## CLAUDE.md — Project-level Instructions / 项目级指令

Create a `CLAUDE.md` file at the root of your project to give Claude persistent context and instructions.

在项目根目录创建 `CLAUDE.md` 文件，为 Claude 提供持久的上下文和指令。

```markdown
# Project: My App

## Tech Stack
- React + TypeScript
- Node.js backend
- PostgreSQL

## Coding Conventions
- Use functional components
- Prefer async/await over callbacks
- All API responses must be typed
```

> Claude reads `CLAUDE.md` automatically at the start of every session.
> Claude 每次会话开始时会自动读取 `CLAUDE.md`。
