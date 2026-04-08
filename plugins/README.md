---
title: Plugins / 插件
nav_order: 3
has_children: true
---

<div class="lang-en" markdown="1">

# Plugin Collection

A curated list of plugins, extensions, and tools that enhance Claude Code.

---

## Plugins

| Name | Description | Guide |
|---|---|---|
| **[claude-hud](./claude-hud.md)** | Real-time status bar: context, tools, agents, git | [Install Guide](./claude-hud.md) |

---

## MCP Servers

[Model Context Protocol (MCP)](https://modelcontextprotocol.io) allows Claude Code to connect to external tools and data sources.

### How to add an MCP server

```bash
# Add globally
claude mcp add <name> <command> [args...]

# Add to current project only
claude mcp add --scope project <name> <command> [args...]

# List configured servers
claude mcp list
```

### Recommended MCP Servers

| Name | Description | Install |
|---|---|---|
| **Filesystem** | Read/write local files with extended permissions | `npx @modelcontextprotocol/server-filesystem` |
| **GitHub** | Interact with GitHub repos, issues, PRs | `npx @modelcontextprotocol/server-github` |
| **Postgres** | Query PostgreSQL databases | `npx @modelcontextprotocol/server-postgres` |
| **Brave Search** | Web search via Brave API | `npx @modelcontextprotocol/server-brave-search` |
| **Puppeteer** | Browser automation and scraping | `npx @modelcontextprotocol/server-puppeteer` |
| **Figma** | Read Figma designs and generate code | Via claude.ai integrations |
| **Supabase** | Manage Supabase projects and databases | Via claude.ai integrations |

---

## IDE Extensions

| Extension | Platform | Description |
|---|---|---|
| **Claude Code** (official) | VS Code | Official VS Code integration |
| **Claude Code** (official) | JetBrains | Official JetBrains integration |

---

## Custom Command Packs

Community-contributed `.claude/commands/` packs for common workflows.

> More packs coming soon...

---

## Tools & Utilities

| Tool | Description | Link |
|---|---|---|
| **claude-export** | Export Claude Code conversations | Coming soon |

---

> Want to add a plugin? See [CONTRIBUTING.md](../CONTRIBUTING.md)

</div>

<div class="lang-zh" markdown="1">

# 插件收录

精选提升 Claude Code 体验的插件、扩展与工具列表。

---

## 插件

| 名称 | 描述 | 安装指南 |
|---|---|---|
| **[claude-hud](./claude-hud.md)** | 实时状态栏：上下文、工具、Agent、Git | [安装指南](./claude-hud.md) |

---

## MCP 服务器

[模型上下文协议（MCP）](https://modelcontextprotocol.io) 允许 Claude Code 连接外部工具和数据源。

### 如何添加 MCP 服务器

```bash
# 全局添加
claude mcp add <name> <command> [args...]

# 仅添加到当前项目
claude mcp add --scope project <name> <command> [args...]

# 列出已配置的服务器
claude mcp list
```

### 推荐 MCP 服务器

| 名称 | 描述 | 安装 |
|---|---|---|
| **Filesystem** | 以扩展权限读写本地文件 | `npx @modelcontextprotocol/server-filesystem` |
| **GitHub** | 与 GitHub 仓库、Issues、PR 交互 | `npx @modelcontextprotocol/server-github` |
| **Postgres** | 查询 PostgreSQL 数据库 | `npx @modelcontextprotocol/server-postgres` |
| **Brave Search** | 通过 Brave API 进行网页搜索 | `npx @modelcontextprotocol/server-brave-search` |
| **Puppeteer** | 浏览器自动化与爬取 | `npx @modelcontextprotocol/server-puppeteer` |
| **Figma** | 读取 Figma 设计并生成代码 | 通过 claude.ai 集成 |
| **Supabase** | 管理 Supabase 项目和数据库 | 通过 claude.ai 集成 |

---

## IDE 扩展

| 扩展 | 平台 | 描述 |
|---|---|---|
| **Claude Code**（官方）| VS Code | 官方 VS Code 集成 |
| **Claude Code**（官方）| JetBrains | 官方 JetBrains 集成 |

---

## 自定义命令包

社区贡献的常用工作流 `.claude/commands/` 命令包。

> 更多命令包持续添加中...

---

## 工具与实用程序

| 工具 | 描述 | 链接 |
|---|---|---|
| **claude-export** | 导出 Claude Code 对话 | 即将上线 |

---

> 想添加插件？请查看 [CONTRIBUTING.md](../CONTRIBUTING.md)

</div>
