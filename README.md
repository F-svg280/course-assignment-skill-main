# course-assignment-skill

> 一个基于 WorkBuddy 项目级 Skill 机制的 AI 概念学习资料生成项目：把"如何讲清一个 AI 概念"的方法论沉淀为 Skill，由 Agent 按需调用，批量产出结构化、可追溯的学习资料。

## 1. 仓库用途

本仓库是一个**课程作业性质的 Skill 开发与使用项目**，核心目标是实践"AI 概念 → Skill 范式"的完整闭环：

1. **定义技能**：将"生成结构化概念学习资料"的方法论（八模块结构、资料来源规范、自检清单）写成标准 `SKILL.md`；
2. **调用技能**：在 WorkBuddy 中让 Agent 加载该 Skill，输入任意 AI 概念（如 Agent、大模型的上下文、Skill 本身），自动产出学习资料；
3. **沉淀资产**：产出物统一落盘到 `learning-materials/`，形成个人 AI 概念知识库；
4. **人机协作**：每份资料保留"AI 生成 + 人工核查/修改"的完整记录，实践负责任的内容生产流程。

## 2. 项目结构

```
course-assignment-skill-main/
├── README.md                  ← 本文件
└── .workbuddy/
    └── skills/
        └── concept-learning-generator/     ← 本项目唯一的 Skill
            ├── SKILL.md                    ← 技能定义（八模块方法论）
            └── learning-materials/         ← 学习资料输出目录
                ├── agent.html              ← 概念：Agent（智能体）
                ├── llm-context.html        ← 概念：大模型的上下文
                ├── skill.html              ← 概念：Skill（Agent Skills）
                └── concept-relationship.html ← 关系篇：三者关系
```

## 3. Skill 说明与存放路径

- **技能名称**：`concept-learning-generator`（概念学习资料生成）
- **存放路径**：`.workbuddy/skills/concept-learning-generator/SKILL.md`
- **功能**：接收任意一个 AI 概念作为输入，输出包含八个固定模块的结构化学习资料：
  ① 概念个人解释（比喻+对应关系）→ ② 核心机制组成（含流程图）→ ③ 应用场景（真实产品+反例）→ ④ 易混淆边界（≥2 组对比+判断口诀）→ ⑤ 参考来源（≥4 条、含原始论文/官方文档、禁止编造链接）→ ⑥ 学习目标（与题目互相引用）→ ⑦ 核心思考题 → ⑧ 自测问题（带答案、难度梯度）
- **质量约定**：交付前按 SKILL.md 内置自检清单逐项核验；产出默认落盘至 `learning-materials/`

## 4. 在 WorkBuddy 中调用本 Skill

**方式一：自然语言触发（常用）**

在 WorkBuddy 对话中直接下指令，带上技能路径与概念名，例如：

```text
调用 .workbuddy/skills/concept-learning-generator 的skill，
学习概念RAG，输出完整html，保存到 learning-materials/rag.html
```

Agent 会自动读取 SKILL.md → 按八模块生成 → 落盘到指定位置。

**方式二：先读定义再执行（更严格）**

```text
读取 .workbuddy/skills/concept-learning-generator/SKILL.md，
严格按其中的输入要求、生成步骤与自检清单执行，
输入概念：Fine-tuning，输出保存为 learning-materials/fine-tuning.html
```

**调用要点**

- 指令中包含**概念名**、**输出格式**（html/md）与**保存文件名**三项，Agent 可完整执行；
- 项目约定所有读写仅限本仓库目录（D 盘），不在 C 盘产生文件；
- 生成后可追问"按 SKILL.md 自检清单复核"，Agent 会逐项报告核验结果。

## 5. 已生成学习资料清单

| # | 文件 | 主题 | 形式 | 要点 | 生成日期 |
|---|---|---|---|---|---|
| 1 | `learning-materials/agent.html` | Agent（智能体） | 单文件 HTML（浅色主题） | ReAct 循环图（内联 SVG）、四组件表、易混三组对比、7 条来源 | 2026-09-06 |
| 2 | `learning-materials/llm-context.html` | 大模型的上下文 | 单文件 HTML | 上下文分层 SVG 图、lost in the middle、写/选/压/隔四策略、7 条来源 | 2026-09-06 |
| 3 | `learning-materials/skill.html` | Skill（Agent Skills） | 单文件 HTML | 渐进披露三级 SVG、Skill/Tool/MCP 边界、供应链安全思考题、7 条来源 | 2026-09-06 |
| 4 | `learning-materials/concept-relationship.html` | 三概念关系篇 | 单文件 HTML（Mermaid） | 4 张 Mermaid 图（总览/膨胀自救/沉淀循环/时序）、两个重点专章、速查表 | 2026-09-06 |

> 注：`concept-relationship.html` 的 Mermaid 图经 CDN（jsDelivr）加载，需联网打开才能渲染流程图；其余图形均为内联 SVG，离线可看。

## 6. 人工核查与手动修改记录

以下为本人（仓库所有者）对 AI 生成内容的人工介入记录，按介入环节分类：

### 6.1 已完成的人工决策与修改

| 环节 | 我的介入 | 性质 |
|---|---|---|
| **技能方向定夺** | 否决 AI 第一版"非遗纪录片概念图"SKILL.md 主题，人工指定改为"概念学习资料生成"技能，并亲自给出输出模块清单（8 模块）与技能章节框架（适用场景/输入/生成步骤/输出结构/资料来源要求/自检项） | 方向否决 + 需求重定义 |
| **目录结构修正** | 人工指定技能存放路径为 `.workbuddy/skills/concept-learning-generator/`（含 `learning-materials/` 输出子目录），纠正 AI 最初建错位置的目录，并清理误建副本；明确约束"所有读写仅在 D 盘，不碰 C 盘" | 结构决策 + 约束约定 |
| **产出规格控制** | 每份资料的输出格式（HTML）与文件名（agent / llm-context / skill / concept-relationship）均由人工指定，覆盖技能默认的 Markdown 命名；关系篇（第 4 份）由人工提出选题与两个论述重点 | 格式与选题决策 |
| **仓库门面** | 本 README 的内容框架（5 项要求清单）由人工拟定 | 文档决策 |

### 6.2 已知未核查项（诚实声明）

| 待核查项 | 说明 |
|---|---|
| 参考来源链接 | 各资料引用的 arXiv 编号、官方文档 URL 为 AI 凭既有知识给出，**尚未逐条打开验证可达性与内容匹配度** |
| 正文技术论点 | 文中的机制描述（如 KV Cache、RoPE 外推、渐进披露细节）未经人工比对原始论文逐条校对 |
| 渲染验证 | Mermaid 图未在完全离线环境验证；HTML 仅在 WorkBuddy 内置预览中查看 |

### 6.3 后续核查计划

- [ ] 逐条打开第 5 节清单所列 4 份资料的参考来源链接，剔除失效项
- [ ] 抽查每份资料"易混淆边界"与"自测答案"的技术准确性
- [ ] 在离线环境验证 HTML 渲染，必要时将 Mermaid 图替换为内联 SVG

---

*本项目为课程作业实践。AI 生成内容由仓库所有者按上述记录承担最终审校责任。*
