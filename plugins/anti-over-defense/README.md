# Anti Over-Defense

用于日常编程和写作的技能插件，基于用户提供的 `Anti-Over-Defense-main.zip` 制作。

- 减少无必要的边界检查、安全审计、SHA 校验、审批和重复验证。
- 避免假设性兜底、过早抽象、无关重构和额外基础设施。
- 复用现有实现及相关检查，完成当前需求后简洁交付。
- 补充防御性写作规则：少用套话、免责声明、重复限制和假想风险清单。

## 使用

将此插件 ZIP 交给 ChatGPT 的 Plugin Creator 保存，再打开返回的插件链接安装。工作区管理员也可通过 GitHub 市场导入；完整步骤见[仓库安装说明](https://github.com/AaronChou313/anti-over-defense#安装到-chatgpt)。

安装后，在需要的任务中选用插件。技能允许匹配任务时隐式调用，也可明确要求“使用 anti-over-defense，直接完成当前任务，仅做必要修改和相关检查”。是否自动触发取决于客户端和当前任务；插件不等于全局强制设置。

## 文件

- `skills/anti-over-defense/SKILL.md`：精简常用规则及新增写作规则。
- `skills/anti-over-defense/references/original-skill.md`：附件中的原始技能，内容未修改，仅在明确需要原文时读取。
- `skills/anti-over-defense/agents/openai.yaml`：技能展示信息及隐式调用策略。

明确要求的安全审查、测试、完整性验证仍照常完成。真实错误、必要权限和项目已有要求应如实处理。
