# 招聘文档类 Skills 工作流说明

本仓库中与「招聘」相关的 **AI 生成文档** skills 位于 `skills/recruitment/` 下，共两类：

| Skill 目录 | 用途 |
|------------|------|
| [`jd-competency-model/`](../jd-competency-model/SKILL.md) | 从 HR 与用人部门沟通材料生成 **岗位 JD** 与 **胜任力模型**（可只要其一） |
| [`interview-evaluation/`](../interview-evaluation/SKILL.md) | 从面试记录等生成 **面试评价**（多受众；默认内部存档语境） |

## 上下游关系

- **JD + 胜任力** 的产出可被后续 **面评** 引用（对齐岗位语境、术语）。
- **简历筛选、匹配度 datatable、对接招聘平台** 不属于本目录 skills，由产品侧 **MCP + datatable 工作流** 实现；勿在以上 skills 的 `description` 中用「筛简历、匹配度表」作为主要触发词，以免路由混淆。

## 模板优先级（与各自 `SKILL.md` 一致）

1. **对话中用户提供的模板**（粘贴或上传）优先，输出结构以用户为准。
2. 用户未提供时：**参考** [`templates/`](../templates/) 中团队放入的样例，并结合 [`industry-norms.md`](industry-norms.md) 与 **行业** 组织章节与用语；不要求与仓库样例逐节一致。
