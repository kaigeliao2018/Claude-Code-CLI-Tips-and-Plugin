---
title: Hooks Configuration / Hooks 配置
parent: Tips & Tricks / 技巧
nav_order: 3
---

<div class="lang-en" markdown="1">

# Hooks Configuration

Hooks allow you to run shell commands automatically in response to Claude Code events — without Claude's involvement.

---

## Where to Configure

Hooks are defined in your Claude Code settings file:

- **Global**: `~/.claude/settings.json`
- **Project-level**: `.claude/settings.json`

---

## Hook Events

| Event | Trigger |
|---|---|
| `PreToolUse` | Before any tool call |
| `PostToolUse` | After any tool call |
| `Notification` | When Claude sends a notification |
| `Stop` | When Claude finishes responding |
| `SubagentStop` | When a subagent finishes |

---

## Basic Hook Structure

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write",
        "hooks": [
          {
            "type": "command",
            "command": "echo 'File written!'"
          }
        ]
      }
    ]
  }
}
```

---

## Practical Examples

### Auto-format after file writes

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "prettier --write \"$CLAUDE_TOOL_INPUT_FILE_PATH\" 2>/dev/null || true"
          }
        ]
      }
    ]
  }
}
```

### Auto-run tests after edits

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit",
        "hooks": [
          {
            "type": "command",
            "command": "npm test --passWithNoTests 2>&1 | tail -5"
          }
        ]
      }
    ]
  }
}
```

### Desktop notification when Claude finishes

```json
{
  "hooks": {
    "Stop": [
      {
        "matcher": "",
        "hooks": [
          {
            "type": "command",
            "command": "osascript -e 'display notification \"Claude has finished\" with title \"Claude Code\"'"
          }
        ]
      }
    ]
  }
}
```

### Log all Bash calls for auditing

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "echo \"$(date): $CLAUDE_TOOL_INPUT_COMMAND\" >> ~/.claude/bash-audit.log"
          }
        ]
      }
    ]
  }
}
```

---

## Environment Variables in Hooks

| Variable | Description |
|---|---|
| `CLAUDE_TOOL_NAME` | Name of the tool being called |
| `CLAUDE_TOOL_INPUT_COMMAND` | Command for Bash tool |
| `CLAUDE_TOOL_INPUT_FILE_PATH` | File path for Write/Edit/Read tools |
| `CLAUDE_TOOL_RESULT` | Result of the tool call (PostToolUse) |

---

## Tips

- Use `|| true` to prevent hook failures from blocking Claude
- Keep hooks fast — slow hooks delay every tool call
- Test hooks independently in terminal before adding to settings

</div>

<div class="lang-zh" markdown="1">

# Hooks 配置

Hooks 允许你在 Claude Code 事件触发时自动运行 Shell 命令，无需经过 Claude。

---

## 配置位置

Hooks 在 Claude Code 的设置文件中定义：

- **全局**：`~/.claude/settings.json`
- **项目级**：`.claude/settings.json`

---

## Hook 事件

| 事件 | 触发时机 |
|---|---|
| `PreToolUse` | 任意工具调用之前 |
| `PostToolUse` | 任意工具调用之后 |
| `Notification` | Claude 发送通知时 |
| `Stop` | Claude 结束响应时 |
| `SubagentStop` | 子智能体结束时 |

---

## 基本 Hook 结构

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write",
        "hooks": [
          {
            "type": "command",
            "command": "echo 'File written!'"
          }
        ]
      }
    ]
  }
}
```

---

## 实用示例

### 写文件后自动格式化

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "prettier --write \"$CLAUDE_TOOL_INPUT_FILE_PATH\" 2>/dev/null || true"
          }
        ]
      }
    ]
  }
}
```

### 编辑后自动运行测试

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit",
        "hooks": [
          {
            "type": "command",
            "command": "npm test --passWithNoTests 2>&1 | tail -5"
          }
        ]
      }
    ]
  }
}
```

### Claude 完成时发送桌面通知

```json
{
  "hooks": {
    "Stop": [
      {
        "matcher": "",
        "hooks": [
          {
            "type": "command",
            "command": "osascript -e 'display notification \"Claude has finished\" with title \"Claude Code\"'"
          }
        ]
      }
    ]
  }
}
```

### 记录所有 Bash 调用以供审计

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "echo \"$(date): $CLAUDE_TOOL_INPUT_COMMAND\" >> ~/.claude/bash-audit.log"
          }
        ]
      }
    ]
  }
}
```

---

## Hook 中的环境变量

| 变量 | 描述 |
|---|---|
| `CLAUDE_TOOL_NAME` | 调用的工具名称 |
| `CLAUDE_TOOL_INPUT_COMMAND` | Bash 工具的命令 |
| `CLAUDE_TOOL_INPUT_FILE_PATH` | Write/Edit/Read 工具的文件路径 |
| `CLAUDE_TOOL_RESULT` | 工具调用结果（PostToolUse）|

---

## 技巧

- 使用 `|| true` 防止 Hook 失败阻塞 Claude
- 保持 Hook 快速执行——慢 Hook 会延迟每次工具调用
- 在添加到设置前在终端独立测试 Hook

</div>
