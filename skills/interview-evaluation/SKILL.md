---
name: interview-evaluation
description: >-
  Generate interview evaluation records from meeting transcripts, optional JD, resume, and
  interviewer notes. Routes by candidate level, interviewer round, industry, and audience.
  Use when asked for 面试评价, 面评, interview feedback, interview assessment, or
  post-interview evaluation documents.
---

# 面试评价记录生成

## Step 0：输入收集 & 路由参数确认

**① 前置面试记录检查**  
搜索 `zoom-docs/` 中是否有同名候选人的既往面试记录。  
- 有 → 作为 Pass 1 前序上下文，标注「前序面试结论」  
- 无 → 询问「是否有前期面试记录可参考？」（可选，跳过不影响流程）

**② 必填输入**  
面试 transcript（会议记录 / 对话文本）

**③ 可选输入**（有则用，无则按需询问）  
岗位 JD、候选人简历、面试官 notes、用户自定义模板

**④ 路由参数**（从输入推断；推断不出则询问）

| 参数 | 取值 | 推断失败时 |
|------|------|-----------|
| 候选人层级 | Junior / Senior / Manager+ | 从 JD 或职位名称推断；不确定则问 |
| 面试官角色 | 一面（直属主管）/ 二面（总监）/ 三面（GM） | 用户提供；无则默认一面 |
| 行业 | 互联网 / 消费品 / 制造业 / 金融 / 医疗 / 咨询 | 从 JD 推断；不确定则先用 `industry-norms/common.md` |
| 受众 | 候选人 / 面试官存档 / HR 决策支持 / 跨部门同步 | 必须确认 |
| 候选人沟通倾向 | 推进 / 待定 / 不推进（受众=候选人时） | 必须先问；无回答→默认「待定」 |

---

## Step 1：Pass 1 — 按路由加载文件 & 提取信号

**加载规则（不多读）：**

| 路由结果 | 加载文件 |
|---------|---------|
| 候选人层级 | `dimensions/junior.md` 或 `senior.md` 或 `manager.md`（三选一） |
| 行业附加维度（若行业已知） | `dimensions/industry-extras.md` |
| 合规规范（必读） | `industry-norms/common.md` |
| 行业细则（若行业已知） | `industry-norms/<行业>.md`（六选一） |

**面试官角色 → 考察层激活规则：**  
每个维度文件含「考察层」列（深度 / 广度 / 高度），按面试官角色筛选重点：

- 一面（直属主管）→ 聚焦**深度**标签维度，挖具体执行细节，要求 STAR 证据
- 二面（总监）→ 聚焦**广度**标签维度，考察思维框架与方案设计
- 三面（GM）→ 聚焦**高度**标签维度，考察软实力、潜力与战略视野
- Manager+ 候选人 → 一面起即含广度维度（自动激活一个层级上的标签）

**若用户提供自定义模板** → 结构以用户模板为准；仍须遵守 `industry-norms/common.md` 合规禁忌。

**提取格式：**

```
[候选人基本信息] 姓名 / 应聘职位 / 面试日期 / 面试官 / 面试轮次
[前序面试结论]（若有）简述既往轮次关键结论与待验证点
[评估维度] 维度 | 考察层 | 档位 | 行为证据（STAR）
[一句话优势] ...
[一句话风险或待验证点] ...
```

---

## Step 2：Pass 2 — 按受众加载模板 & 生成输出

**模板加载（一次只读一个文件）：**

| 受众 + 沟通倾向 | 加载文件 |
|----------------|---------|
| 候选人 · 推进 | `templates/candidate-advance.md` |
| 候选人 · 待定（含默认兜底） | `templates/candidate-hold.md` |
| 候选人 · 不推进 | `templates/candidate-decline.md` |
| 面试官存档 | `templates/internal-archive.md` |
| HR 决策支持 | `templates/hr-decision.md` |
| 跨部门同步 | `templates/cross-functional.md` |

**通用原则：**
- 全文不使用综合分制（1–5 分、X/5）作为录用结论
- 有行为证据再写判断；无证据标「证据不足」
- 中文输出，除非用户要求英文
