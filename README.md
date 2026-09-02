# Skills

面向 Codex 和 Claude Code 的可安装技能集合。每个 `skills/<skill-name>/` 子目录都是一个独立技能，入口文件是 `SKILL.md`。

## 安装到当前项目

先确认当前目录是目标项目根目录。根据使用的工具，选择对应命令：

### Codex

```bash
mkdir -p .agents/skills
cp -R /path/to/skills/skills/. .agents/skills/
```

### Claude Code

```bash
mkdir -p .claude/skills
cp -R /path/to/skills/skills/. .claude/skills/
```

把 `/path/to/skills` 换成这个仓库的实际路径。如果还没有克隆仓库：

```bash
git clone --depth 1 https://github.com/zibyn/skills.git /tmp/zibyn-skills
mkdir -p .agents/skills
cp -R /tmp/zibyn-skills/skills/. .agents/skills/  # Codex
mkdir -p .claude/skills
cp -R /tmp/zibyn-skills/skills/. .claude/skills/  # Claude Code
```

上面的复制命令可以重复执行；同名技能会以本仓库版本覆盖。

## 只安装一个技能

```bash
mkdir -p .agents/skills/<skill-name>
cp -R /path/to/skills/skills/<skill-name>/. .agents/skills/<skill-name>/
```

Claude Code 只需把 `.agents/skills` 换成 `.claude/skills`。

## 可用技能

| 名称 | 用途 |
| --- | --- |
| `code-review` | 审查代码改动是否符合规范和需求 |
| `codebase-design` | 设计模块接口，提升可理解性和可测试性 |
| `domain-modeling` | 明确领域术语、关系和设计决策 |
| `grill-with-docs` | 通过提问澄清方案，并同步记录文档 |
| `grilling` | 系统审视计划、设计或想法 |
| `handoff` | 整理当前工作上下文，生成交接文档 |
| `implement` | 根据需求或规格说明实现功能 |
| `improve-codebase-architecture` | 发现架构问题并提出改进方案 |
| `prototype` | 用一次性原型验证逻辑或界面方案 |
| `research` | 基于一手资料调查问题并记录结论 |
| `tdd` | 通过先写测试再实现功能 |
| `to-spec` | 将当前讨论整理成 Markdown 规格说明 |

安装后，直接告诉代理要使用的技能，例如：

```text
使用 code-review skill 审查当前分支相对 main 的改动。
```

`implement`、`to-spec`、`handoff`、`grill-with-docs` 和 `improve-codebase-architecture` 默认不会自动触发，需要明确点名。

## 目录结构

```text
skills/
├── <skill-name>/
│   ├── SKILL.md           # 技能说明和执行规则
│   ├── agents/openai.yaml # 可选：Codex 显示信息
│   └── 其他参考文件        # 可选
```

安装完成后检查目标目录中是否存在对应的 `SKILL.md`，然后重新打开代理会话即可。
