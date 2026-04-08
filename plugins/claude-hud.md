---
title: claude-hud 安装指南
parent: Plugins / 插件
nav_order: 1
---

# Claude Code CLI - Claude-HUD 插件安装指南

## 📋 概述

**Claude-HUD** 是 Claude Code CLI 的一个插件，提供实时状态栏功能，显示：
- 📊 Context 使用情况（百分比）
- 🔧 活跃工具列表
- 🤖 运行中的 agents
- ✅ Todo 进度
- 📁 Git 状态
- ⏱️ 运行时间和速度

**插件来源**：`jarrodwatts/claude-hud`

---

## 🚀 快速安装（4 步）

### 第一步：启动 Claude Code CLI

在终端中运行：
```bash
claude
```

等待看到 `claude>` 提示符后，继续下一步。

---

### 第二步：添加插件市场

```bash
claude> /plugin marketplace add jarrodwatts/claude-hud
```

**预期输出**：插件市场源已添加。

---

### 第三步：安装插件

```bash
claude> /plugin install claude-hud
```

**菜单选择**：
选择 → `Install for you (user scope)` 或按 Enter 默认选择

**预期输出**：
```
✓ Installed claude-hud. Run /reload-plugins to apply.
```

---

### 第四步：重新加载插件

```bash
claude> /reload-plugins
```

**预期输出**：
```
Reloaded: 1 plugin · 2 skills · 5 agents · ...
```

---

### 第五步：配置状态栏

```bash
claude> /claude-hud:setup
```

**菜单选择**：
1. `Yes` - 仅此次确认
2. `Yes, and don't ask again` - **推荐**，后续不再确认
3. `No` - 取消

选择后，系统会：
- 编辑 `.claude/settings.json`
- 配置 `statusLine` 命令
- 提示重启 Claude Code

---

### 第六步：重启 Claude Code

**退出当前会话**：
```bash
exit
```

或按 `Ctrl + D`

**重新启动**：
```bash
claude
```

等待初始化完成。

---

### 第七步：验证安装

```bash
claude> /claude-hud:setup
```

✅ **成功标志**：
- 看到确认提示
- Claude Code 下方出现实时状态栏
- 状态栏显示 Context 百分比、模型名、Git 状态等

---

## ⚙️ 配置与个性化

### 查看配置选项

```bash
/claude-hud:configure
```

### 三种预设风格

| 预设 | 显示内容 | 适用场景 |
|------|---------|--------|
| **Full** | 所有功能全开 | 需要完整监控的复杂工作流 |
| **Essential** | 活动行 + Git 状态 | 日常开发的平衡选择 |
| **Minimal** | 仅模型名 + 上下文进度条 | 追求极简的用户 |

### 配置文件位置

```
~/.claude/plugins/claude-hud/config.json
```

可手动编辑以调整：
- `showModel` - 显示模型名
- `showContextBar` - 显示 Context 进度条
- `showUsage` - 显示 Token 使用
- `showTools` - 显示活跃工具
- `showAgents` - 显示运行中的 agents
- `showTodos` - 显示 Todo 进度
- 等其他选项

---

## 🐧 Linux 用户注意事项

如果在 Linux 上遇到 `/tmp` 跨设备链接错误，运行：

```bash
mkdir -p ~/.cache/tmp && TMPDIR=~/.cache/tmp claude
```

然后重复上述安装步骤。

---

## ❌ 故障排除

### 问题 1：插件未显示在列表中

**解决**：确保已运行 `/plugin marketplace add jarrodwatts/claude-hud`

### 问题 2：安装后状态栏不显示

**解决**：
1. 确保已运行 `/reload-plugins`
2. 确保已运行 `/claude-hud:setup`
3. 重启 Claude Code（`exit` → `claude`）

### 问题 3：配置不生效

**解决**：
1. 检查 `~/.claude/settings.json` 中是否有 `statusLine` 配置
2. 删除该配置后重新运行 `/claude-hud:setup`
3. 重启 Claude Code

### 问题 4：插件市场连接失败

**解决**：
- 检查网络连接
- 稍后重试
- 确保已安装最新版本的 Claude Code CLI

---

## 📝 常用命令速查

```bash
# 启动 Claude Code
claude

# 安装插件
/plugin install claude-hud

# 重新加载所有插件
/reload-plugins

# 设置 HUD 状态栏
/claude-hud:setup

# 配置 HUD 选项（风格、显示内容等）
/claude-hud:configure

# 退出 Claude Code
exit
```

---

## ✅ 验证清单

- [ ] 已启动 Claude Code CLI (`claude`)
- [ ] 已添加插件市场源
- [ ] 已安装 claude-hud 插件
- [ ] 已运行 `/reload-plugins`
- [ ] 已运行 `/claude-hud:setup`
- [ ] 已重启 Claude Code
- [ ] 状态栏成功显示

---

## 📚 更多信息

**官方项目**：https://github.com/jarrodwatts/claude-hud

**Claude Code CLI 文档**：https://github.com/anthropics/claude-code

---

## 📅 更新日期

文档创建日期：2026 年 4 月 8 日

最后更新：2026 年 4 月 8 日

---

**祝你安装顺利！如有问题，请参考故障排除部分。** 🎉
