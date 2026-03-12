---
date: 2026-03-12
type: kickoff-plan
project: Context-Aware MacroPad
status: draft
---
# Kickoff Plan: 上下文感知迷你宏键盘

## Source
- Inbox file: 内联输入（来自 [[10_Daily/2026-03-12]] 的头脑风暴记录）

## Objective
配置已购入的 3键+旋钮外接宏键盘，配合 Karabiner-Elements 实现 AI vibe coding 场景下的一键审批操作——根据活动 IDE/工具自动切换快捷键映射（如 Alt+Enter 审批 AI 请求），覆盖多个开发工具。

## Project Structure
- Area: [[Productivity]]
- Type: project
- Estimated scope: small（单文件，后期可扩展为文件夹）

## Proposed Action Items
- [ ] 定义成功标准（哪些 app + 哪些快捷键场景）
- [ ] 拆分阶段与里程碑（软件验证 → 硬件采购 → 完整配置）
- [ ] 确认依赖与阻碍（Karabiner 版本兼容、macOS 权限设置）
- [ ] 建立项目文件结构（如规模扩大则升级为文件夹）

## Draft Project Outline

### Context
**背景**：用户已购入一块 3键+旋钮的可自定义外接宏键盘（具体型号待收货后确认），主要用途是辅助 **AI vibe coding** 工作流。

**核心痛点**：在 AI 辅助编码过程中（如 [[Antigravity]] 项目），AI 工具频繁弹出权限审批请求（Antigravity 使用 `Alt+Enter` 确认），需要手动切换到键盘操作，打断心流。不同 IDE / AI 工具的审批快捷键各不相同，难以统一记忆。

**方案**：将宏键盘的物理按键配置为"AI 审批键"——通过 Karabiner-Elements 的 `frontmost_application` 条件，同一物理按键在不同工具下自动触发对应的审批/确认快捷键：
- **Antigravity / Cursor** → `Alt+Enter`
- **其他 IDE** → 待收货后根据实际使用场景补充
- **旋钮** → 可配置为滚动、音量或其他高频调节

**为什么值得做**：AI vibe coding 的核心是保持心流，减少手眼离开主界面的次数。一键审批可将重复性中断操作降至零摩擦。

### Actions (Phases)

- **Phase 1：收货 & 识别硬件**
  - 等待键盘到货，确认型号和固件类型（QMK/VIA 或厂商专属软件）
  - 用 VIA 网页配置器（或厂商工具）将 3 个物理按键输出设为独立键值（建议 F13、F14、F15）
  - 里程碑：键盘接入 Mac 后 3 个按键可被系统识别为独立输入

- **Phase 2：Karabiner-Elements 核心配置**
  - 安装 Karabiner-Elements，开启辅助功能权限
  - 为每个目标工具编写 `frontmost_application` 条件规则：
    - **Antigravity / Cursor**：F13 → `Alt+Enter`（AI 审批）
    - **其他 IDE**：收货后补充（待用户提供具体工具列表）
    - **通用兜底**：无匹配 app 时 F13 → `Enter`
  - 里程碑：在 Antigravity 中一键通过 AI 审批无误触

- **Phase 3：扩展 & 备份**
  - 根据实际使用补充更多 app 的映射规则
  - 配置旋钮功能（滚动 / 音量 / 其他）
  - 将 Karabiner JSON 规则文件备份至 vault（`99_System/` 或本项目文件夹）
  - 里程碑：配置可在新机器上一键复现

### Success Metrics
- [ ] Antigravity / Cursor 中 AI 审批请求可通过单键完成，无需手动按 Alt+Enter
- [ ] 至少覆盖 3 个常用 AI 编码工具的审批快捷键
- [ ] 无误触：非目标 app 下按键不触发错误操作
- [ ] Karabiner JSON 配置已备份至 vault，可在新机器复现
- [ ] 旋钮已配置实用功能

## Clarification Questions (Optional)
*如有答案请填写；留空则按标准假设推进。*

**Q:** 这个项目的时间线或截止日期是什么？
**A:**

**Q:** 优先级如何？（P0=紧急, P1=高, P2=中, P3=低, P4=随时）
**A:**

**Q:** 有哪些特定限制或要求？
**A:** 硬件已购入（3键+旋钮，型号待确认）；软件侧仅使用 Karabiner-Elements（免费），不引入付费工具；主要场景为 AI vibe coding 审批操作。

**Q:** 已知的 AI 工具审批快捷键？
**A:** Antigravity → `Alt+Enter`；其他 IDE 待收货后补充。