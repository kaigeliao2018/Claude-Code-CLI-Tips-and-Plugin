# Plugin Collection / 插件收录

A curated list of plugins, extensions, and tools that enhance Claude Code.

精选提升 Claude Code 体验的插件、扩展与工具列表。

---

## MCP Servers / MCP 服务器

[Model Context Protocol (MCP)](https://modelcontextprotocol.io) allows Claude Code to connect to external tools and data sources.

[模型上下文协议（MCP）](https://modelcontextprotocol.io) 允许 Claude Code 连接外部工具和数据源。

---

## Plugins / 插件

| Name / 名称 | Description / 描述 | Guide / 安装指南 |
|---|---|---|
| **[claude-hud](./claude-hud.md)** | Real-time status bar (context, tools, agents, git) / 实时状态栏（上下文、工具、Agent、Git） | [安装指南](./claude-hud.md) |

---

## MCP Servers / MCP 服务器

### How to add an MCP server / 如何添加 MCP 服务器

```bash
# Add globally / 全局添加
claude mcp add <name> <command> [args...]

# Add to current project only / 仅添加到当前项目
claude mcp add --scope project <name> <command> [args...]

# List configured servers / 列出已配置的服务器
claude mcp list
```

### Recommended MCP Servers / 推荐 MCP 服务器

| Name / 名称 | Description / 描述 | Install / 安装 |
|---|---|---|
| **Filesystem** | Read/write local files with extended permissions / 以扩展权限读写本地文件 | `npx @modelcontextprotocol/server-filesystem` |
| **GitHub** | Interact with GitHub repos, issues, PRs / 与 GitHub 仓库、Issues、PR 交互 | `npx @modelcontextprotocol/server-github` |
| **Postgres** | Query PostgreSQL databases / 查询 PostgreSQL 数据库 | `npx @modelcontextprotocol/server-postgres` |
| **Brave Search** | Web search via Brave API / 通过 Brave API 进行网页搜索 | `npx @modelcontextprotocol/server-brave-search` |
| **Puppeteer** | Browser automation and scraping / 浏览器自动化与爬取 | `npx @modelcontextprotocol/server-puppeteer` |
| **Figma** | Read Figma designs and generate code / 读取 Figma 设计并生成代码 | Via claude.ai integrations |
| **Supabase** | Manage Supabase projects and databases / 管理 Supabase 项目和数据库 | Via claude.ai integrations |

---

## IDE Extensions / IDE 扩展

| Extension / 扩展 | Platform / 平台 | Description / 描述 |
|---|---|---|
| **Claude Code** (official) | VS Code | Official VS Code integration / 官方 VS Code 集成 |
| **Claude Code** (official) | JetBrains | Official JetBrains integration / 官方 JetBrains 集成 |

---

## Status Line / 状态栏

### claude-hud

Display Claude Code session info in your terminal status line (Starship, Oh My Zsh, etc.)

在终端状态栏（Starship、Oh My Zsh 等）显示 Claude Code 会话信息。

```bash
# Configure via Claude Code skill / 通过 Claude Code skill 配置
/claude-hud:setup
```

---

## Custom Command Packs / 自定义命令包

Community-contributed `.claude/commands/` packs for common workflows.

社区贡献的常用工作流 `.claude/commands/` 命令包。

> More packs coming soon / 更多命令包持续添加中...

---

## Tools & Utilities / 工具与实用程序

| Tool / 工具 | Description / 描述 | Link / 链接 |
|---|---|---|
| **claude-export** | Export Claude Code conversations / 导出 Claude Code 对话 | Coming soon |

---

> Want to add a plugin? See [CONTRIBUTING.md](../CONTRIBUTING.md)
>
> 想添加插件？请查看 [CONTRIBUTING.md](../CONTRIBUTING.md)
