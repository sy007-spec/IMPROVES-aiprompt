# 虚构示例：器材服务手册（PATCH）

仅演示格式，不是业务规则或测试通过证据。使用 [PATCH](../../templates/PATCH.md) 与 [FEATURE](../../templates/FEATURE.md)，继承 [CONTRACT](../../CONTRACT.md)。

## 输入材料

虚构来源 s-demo/c-equipment/v1/r1，段落p1：“成员可以收藏器材说明；取消收藏不删除说明。” 段落p2：“管理员可以停用器材借用；停用不删除历史借用记录。” hash在真实调用时由程序计算，本例不伪造。

## 组织输出

Purpose：帮助成员理解器材服务。Audience：成员和服务管理员。Topics：收藏说明 F-01、停用借用 F-02（待编纂）。Connections：同属器材服务，无材料证明两者有业务先后。Holes：停用后已有借用如何处理待确认。

## F-01 完整特性草稿

Frame：成员管理常用说明，不涉及说明内容删除。
Experience：成员收藏说明，之后可取消收藏；如何进入收藏列表未提供，待确认。
Authority：成员可以操作；是否仅本人可见待确认。
Terms：收藏关系与说明内容是不同对象。
Unhappy paths：取消收藏不删除说明；重复收藏和网络失败行为待确认。
References：s-demo/c-equipment/v1/r1 p1，连续依据“取消收藏不删除说明”。
Evaluation：有依据条件为取消收藏后说明仍存在；按钮路径与重复提交测试须补充规则后确定。

状态proposal；未创建课程或发布。检查：主题不强造流程、缺项未补编、引用连续；权限边界未清，暂不具备完整定稿条件。
