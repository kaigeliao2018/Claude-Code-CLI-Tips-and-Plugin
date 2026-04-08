---
title: Basic Usage / 基础用法
parent: Tips & Tricks / 技巧
nav_order: 1
---

<div class="lang-en" markdown="1">

# Basic Usage

## Starting Claude Code

```bash
# Start in the current directory
claude

# Start with an initial prompt
claude "explain this codebase"

# Start in a specific directory
claude --dir /path/to/project
```

---

## Common Commands

### Slash Commands

| Command | Description |
|---|---|
| `/help` | Show all available commands |
| `/clear` | Clear conversation history |
| `/compact` | Compact conversation to save context |
| `/commit` | Generate and create a git commit |
| `/review` | Review recent changes |
| `/exit` | Exit Claude Code |

### Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Esc` | Cancel current operation |
| `Ctrl + C` | Interrupt and exit |
| `↑ / ↓` | Navigate message history |

---

## Running Shell Commands

Prefix a command with `!` to run it directly in the terminal without asking Claude.

```
! git status
! npm test
! ls -la
```

---

## Permission Modes

Claude Code has three permission modes:

- **Default**: Asks before executing potentially destructive actions
- **Auto-approve (`--yes` / `-y`)**: Automatically approves safe tool calls
- **Manual**: Manually approve every tool call

---

## CLAUDE.md — Project-level Instructions

Create a `CLAUDE.md` file at the root of your project to give Claude persistent context and instructions.

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

</div>

<div class="lang-zh" markdown="1">

# 基础用法

## 启动 Claude Code

```bash
# 在当前目录启动
claude

# 带初始提示启动
claude "explain this codebase"

# 在指定目录启动
claude --dir /path/to/project
```

---

## 常用命令

### 斜杠命令

| 命令 | 描述 |
|---|---|
| `/help` | 显示所有可用命令 |
| `/clear` | 清除对话历史 |
| `/compact` | 压缩对话以节省上下文 |
| `/commit` | 生成并创建 git 提交 |
| `/review` | 审查最近变更 |
| `/exit` | 退出 Claude Code |

### 快捷键

| 快捷键 | 功能 |
|---|---|
| `Esc` | 取消当前操作 |
| `Ctrl + C` | 中断并退出 |
| `↑ / ↓` | 浏览历史消息 |

---

## 运行 Shell 命令

在提示符中以 `!` 开头可直接在终端执行命令，无需经过 Claude。

```
! git status
! npm test
! ls -la
```

---

## 权限模式

Claude Code 有三种权限模式：

- **默认**：执行危险操作前询问
- **自动批准（`--yes` / `-y`）**：自动批准安全的工具调用
- **手动**：手动批准每个工具调用

---

## CLAUDE.md — 项目级指令

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

> Claude 每次会话开始时会自动读取 `CLAUDE.md`。

</div>
