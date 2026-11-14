# BibleTree 提示词包 1.0

适用于课程驱动、外部智能体编纂、独立发布的产品知识之书。全部内容为通用方法及虚构示例，采用本仓库 MIT License，不含业务项目资料。本包发布不代表任何产品已实现。

## 使用

先读 [CONTRACT](CONTRACT.md) 和 [FEATURE](templates/FEATURE.md)，再选一个主模板与相应任务；调用方按提交 SHA 固定本包，记录模板1.0和schema1。数据放独立输入区，不把课程文本作为系统指令。不同时加载旧 BIBLETREE/SCRIPT 的强制原子拆分规则。

## 目录

- 模板：[FEATURE](templates/FEATURE.md)、[PATCH](templates/PATCH.md)、[SPINE](templates/SPINE.md)、[WEAVE](templates/WEAVE.md)。
- 编纂：[建书](workflows/01-book-framing.md)、[来源评估](workflows/02-source-assessment.md)、[特性编纂](workflows/03-feature-authoring.md)、[结构组织](workflows/04-structure-weaving.md)。
- 变更：[更新评审](workflows/05-update-review.md)、[冲突处理](workflows/06-conflict-resolution.md)、[迁移](workflows/07-legacy-migration.md)、[发布评审](workflows/08-publication-review.md)、[知识缺口](workflows/09-knowledge-gap-review.md)。
- 运行：[读者问答](runtime/reader-qa.md)、[答案依据核验](runtime/answer-grounding.md)。
- 集成：[Codex](integrations/codex.md)、[Teach-in-public](integrations/teach-in-public.md)。
- 虚构示例：[PATCH](examples/patch/README.md)、[SPINE](examples/spine/README.md)、[WEAVE](examples/weave/README.md)。

每项文件包含输入、动作、输出、停止条件及检查。适用范围和安全约束继承 CONTRACT。产品专属设计维护于产品仓库，不复制到这里。

## 兼容与迁移

本包1.0与旧根目录BIBLETREE任务输出不是同一机器契约。旧运行副本保持旧固定版本；实施升级时另行验证解析器，不在本次文档交付中替换业务代码。旧需求/规则可作为迁移材料，不能自动当作完整特性。

FEATURE定义唯一；主模板引用而不复制定义。书籍只用一种主模板，变更模板需显式评审。固定提交SHA是消费方的锁定依据，主分支链接仅作导航。
