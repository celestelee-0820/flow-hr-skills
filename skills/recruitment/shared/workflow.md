# 面试评价 Skill 工作流说明

本仓库中与「招聘」相关的 **AI 生成文档** skill 仅保留 **面试评价**：

| Skill 目录 | 用途 |
|------------|------|
| [`interview-evaluation/`](../interview-evaluation/SKILL.md) | 从面试记录等生成 **面试评价**（多受众；默认内部存档语境） |

## 边界

- **简历筛选、匹配度 datatable、对接招聘平台** 不属于本 skill，由产品侧 **MCP + datatable 工作流** 实现；勿在本 skill 的 `description` 中用「筛简历、匹配度表」作为主要触发词，以免路由混淆。

## 模板优先级（与 `interview-evaluation/SKILL.md` 一致）

1. **对话中用户提供的模板**（粘贴或上传）优先，输出结构以用户为准。
2. 用户未提供时：**参考** [`templates/interview-evaluation.md`](../templates/interview-evaluation.md)（若团队已填入内容）与 [`interview-evaluation/templates.md`](../interview-evaluation/templates.md)，并结合 [`industry-norms.md`](industry-norms.md) 与 **行业** 组织章节与用语；不要求与仓库样例逐节一致。
