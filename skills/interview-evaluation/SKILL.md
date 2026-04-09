---
name: interview-evaluation
description: >-
  Generate interview evaluation records from meeting transcripts, optional JD and resume, and optional
  interviewer notes. Routes by audience and candidate communication intent (advance, hold, or decline;
  defaults to neutral hold if unspecified). Uses qualitative recommendation and one-line strength/risk
  summaries—no numeric hire score. Apply industry writing norms from industry-norms.md. Use when asked
  for 面试评价, 面评, interview feedback, interview assessment, or post-interview evaluation documents.
---

# 面试评价记录生成

## 工作流概览

**两遍写作法**：Pass 1 从原材料提取结构化信号与客观一句话优劣势；Pass 2 按受众与候选人沟通倾向套用模板，并遵守 [industry-norms.md](industry-norms.md) 中对应行业的长度与禁忌。

---

## Step 0：收集输入信息

**必填：**
- 面试 transcript（会议记录/对话文本）

**可选（若用户已提供则跳过询问；否则应主动询问）：**
- **岗位简介（JD）**：「是否有岗位简介（JD）？有请粘贴，便于对齐行业、岗位层级与用语。」
- **候选人简历**：「是否有候选人简历？有请粘贴，便于对照经历与面试陈述（仅写面试可支撑的差异，不臆断）。」
- 面试官 notes（已整理的评估笔记）
- 写作标准模板（结构骨架 / rubric / 风格范本）

**路由参数（需确认；可逐项使用默认值）：**
1. **受众**：候选人 / 面试官存档 / HR 决策支持 / 跨部门同步
2. **候选人沟通倾向**（仅当受众为候选人时）：**推进** / **待定** / **不推进**  
   - **必须先问**：「本次给候选人的沟通倾向是推进、待定还是不推进？」  
   - **用户未回答**：一律使用 [templates.md](templates.md) 中的 **候选人·待定** 模板（中性兜底）。
3. **定性推荐**（面试官存档、HR 用）：推荐进入下一轮 / 待定 / 不推荐（可与用户确认或由材料归纳，须在输出中明示）
4. **行业**：优先从 JD 推断；推断不出则问用户（互联网 / 消费品 / 制造业 / 金融 / 医疗药械 / 咨询 / 其他）  
   - 无法判断时：先按 [industry-norms.md](industry-norms.md) 的 **通用** 节撰写，并提示用户确认行业后必要时再改一版。
5. **岗位层级**：优先从 JD（职级、年限、职责范围）推断为 Junior / Senior / Manager+；不确定则询问用户
6. **输出长度**（可选，可被行业规范覆盖）：简报 / 标准 / 详细；默认与 industry-norms 中该行业建议对齐

快速模式：用户可声明「标准长度、待定候选人信、行业按 JD」等一次性默认值。

---

## Step 1：Pass 1 — 信号提取

**输入融合优先级：**
- 内容：interviewer notes（若有）> transcript；**JD** 定岗位与行业语境；**简历** 用于与面试陈述交叉核对（只记录面试中可印证的差异或一致点）
- 格式：用户模板（若有）> [templates.md](templates.md)
- 行业与长度：**执行前阅读** [industry-norms.md](industry-norms.md) 中与当前行业匹配的章节（含通用节）

**提取目标：**

```
[候选人基本信息]
姓名 / 应聘职位 / 面试日期 / 面试官（据输入提取）

[岗位与语境]
行业（推断或用户指定）/ 岗位层级（推断或用户指定）

[评估维度]（按层级选维度表，见 dimensions.md）
维度名称 | 定性档（显著优秀/良好/达标/需提升/明显不足/证据不足）| 关键行为证据（1–2 条 STAR 片段）

[整体印象]
核心优势（2–3 点，bullet）
主要顾虑或待验证点（1–2 点，若无则注明）

[客观摘要]（替代任何综合打分）
一句话优势：[单句，仅概括有证据的亮点]
一句话风险或待验证点：[单句；无实质风险则写「暂无明显风险」或「某维度证据不足，建议补充考察」等]
```

**仅有 transcript 时：** 全量扫描对话 → 按 dimensions 归类 → 证据不足标「证据不足」。  
**有 notes 时：** 以 notes 的维度判断为骨架，用 transcript 补证据。

---

## Step 2：路由决策

**受众为候选人时**（须已执行 Step 0 对「沟通倾向」的询问与兜底）：

| 用户指定的沟通倾向 | 模板 |
|--------------------|------|
| 推进 | templates.md → 候选人·推进 |
| 待定 | templates.md → 候选人·待定 |
| 不推进 | templates.md → 候选人·不推进 |
| （未指定） | templates.md → 候选人·待定 |

**受众为内部时：**

| 受众 | 模板 |
|------|------|
| 面试官存档 | templates.md → 面试官存档 |
| HR 决策支持 | templates.md → HR 决策支持 |
| 跨部门同步 | templates.md → 跨部门同步 |

用户自定义模板存在时：结构以用户为准，但仍须遵守 industry-norms 的禁忌与长度建议（除非用户声明豁免某条）。

---

## Step 3：Pass 2 — 生成输出

**通用原则：**
- 全文 **不使用** 综合分制（如 1–5 分、X/5）作为录用结论
- 有行为证据再写判断；禁忌与措辞见 industry-norms **通用** 节
- 术语与长度按 industry-norms 中 **当前行业** 小节调整
- 中文输出，除非用户要求英文

**受众原则：**
- **候选人·推进**：肯定语气，亮点先行，可写进入下一阶段；不写内部定性标签、不写分数
- **候选人·待定**：中性，说明评估仍在进行，不夸大期望或否定
- **候选人·不推进**：建设性，聚焦岗位匹配与成长方向，避免人身否定
- **面试官存档**：中性、结构化；含 **定性推荐**（推荐进入下一轮 / 待定 / 不推荐）+ **一句话优势** + **一句话风险或待验证点** + 维度表
- **HR 决策支持**：结论与定性推荐前置；**一句话优势** + **一句话风险或待验证点** 显眼；风险提示分条
- **跨部门同步**：短摘要；结论一句；不按 industry-norms 可适度省略细节，但忌泄密与歧视

---

## 参考文件

- 行业长度、术语、禁忌：[industry-norms.md](industry-norms.md)
- 岗位层级维度表：[dimensions.md](dimensions.md)
- 输出骨架：[templates.md](templates.md)
