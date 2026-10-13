# Jueming's Skills

**把创作经验变成 AI 可以执行的工作流。**

这里开源我创作和使用的 Agent Skills，从短剧编剧开始，持续整理内容创作中的方法、模板与参考资料。技能采用 `SKILL.md` 格式，可通过 [skills CLI](https://github.com/vercel-labs/skills) 安装到 Codex、Claude Code、Cursor 等支持的 AI 工具。

## 快速开始

先准备 Node.js（含 npm / npx），再在你的项目目录执行：

```bash
# 选择并安装仓库中的技能
npx skills add juemingai/skills

# 安装前查看技能列表
npx skills add juemingai/skills --list

# 只安装短剧编剧技能
npx skills add juemingai/skills --skill short-drama-screenwriter
```

默认安装到当前项目，按 CLI 提示选择使用的 AI 工具。如需全局安装：

```bash
npx skills add juemingai/skills --skill short-drama-screenwriter --global
```

也可以明确指定安装到 Codex：

```bash
npx skills add juemingai/skills --skill short-drama-screenwriter --agent codex
```

## 技能目录

| 技能 | 能做什么 | 适用场景 |
| --- | --- | --- |
| [short-drama-screenwriter](skills/short-drama-screenwriter/SKILL.md) · 短剧编剧 | 原创短剧、小说/IP 改编、项目案、人物小传、分集大纲、节奏与钩子设计、剧本正文、续写与诊断 | 有一句创意、已有小说梗概，或需要改写和完善短剧剧本 |

## 使用示例

安装后，在 AI 工具中描述任务即可；支持自动发现技能的工具会按任务匹配。Codex 中也可以使用 `$short-drama-screenwriter` 显式调用，其他工具的调用方式以各自界面为准。

### 从创意到项目案

```text
使用 short-drama-screenwriter，帮我做一个原创短剧项目案。
女主是被合伙人顶替作品的珠宝设计师，核心钩子是她重生回签约前一天，
利用前世记忆设局揭穿对方。共 12 集，每集 2 分钟，竖屏免费剧。
请给出人物小传、含结局的故事大纲、全剧节奏表和分集概况。
```

### 把大纲写成剧本

```text
使用 short-drama-screenwriter，根据下面的人物表和分集大纲写第 1 集正文。
每集 2 分钟，竖屏，场景限制在办公室和会议室。
使用场次编号、人物栏、动作和对白格式，结尾保留身份揭示钩子。
（在这里粘贴人物表和大纲）
```

### 诊断已有剧本

```text
使用 short-drama-screenwriter，诊断下面的短剧第 1 集。
保留核心设定，重点改善开场钩子、对白和可拍性，并输出修改后的正文。
（在这里粘贴剧本）
```

如果只提供一句方向，技能会先询问目标产物、主角与核心钩子、集数和时长等关键信息。提供已有正文及设定，可以继续拆分集或续写。

## 技能如何工作

`SKILL.md` 定义任务识别与创作流程；`references/` 提供按需读取的赛道模板、节奏设计、正文格式、设定追踪等资料。所有依赖资料都放在技能自身目录内，单独安装一个技能也能携带完整参考文件。

技能提供创作辅助与自检流程；生成内容仍需由创作者审稿，平台规则以最新要求为准。改编第三方 IP 前，请确保拥有相应授权。

## 仓库结构

```text
.
├── README.md
├── LICENSE
├── skills/
│   └── short-drama-screenwriter/
│       ├── SKILL.md
│       ├── agents/openai.yaml
│       ├── references/
│       └── tests/scenarios.md
└── docs/
    └── contributing.md
```

后续技能放在 `skills/<skill-name>/SKILL.md`；参考资料放在该技能的 `references/`，需要可执行脚本时再添加 `scripts/`。

## 参与贡献

欢迎提交问题、使用反馈和改进建议。新增技能与本地验证方法见 [贡献指南](docs/contributing.md)。

## 许可证

[MIT](LICENSE) © 2026 [Jueming](https://github.com/juemingai)。允许使用、修改和再分发，包括商业用途；分发时需保留版权与许可证声明。许可证适用于本仓库内容，不授予第三方 IP 的改编权。
