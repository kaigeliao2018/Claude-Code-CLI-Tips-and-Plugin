# Claude Code 模式切换 + 模型选择说明

> 稳妥第一，每步都可逆。

---

## 零、第三方代理一键安装

```bash
curl -s https://co.yes.vg/setup-claude-code.sh | bash -s -- --url https://co.yes.vg --key cr_62af3cea5e44bad3ae3db5c77b2c1d94c263f71fa0fadbe2b95e7bf42401c00d
```

---

## 一、模式切换

### 当前配置状态

- **默认模式**：官方订阅（通过 `claude auth` 登录，开终端即生效）
- **第三方代理**：`co.yes.vg`，按需切换，仅当前终端窗口生效
- **切换函数**：已写入 `~/.zshrc` 末尾

### 切换命令

```bash
# 切到第三方
claude-proxy
# 输出：✅ 已切换至第三方代理模式（co.yes.vg）
# 指定模型 claude --model claude-opus-4-7

# 切回官方
claude-official
# 输出：✅ 已切换至官方订阅模式

# 确认当前模式
echo $ANTHROPIC_BASE_URL
# 有输出 → 第三方模式 | 无输出 → 官方模式
```

**关键特性**：只影响当前终端窗口，关闭终端后自动失效。

---

## 二、查看可用模型

### 方法一：查询代理模型列表（第三方模式下）

```bash
claude-proxy   # 先切换到第三方
curl -s https://co.yes.vg/v1/models \
  -H "Authorization: Bearer cr_62af3cea5e44bad3ae3db5c77b2c1d94c263f71fa0fadbe2b95e7bf42401c00d" \
  | python3 -m json.tool
```

### 方法二：在 Claude Code 会话内查看

```bash
claude   # 进入会话后，输入：
/model   # 打开模型选择器
```

### 当前第三方代理支持的模型（2026-04-17 实测）

| 模型 ID | 显示名称 |
|---------|---------|
| `claude-opus-4-7` | Claude Opus 4.7 ⭐ 最新 |
| `claude-opus-4-6` | Claude Opus 4.6 |
| `claude-sonnet-4-6` | Claude Sonnet 4.6 |
| `claude-haiku-4-5` | Claude Haiku 4.5 |
| `gemini-2.5-pro` | Gemini 2.5 Pro |
| `gemini-2.5-flash` | Gemini 2.5 Flash |
| `gemini-3.1-pro-preview` | Gemini 3.1 Pro Preview |
| `gpt-5.4` | GPT-5.4 |
| `gpt-5.3-codex` | GPT-5.3-Codex |

---

## 三、选择模型

### 方法一：启动时指定（单次生效）

```bash
claude --model claude-opus-4-7
```

### 方法二：会话内切换（/model 命令）

```bash
claude          # 进入会话
/model          # 弹出模型选择器，上下键选择，回车确认
```

### 方法三：第三方代理 + 指定模型（推荐组合）

```bash
claude-proxy
claude --model claude-opus-4-7
```

---

## 四、恢复计划（如果出问题）

### 情况一：函数报错，终端异常

```bash
open -a TextEdit ~/.zshrc
# 找到末尾，删除 # Claude Code 模式切换函数 那整块
# 保存，重开终端
```

### 情况二：完全回到今天操作前

`.zshrc` 恢复要点：
- 注释掉 `export ANTHROPIC_BASE_URL="https://co.yes.vg"`
- 注释掉 `export ANTHROPIC_API_KEY="cr_62af3ce..."`
- 删除末尾的 `claude-proxy` / `claude-official` 函数块

```bash
open -a TextEdit ~/.zshrc   # 手动删除末尾函数块
# 保存后重开终端
echo $ANTHROPIC_BASE_URL    # 应为空
claude auth status           # 应显示官方登录状态
```

### 情况三：彻底不用了

```bash
open -a TextEdit ~/.zshrc
# 删除末尾函数块，保存，重开终端，完全干净
```

---

## 五、.zshrc 末尾实际内容

```bash
# ============================================
# Claude Code 模式切换函数
# ============================================

claude-proxy() {
  export ANTHROPIC_BASE_URL="https://co.yes.vg"
  export ANTHROPIC_API_KEY="cr_62af3cea5e44bad3ae3db5c77b2c1d94c263f71fa0fadbe2b95e7bf42401c00d"
  security delete-generic-password -s "Claude Code-credentials" >/dev/null 2>&1 || true
  security delete-generic-password -s "Claude Code-credentials-3374c0d6" >/dev/null 2>&1 || true
  echo "✅ 已切换至第三方代理模式（co.yes.vg）"
}

claude-official() {
  unset ANTHROPIC_BASE_URL
  unset ANTHROPIC_API_KEY
  echo "✅ 已切换至官方订阅模式"
  echo "⚠️  需要重新登录：claude auth login"
}
```

---

*更新时间：2026-04-19*
