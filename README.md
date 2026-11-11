# Anti Over-Defense

减少过度工程化、重复检查和防御性长文，直接完成当前任务。

这是已安装 **Anti Over-Defense 1.0.0** 的可分发版本，保留原有技能、参考原文、图标与隐式调用策略。适用于日常编程、排错、重构、技术解释和文档写作；无需服务器、API Key 或外部服务连接。

## 安装到 ChatGPT

### 个人使用：下载插件 ZIP

1. 下载 [anti-over-defense-1.0.0.zip](https://github.com/AaronChou313/anti-over-defense/releases/download/v1.0.0/anti-over-defense-1.0.0.zip)。请使用这个插件包，GitHub 的 **Code → Download ZIP** 是完整仓库源码。
2. 在 ChatGPT 中打开 **Plugin Creator**，上传该 ZIP，并发送：

   > 请将这个 ZIP 保存为我的个人插件，保留其中的技能和配置，并返回插件安装链接。

3. 打开返回的插件链接并安装。在有活动工作区时，Plugin Creator 会保存到工作区；若需个人插件，请先切换至个人空间。

### 工作区使用：从 GitHub 导入

工作区管理员可在 **Admin → Plugins → Add → Import marketplace** 中填写：

| 字段 | 值 |
| --- | --- |
| Source | `https://github.com/AaronChou313/anti-over-defense` |
| Path | 留空 |
| Branch、tag 或 commit | `main`，或使用 `v1.0.0` 固定版本 |

导入后，在插件目录中找到 **Anti Over-Defense** 并安装。此流程需要工作区管理员权限，详见 [OpenAI 官方 GitHub 导入说明](https://learn.chatgpt.com/docs/enterprise/plugin-management)。

GitHub 分发包可通过上述流程安装；它尚未上架 OpenAI 公共插件目录。

## 安装到 Codex

在支持插件的 Codex CLI 中运行：

```sh
codex plugin marketplace add https://github.com/AaronChou313/anti-over-defense.git
codex plugin add anti-over-defense@anti-over-defense
```

安装后重启客户端或开启新会话。也可将本仓库作为项目打开，使用仓库自带的 `.agents/plugins/marketplace.json` 发现插件。格式参见 [OpenAI 官方打包说明](https://developers.openai.com/plugins/build/plugins)。

## 使用

在 ChatGPT 中选择插件或通过 `@` 调用，然后描述任务，例如：

> 使用 Anti Over-Defense，修复这个问题，仅做必要修改和相关检查，简洁交付。

在 Codex 中也可显式调用技能：

```text
使用 $anti-over-defense 完成当前任务，复用现有实现，做相关验证后简洁交付。
```

技能允许在匹配任务时隐式调用，实际触发取决于客户端与任务。它不会变成全局强制设置，也不会绕过权限、上级指令或用户明确要求的安全审查、测试及完整性验证。

## 源码与打包

```text
.agents/plugins/marketplace.json       GitHub / 本地市场入口
plugins/anti-over-defense/
  plugin.json                         Agent Plugins 1.0 清单
  .codex-plugin/plugin.json           原有 Codex 兼容清单
  assets/icon.svg                     原有图标
  skills/anti-over-defense/
    SKILL.md                          常用规则和写作规则
    agents/openai.yaml                展示信息与隐式调用策略
    references/original-skill.md       保留的原始技能全文
```

插件基于用户提供的 `Anti-Over-Defense-main.zip` 制作，此仓库导出当前已安装的适配版本。技能正文和参考原文保持原样，清单补充本仓库地址。

从仓库根目录重新生成同样布局的插件包：

```sh
git archive --format=zip --prefix=anti-over-defense/ \
  --output=anti-over-defense-1.0.0.zip HEAD:plugins/anti-over-defense
```

ZIP 仅含一个插件目录，市场配置不放入插件包。当前仅验证分发结构与包内配置；尚未在新的 ChatGPT 账号中完成导入及调用测试。
