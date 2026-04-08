# Hooks Configuration / Hooks 配置

Hooks allow you to run shell commands automatically in response to Claude Code events — without Claude's involvement.

Hooks 允许你在 Claude Code 事件触发时自动运行 Shell 命令，无需经过 Claude。

---

## Where to Configure / 配置位置

Hooks are defined in your Claude Code settings file:

Hooks 在 Claude Code 的设置文件中定义：

- **Global / 全局**: `~/.claude/settings.json`
- **Project / 项目级**: `.claude/settings.json`

---

## Hook Events / Hook 事件

| Event / 事件 | Trigger / 触发时机 |
|---|---|
| `PreToolUse` | Before any tool call / 任意工具调用之前 |
| `PostToolUse` | After any tool call / 任意工具调用之后 |
| `Notification` | When Claude sends a notification / Claude 发送通知时 |
| `Stop` | When Claude finishes responding / Claude 结束响应时 |
| `SubagentStop` | When a subagent finishes / 子智能体结束时 |

---

## Basic Hook Structure / 基本 Hook 结构

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

## Practical Examples / 实用示例

### Auto-format after file writes / 写文件后自动格式化

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

### Auto-run tests after edits / 编辑后自动运行测试

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

### Desktop notification when Claude finishes / Claude 完成时发送桌面通知

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

### Log all tool calls for auditing / 记录所有工具调用以供审计

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

## Environment Variables in Hooks / Hook 中的环境变量

| Variable / 变量 | Description / 描述 |
|---|---|
| `CLAUDE_TOOL_NAME` | Name of the tool being called / 调用的工具名称 |
| `CLAUDE_TOOL_INPUT_COMMAND` | Command for Bash tool / Bash 工具的命令 |
| `CLAUDE_TOOL_INPUT_FILE_PATH` | File path for Write/Edit/Read tools / Write/Edit/Read 工具的文件路径 |
| `CLAUDE_TOOL_RESULT` | Result of the tool call (PostToolUse) / 工具调用结果（PostToolUse）|

---

## Tips / 技巧

- Use `|| true` to prevent hook failures from blocking Claude / 使用 `|| true` 防止 Hook 失败阻塞 Claude
- Keep hooks fast — slow hooks delay every tool call / 保持 Hook 快速执行——慢 Hook 会延迟每次工具调用
- Test hooks independently in terminal before adding to settings / 在添加到设置前在终端独立测试 Hook
