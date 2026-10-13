# 贡献指南

## 新增技能

一个目录对应一个技能，目录名使用英文小写字母、数字和连字符，并与 `name` 一致：

```text
skills/my-skill/
├── SKILL.md
├── references/   # 按需添加参考资料
└── scripts/      # 按需添加可执行脚本
```

`SKILL.md` 至少包含 YAML frontmatter 和可执行的工作流：

```markdown
---
name: my-skill
description: 描述技能能做什么，以及什么请求应当使用它。
---

# 技能名称

写明目标、必要输入、执行流程与交付标准。
```

将技能需要的资料放在自身目录内，并使用相对路径引用。不要依赖本机绝对路径、其他私有仓库或仓库根目录的共享文件，否则单技能安装后可能无法使用。不要提交密钥、私人素材或未经许可的第三方内容。

如需界面元数据，可添加 `agents/openai.yaml`。有脚本时说明运行依赖；没有脚本时无需创建空 `scripts/` 目录。

新增后同步更新根目录 README 的技能目录和使用示例。

## 本地验证

在仓库根目录检查 CLI 能否发现技能：

```bash
npx skills add . --list
```

在临时目录验证安装，避免覆盖日常使用的技能：

```bash
skill_repo="$PWD"
skill_test_dir="$(mktemp -d)"
cd "$skill_test_dir"
npx skills add "$skill_repo" --skill short-drama-screenwriter --agent codex --copy --yes
```

安装后检查 `.agents/skills/short-drama-screenwriter/` 中的入口和参考文件，确认相对引用可解析。测试其他技能时替换技能名。

短剧编剧技能保留了 [复测场景](../skills/short-drama-screenwriter/tests/scenarios.md)，可在支持的 AI 工具中检查实际创作行为。CLI 能发现或安装技能，不代表已验证生成内容质量。

## 提交流程

从最新 `main` 创建独立的 `feat/`、`fix/` 或 `docs/` 分支，每个分支只处理一个任务。提交使用 Conventional Commits，例如 `feat: add a new writing skill`。完成验证后发起 Pull Request，并说明改动目的及验证方法；维护者确认后再合并。
