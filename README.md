# IMPROVES AI Prompt

面向产品、项目与文档协作的八项质量规则：让 AI 的输出可以实施、核实、验收和持续维护。

## 快速使用

1. 阅读 [IMPROVES 规则原文](IMPROVES.md)，作为规则的唯一权威来源。
2. 将 [任务提示词](PROMPT.md) 复制到 AI 对话或项目指令中，并填入任务、材料、约束和期望交付物。
3. 按交付物检查结果；没有证据的完成状态应保持“待验证”。

也可以在项目的 `AGENTS.md` 中引用本仓库内的 `IMPROVES.md` 与 `PROMPT.md`。不同工具读取文件的能力不同，应确认文件确实进入当前上下文。

## 内容导航

| 文件 | 用途 |
| --- | --- |
| [IMPROVES.md](IMPROVES.md) | 八项规则及其原始定义 |
| [PROMPT.md](PROMPT.md) | 可直接使用的任务模板与自检要求 |
| [BLUEPRINT.md](BLUEPRINT.md) | PRD 总体编写规范：骨架、跨分区一致性与定稿门槛 |
| [BLUEPRINT_S01.md](BLUEPRINT_S01.md) | PRD 分区功能规格提示词，与 IMPROVES 配合可独立使用 |
| [SCRIPT.md](SCRIPT.md) | 业务内容写作规范与提示词：把台账和零散需求改写成可评审的方案文字，业务规则拆成带唯一编号的原子规则 |
| [TRACE.md](TRACE.md) | 业务案例因果与变更影响分析提示词 |
| [BIBLETREE.md](BIBLETREE.md) | BibleTree 工具的六个结构化任务提示词（改写、证据摘录、影响判定、流程评审、需求拆分、原子规则拆分） |
| [examples/README.md](examples/README.md) | 虚构场景的填写与评审示例 |
| [CONTRIBUTING.md](CONTRIBUTING.md) | 修改、评审与资料边界 |
| [CHANGELOG.md](CHANGELOG.md) | 版本变化 |
| [LICENSE](LICENSE) | MIT 开放授权全文 |

## 作为 Git 子模块使用

```sh
git submodule add git@github.com:sy007-spec/IMPROVES-aiprompt.git IMPROVES-aiprompt
git submodule update --init --recursive
```

使用 HTTPS 的项目可将地址替换为 `https://github.com/sy007-spec/IMPROVES-aiprompt.git`。父库记录子库的具体提交；更新规则时应先评审并推送子库，再更新父库指针。不要复制规则形成多份权威版本。

## 适用范围

适用于需求梳理、产品方案、项目计划、文档审阅和验收准备。根据任务复杂度选择必要的信息，不要求每次输出八个章节。提示词不能证明实现、测试或部署已经完成，实际权限和审批仍由使用项目管理。

本仓库只发布通用方法、提示词与虚构示例，不包含采用该方法的业务项目资料、凭据或生产数据。规则最初从 DHAVEN 工作管理库独立提取；项目专属约束应在使用方维护。

## 授权

本仓库中的规则、提示词、说明和示例采用 [MIT License](LICENSE)，允许商用、修改、分发及再许可；使用或分发实质性内容时保留版权与许可声明。软件与内容按许可中的免责声明提供。
