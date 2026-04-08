---
title: Advanced Techniques / 进阶技巧
parent: Tips & Tricks / 技巧
nav_order: 2
---

# Advanced Techniques / 进阶技巧

## Custom Slash Commands / 自定义斜杠命令

You can create custom slash commands by adding `.md` files to `.claude/commands/`.

在 `.claude/commands/` 目录下添加 `.md` 文件即可创建自定义斜杠命令。

```
.claude/
└── commands/
    ├── review-pr.md     # → /review-pr
    ├── deploy.md        # → /deploy
    └── test-all.md      # → /test-all
```

Example `/review-pr` command / `/review-pr` 命令示例：

```markdown
Review the current git diff for:
- Logic errors
- Security vulnerabilities
- Missing error handling
- Code style issues

Provide a summary and list of actionable suggestions.
```

---

## Multi-file Context Strategy / 多文件上下文策略

When working across many files, guide Claude explicitly to avoid context drift.

跨多个文件工作时，明确引导 Claude 以避免上下文漂移。

**Tips / 技巧：**

- Use `/compact` regularly to compress conversation history / 定期使用 `/compact` 压缩对话历史
- Reference specific files by path in your prompts / 在提示中通过路径明确引用文件
- Break large tasks into smaller scoped requests / 将大任务拆分为更小的有范围的请求

---

## Agentic (Autonomous) Mode / 智能体（自主）模式

For long-running tasks, Claude Code can operate autonomously. Use clear, scoped instructions.

对于长时间运行的任务，Claude Code 可以自主运行。使用清晰、有范围的指令。

**Good prompt structure / 良好的提示结构：**

```
Task: [What to accomplish]
Scope: [Which files/directories to touch]
Constraints: [What NOT to do]
Done when: [Definition of done]
```

**Example / 示例：**
```
Task: Add input validation to all API endpoints
Scope: src/routes/ only
Constraints: Do not modify tests or change response schemas
Done when: All routes validate required fields and return 400 on invalid input
```

---

## Using `$ARGUMENTS` in Custom Commands / 在自定义命令中使用 `$ARGUMENTS`

Pass dynamic arguments to your custom slash commands.

向自定义斜杠命令传递动态参数。

```markdown
<!-- .claude/commands/explain.md -->
Explain the following in simple terms, suitable for a junior developer:

$ARGUMENTS
```

Usage / 使用：
```
/explain the difference between async/await and Promises
```

---

## Git Workflow Integration / Git 工作流集成

```bash
# Let Claude generate commit messages / 让 Claude 生成提交信息
/commit

# Review changes before committing / 提交前审查变更
/review

# Ask Claude to summarize a PR diff / 让 Claude 总结 PR diff
! git diff main...HEAD | claude "summarize these changes as a PR description"
```

---

## Memory System / 记忆系统

Claude Code has a file-based memory system at `~/.claude/projects/<project>/memory/`.

Claude Code 在 `~/.claude/projects/<project>/memory/` 有基于文件的记忆系统。

- Ask Claude to "remember" preferences, decisions, or context across sessions
- Ask Claude to "forget" outdated information
- 让 Claude "记住" 跨会话的偏好、决策或上下文
- 让 Claude "忘记" 过时信息
