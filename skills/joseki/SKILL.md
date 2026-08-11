---
name: joseki
description: "Manual trigger only (/joseki). Company-project IA/UI exploration before implementation: generate 2-3 static HTML mockup variants for a page or feature whose requirements (PRD / design spec) are already fixed, open them in the browser for side-by-side comparison. Not for value judgment, not for backend design."
---

# Joseki（定式）— 定式之内选变化图

公司项目的编码前探索。需求已被 PRD 和设计稿锁死，自由度只在 IA 和 UI 层面——这个 skill 把「反复重做页面」的成本从实现后推翻，提前到 mockup 阶段推翻。

不写 spec，不拆 task。选定变化图后直接进 plan mode 实现。

## 流程

1. **确认定式**：读 PRD / 设计稿 / 现有页面，用 3-5 行复述「不可动的约束」（字段、流程、交互契约、设计系统 token）。复述有误，用户会在这里纠正——这比 mockup 画错了再改便宜十倍。
2. **找变化点**：明确说出这次探索的自由度在哪一层——信息架构（分栏 / 分步 / 分 tab）、布局密度、还是组件形态。一次只探索一层，混着探索会导致变体之间不可比。
3. **出 2-3 个变体**：差异必须在被探索的那一层上是**结构性的**，配色和圆角不同不算变体。
4. **开浏览器对比**，用户选定或要求杂交（「A 的头部 + B 的表格」算正常产出，不算返工）。
5. **落一行决策记录**，然后停。实现另开 plan mode。

## Mockup 约定

- 每个变体一个**自包含的静态 HTML**（内联 CSS，无 build、无 server、无外部依赖），写到 `<repo>/.mockups/<yyyy-mm-dd>-<topic>/variant-{a,b,c}.html`。确保 `.mockups/` 在 `.gitignore` 里。
- 用**真实感数据**（真实字段名、合理长度的中文文案、边界情况如超长文本和空态），禁止 lorem ipsum——IA 判断靠真数据。
- 如果项目有设计系统（组件库、design token），mockup 的视觉语言必须贴近它，别画一个实现不出来的。
- 每个变体顶部放一条浅色说明栏：这个变体押的是什么（如「A 押：筛选高频，常驻左栏」）。
- 全部写完后 `open` 所有变体，让用户并排比。

## 决策记录（品味语料）

用户选定后，追加一行到 `<repo>/.mockups/decisions.md`：

```
- 2026-08-11 资产列表迁移：选 B（分组折叠）弃 A（平铺+筛选）。理由：运营常按业务线批量操作，分组命中心智。
```

这份文件是使用者 UI 品味的原始语料，攒够了会蒸馏成 taste 参考。只记选择和理由，一行一条，不写小作文。

## 边界

- 不做价值判断（那是 fuseki 的事），不设计接口和数据流。
- 变体数量上限 3。用户说「再来几个方向」时，先问上一轮哪里不对，带着约束出新变体，不撒新一轮大网。
- Mockup 是一次性产物，选完即弃；唯一沉淀的是 decisions.md。不要试图让 mockup 代码复用进实现。
