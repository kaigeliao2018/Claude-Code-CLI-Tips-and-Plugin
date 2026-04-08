---
title: Advanced Techniques / 进阶技巧
parent: Tips & Tricks / 技巧
nav_order: 2
---

<div class="lang-en" markdown="1">

# Advanced Techniques

## Custom Slash Commands

Create custom slash commands by adding `.md` files to `.claude/commands/`.

```
.claude/
└── commands/
    ├── review-pr.md     # → /review-pr
    ├── deploy.md        # → /deploy
    └── test-all.md      # → /test-all
```

Example `/review-pr` command:

```markdown
Review the current git diff for:
- Logic errors
- Security vulnerabilities
- Missing error handling
- Code style issues

Provide a summary and list of actionable suggestions.
```

---

## Multi-file Context Strategy

When working across many files, guide Claude explicitly to avoid context drift.

**Tips:**

- Use `/compact` regularly to compress conversation history
- Reference specific files by path in your prompts
- Break large tasks into smaller scoped requests

---

## Agentic (Autonomous) Mode

For long-running tasks, Claude Code can operate autonomously. Use clear, scoped instructions.

**Good prompt structure:**

```
Task: [What to accomplish]
Scope: [Which files/directories to touch]
Constraints: [What NOT to do]
Done when: [Definition of done]
```

**Example:**
```
Task: Add input validation to all API endpoints
Scope: src/routes/ only
Constraints: Do not modify tests or change response schemas
Done when: All routes validate required fields and return 400 on invalid input
```

---

## Using `$ARGUMENTS` in Custom Commands

Pass dynamic arguments to your custom slash commands.

```markdown
<!-- .claude/commands/explain.md -->
Explain the following in simple terms, suitable for a junior developer:

$ARGUMENTS
```

Usage:
```
/explain the difference between async/await and Promises
```

---

## Git Workflow Integration

```bash
# Let Claude generate commit messages
/commit

# Review changes before committing
/review

# Ask Claude to summarize a PR diff
! git diff main...HEAD | claude "summarize these changes as a PR description"
```

---

## Memory System

Claude Code has a file-based memory system at `~/.claude/projects/<project>/memory/`.

- Ask Claude to "remember" preferences, decisions, or context across sessions
- Ask Claude to "forget" outdated information

</div>

<div class="lang-zh" markdown="1">

# 进阶技巧

## 自定义斜杠命令

在 `.claude/commands/` 目录下添加 `.md` 文件即可创建自定义斜杠命令。

```
.claude/
└── commands/
    ├── review-pr.md     # → /review-pr
    ├── deploy.md        # → /deploy
    └── test-all.md      # → /test-all
```

`/review-pr` 命令示例：

```markdown
Review the current git diff for:
- Logic errors
- Security vulnerabilities
- Missing error handling
- Code style issues

Provide a summary and list of actionable suggestions.
```

---

## 多文件上下文策略

跨多个文件工作时，明确引导 Claude 以避免上下文漂移。

**技巧：**

- 定期使用 `/compact` 压缩对话历史
- 在提示中通过路径明确引用文件
- 将大任务拆分为更小的有范围的请求

---

## 智能体（自主）模式

对于长时间运行的任务，Claude Code 可以自主运行。使用清晰、有范围的指令。

**良好的提示结构：**

```
Task: [要完成什么]
Scope: [涉及哪些文件/目录]
Constraints: [不能做什么]
Done when: [完成的定义]
```

**示例：**
```
Task: Add input validation to all API endpoints
Scope: src/routes/ only
Constraints: Do not modify tests or change response schemas
Done when: All routes validate required fields and return 400 on invalid input
```

---

## 在自定义命令中使用 `$ARGUMENTS`

向自定义斜杠命令传递动态参数。

```markdown
<!-- .claude/commands/explain.md -->
Explain the following in simple terms, suitable for a junior developer:

$ARGUMENTS
```

使用：
```
/explain the difference between async/await and Promises
```

---

## Git 工作流集成

```bash
# 让 Claude 生成提交信息
/commit

# 提交前审查变更
/review

# 让 Claude 总结 PR diff
! git diff main...HEAD | claude "summarize these changes as a PR description"
```

---

## 记忆系统

Claude Code 在 `~/.claude/projects/<project>/memory/` 有基于文件的记忆系统。

- 让 Claude "记住" 跨会话的偏好、决策或上下文
- 让 Claude "忘记" 过时信息

</div>
