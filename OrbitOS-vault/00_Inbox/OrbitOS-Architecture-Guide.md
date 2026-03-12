---
type: inbox
created: 2026-03-12
topic: OrbitOS 架构与使用指南
status: captured
source: Claude Code 架构分析
tags: [orbitOS, system, guide]
---
# OrbitOS 架构与使用指南

## 核心理念

**OrbitOS** = 以你为中心的知识轨道系统。所有笔记、项目、知识都在你周围运转，保持流动与关联。三个核心循环：**捕获 → 处理 → 参考**。

---

## 文件夹结构

```
00_Inbox/       快速捕获区（想法、链接、待处理）
10_Daily/       每日日记（YYYY-MM-DD.md）
20_Project/     活跃项目（平级结构，不按领域嵌套）
30_Research/    深度研究参考资料
40_Wiki/        原子知识（单概念笔记）
50_Resources/   精选内容（Newsletter / 产品发布）
90_Plans/       执行计划（完成后归档）
99_System/      系统文件（模板、Prompt、归档）
```

**关键规则**：项目通过 frontmatter `area: "[[AreaName]]"` 关联领域，而不是通过文件夹嵌套。

---

## 日常工作流（Flow）

### 早晨例行
```
/start-my-day
├── 回顾昨天未完成的任务
├── 列出活跃项目（标记超过3天未更新的）
├── 抓取 AI 简报（/ai-newsletters + /ai-products 并行）
├── 询问今日重点 / 新想法 / 阻碍
└── 生成今日日记（10_Daily/YYYY-MM-DD.md）
```

### 有想法 / 任务出现
```
快速记录 → 00_Inbox/{Item}.md（status: pending）
    ↓
转化为项目 → /kickoff     （结构化为 20_Project/）
深度研究   → /research    （生成 30_Research/ + 40_Wiki/）
快速提问   → /ask         （对话回答，不产生过多笔记）
处理文本块 → /parse-knowledge （非结构化文本 → vault）
```

### 项目生命周期
```
想法 → Inbox（pending）
  ↓ /kickoff
Project（active）
  ↓ 日常更新 Progress 区域
  ↓ Daily Note 互相链接
Project（done）
  ↓ /archive
99_System/Archives/Projects/YYYY/
```

---

## 核心技能（Slash Commands）

### 内容生产
| 命令 | 用途 |
|------|------|
| `/start-my-day` | 每日晨间规划 |
| `/kickoff` | 想法/Inbox → 正式项目 |
| `/research` | 深度研究 → 30_Research + 40_Wiki |
| `/brainstorm` | 交互式头脑风暴（可选转为项目） |
| `/ask` | 快速问答，不产生过多笔记 |
| `/parse-knowledge` | 文本块 → vault 结构化 |
| `/archive` | 清理完成项目和已处理 Inbox |

### 内容订阅
| 命令 | 用途 |
|------|------|
| `/ai-newsletters` | 每日 AI 简报（TLDR AI + The Rundown AI）|
| `/ai-products` | AI 产品发布（Product Hunt、HN、GitHub）|

### Obsidian 功能
| 命令 | 用途 |
|------|------|
| `/obsidian-markdown` | Obsidian 特有语法（wikilink、callout 等）|
| `/obsidian-bases` | 创建 .base 数据库视图文件 |
| `/json-canvas` | 创建 .canvas 可视化画布 |
| `/sync` | 提交所有变更并推送到 GitHub |

---

## 项目结构（C.A.P. 模型）

每个项目笔记用三段式：

```
## Context    ← 为什么做、目标、约束
## Actions    ← 分阶段任务（Phase 1 / 2 / 3...）
## Progress   ← 每次更新记录（链接到 Daily Note）
```

Frontmatter 模板：
```yaml
---
title: "项目名称"
type: project
status: active       # active | on-hold | done
area: "[[AreaName]]"
priority: P2         # P0-P4
created: YYYY-MM-DD
due: YYYY-MM-DD
tags: [project, ...]
---
```

---

## 双 Agent 工作流（/kickoff 和 /research）

这两个命令会自动启动两个 AI 子代理，不需要手动干预：

```
Phase 1 - Planning Agent
    ↓ 分析现有笔记、设计结构
    ↓ 生成计划文件（90_Plans/Plan_YYYY-MM-DD_*.md）
    ↓ 等待你确认/修改

Phase 2 - Execution Agent（确认后启动）
    ↓ 读取计划文件（全新上下文，无干扰）
    ↓ 创建实际笔记
    ↓ 归档 Inbox 原文件
    ↓ 链接到今日日记
```

---

## 知识层级

```
30_Research/{Area}/{Topic}.md     深度参考资料（完整内容）
       ↓ 提炼
40_Wiki/{Category}/{Concept}.md   原子概念（单一想法）
       ↓ 被引用
20_Project/*.md                   项目中通过 [[wikilink]] 引用
10_Daily/*.md                     日记中记录进展
```

---

## 系统资产

### 模板（99_System/Templates/）
- `Daily_Note.md` — 每日日记
- `Project_Template.md` — 项目笔记（C.A.P.）
- `Inbox_Template.md` — 快速捕获
- `Wiki_Template.md` — 原子知识
- `Content_Template.md` — 内容创作

### 专业 Prompt（99_System/Prompts/）
激活特定领域专家角色：
- **Finance**：Crypto、股票、债务、投资组合、税务
- **Health**：通用健康、用药、营养、症状分析
- **Software Engineering**：架构、代码库分析、面试准备
- **General**：第一性原理、心智模型、二阶思维

### Dashboard 视图（99_System/Bases/）
- `Projects.base` — 活跃项目看板
- `Projects_Archive.base` — 已归档项目
- `Knowledge.base` — 知识库索引

---

## 多 AI 支持

同一套技能（.agents/skills/）被三个 AI 客户端共享：
- **Claude Code**（.claude/） — 主要使用
- **Gemini CLI**（.gemini/）
- **Codex CLI**（.codex/）

---

## 快速上手建议

1. **每天早上** → `/start-my-day`
2. **有想法时** → 先丢进 `00_Inbox/`，再用 `/kickoff`
3. **想深入了解某个话题** → `/research`
4. **快速提问** → `/ask`（不会产生笔记噪音）
5. **用 `[[wikilink]]`** 大量连接笔记
6. **每周** → `/archive` 清理完成项目
