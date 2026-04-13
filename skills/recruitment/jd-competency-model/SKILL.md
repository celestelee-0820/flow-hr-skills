---
name: recruitment-jd-competency
description: >-
  Generate a job description (JD) and/or a competency model from HR–hiring-manager communication
  notes or transcripts. Respects user-provided templates in the conversation first; otherwise refers to
  ../templates/ and shared terminology. Use when asked for 岗位JD, 职位描述, 招聘JD, 胜任力模型,
  能力模型, competency model, job description, or role requirements in a recruitment context.
---

# 岗位 JD + 胜任力模型生成

## 工作流概览

根据 **HR 与用人部门沟通材料** 生成成文 **岗位 JD** 与 **胜任力模型**。二者可在同一次输出中分节呈现；用户只要其一则只输出对应部分。

**执行前** 可阅读 [../shared/terminology.md](../shared/terminology.md)（JD 与胜任力的分工）与 [../shared/workflow.md](../shared/workflow.md)（与其他招聘能力边界）。

---

## Step 0：收集输入

**必填（至少其一有实质内容）：**

- HR 与用人部门沟通记录、纪要或对话文本（说明岗位背景、编制、期待、痛点等）

**可选：**

- **本次对话中用户提供的模板**（粘贴或上传）：若有，**章节与字段以用户模板为准**。
- 岗位名称、部门、职级、对标岗位、紧急程度、必须项与加分项等（沟通材料中未写清时再问）。
- **输出范围**：仅 JD / 仅胜任力 / **两者都要**（默认 **两者都要**）。

**模板优先级：**

1. 对话中用户提供的模板 → 严格遵循。
2. 未提供时 → **参考** [../templates/job-description.md](../templates/job-description.md)、[../templates/competency-model.md](../templates/competency-model.md)（若团队已填入内容）；结合沟通材料组织章节，**不要求**与仓库样例完全一致。

---

## Step 1：生成 JD（当用户需要 JD 时）

**原则：**

- 仅基于用户提供的沟通材料做合理结构化；**不虚构** 组织名称、团队规模、未提及的福利或汇报关系。
- 典型章节可包括：岗位概述、工作职责、任职要求（学历/经验/技能）、加分项、工作关系与地点等（按模板与用户习惯调整）。

---

## Step 2：生成胜任力模型（当用户需要胜任力时）

**原则：**

- 维度与行为指标应 **对齐** JD 中的核心职责与挑战（见 [../shared/terminology.md](../shared/terminology.md)）。
- 避免把 JD 里已有的一条条硬性条件原样复制为「胜任力」；胜任力侧重 **可观察行为与能力**。

---

## Step 3：输出格式

- 使用清晰的一级/二级标题区分 **JD** 与 **胜任力模型**（若两者都输出）。
- 中文输出，除非用户要求英文。

---

## 参考文件

- 术语与 JD/胜任力分工：[../shared/terminology.md](../shared/terminology.md)
- 团队参考模板目录：[../templates/](../templates/)
