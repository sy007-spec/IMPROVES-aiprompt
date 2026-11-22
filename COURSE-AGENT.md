# 教学课程智能体接入规范 v1

面向课程所有者与受委托的外部智能体。目标是从创建到维护教材和发布有一条可重试、可撤权、可回读的机器入口。平台账号、付费订阅、读者授权、学员记录和 AI 提供商配置由各自的管理流程负责。

## 接入

1. 课程所有者打开目标课堂的「管理 → 大模型智能体访问」。为课程指定短期权限。新课先选定唯一小写课程 ID，创建授权只绑定该 ID。保存时复制一次性令牌，经私有凭据通道交给智能体。
2. 智能体在同一个 HTTPS 课堂站点读取 `GET /api/agent/v1/course-management`。响应给出协议名 `seii.training.course-management`、版本 `1`、操作、范围、字段和是否写入。认证用 `Authorization: Bearer <token>`，令牌不进教材、URL、提示词、Git 或日志。
3. 向同一路径发送 JSON `POST`，请求对象为 `{"operation":"inspect","input":{"course":"example-course"}}`。写入必须带 `Idempotency-Key`，使用 8–100 个字母、数字、点、下划线或连字符。重试传原请求字节和原键。服务在 24 小时内返回原结果，通过 `Idempotency-Replayed: true` 标识重放。同一键换内容返回 409。超过窗口先回读。

| 权限 | 操作与输入 |
| --- | --- |
| `course:read` | `list` 用空对象；`inspect`、`revisions`、`tracks`、`brief`、`links` 用 `course`；`material` 另可传 `businessVersion`、`version`；`source` 传 `version`，可指定 `language` 为 zh 或 en |
| `course:create` | `create` 传预授权 `id`、双语 `title`，可传 `code` 或双语 `files`。省略 `code` 时服务生成，机器响应不会返回访问口令。创建后是草稿 |
| `course:write` | `preview`／`upload` 传 `course`、最新 `baseVersion`、双语 `files` 或既有合并 `markdown`。替换最新从未发布的草稿须加 `replaceLatest:true` 与当前 `baseSha256`。`saveMaterial` 适用于结构化编辑，带 `baseVersion`、`material`、可选 `businessVersion`。已有 Markdown 来源的修订沿用 Markdown 上传。`saveBrief` 带 `baseUpdated`、`zh`、`en`。`addLink`／`removeLink` 用同课程链接 |
| `course:publish` | `publish` 带 `businessVersion`、`version`、`basePublished`、`confirmMarkdown:true`。`publicationScope` 另核对 `baseRevisions`，提交 `revisions` 和 `currentRevision`。`defaultTrack`、`trackVisibility` 管业务版本。`restrictRevision` 限制指定教材修订。以上均带 `course` |
| `course:maintain` | `patchCourse` 按授权更新双语 `title`、`enabled` 或轮换 `code`。`removeRevision` 删除可删除的 `revision`，当前已发布修订须先切换。均带 `course` |

双语 `title` 使用 `{"zh":"示例课程","en":"Example Course"}`。双语文件是 `files` 数组，每项提供 `filename` 与 UTF-8 的 `markdown`，文件第一行声明 `<!-- training:language zh -->` 或 `<!-- training:language en -->`。两种语言须使用相同业务版本与稳定教学页 ID。预检结果中的警告要处理，发布依旧执行教学平台的双语、版本和发布校验。

成功返回课程对象、版本、解析摘要或 `ok`。401 表示令牌无效、过期或撤销，403 表示超范围或只读，404 表示获授权对象或修订不存在，409 表示并发、重放冲突或当前状态不允许，413 表示超体积，429 表示限流。冲突时回读、重新比较，确认更改后使用新请求键。上传前保留稳定页 ID，讲师和学员历史记录按现有版本规则保留。

服务通过请求所在课堂识别租户，所有授权、课程范围和版本校验由服务端执行。令牌只能调用清单中的课程操作。旧的提问和 FAQ 草稿接口保留独立权限。机器接口不能扩大读者范围、继承其他课程的读者授权或修改课堂所有者。课程修改写审计，校验内容来源和发布批准由操作智能体按提示词核对。
