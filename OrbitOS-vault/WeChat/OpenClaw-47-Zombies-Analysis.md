---
type: content
format: article
status: processed
area: "[[OpenClaw]]"
created: 2026-03-22
tags: [openclaw, analysis, engineering]
---
# 我给 OpenClaw 杀了 47 次僵尸进程，终于想明白了一些事

**Source:** 微信文章 - 阿里云开发者 (苗刀)
**Date:** 2026-03-18
**Cover:** openclaw-47-zombies-2026-03-22.jpg

---

## 全文导读

1. 吐槽了部署和二开 OpenClaw 踩过的坑
2. 吐槽了钉钉通道集成的问题
3. 探究了 OpenClaw 为啥火
4. 对比了本地模式和云上沙箱
5. 反思了 Skill 与传统 Agent 工程
6. 反思了 AI 交付产品的局限性

---

## 核心观点

### 1. Gateway 是单点故障

- Gateway 挂了，整个系统就挂了
- 消息渠道、Agent 事件、定时任务、插件加载、浏览器自动化全部绑在 WebSocket 上
- 春节期间反复重启 Gateway，被迫"左右互搏"（装两个 OpenClaw 互相救）

### 2. 钉钉通道 vs Telegram

- Telegram 是标准 ChannelPlugin 接口
- 钉钉更像是"嫁接"上去的独立应用，缺少 gateway/status/pairing 适配器
- 图片消息处理不完整，只返回占位符

### 3. OpenClaw 成功的本质

- 30万 Star 是"叙事的胜利"而非技术胜利
- 它第一次把"个人 AI 助理"完整具象化了
- 站在成熟技术链条上：Pi-Mono + Skill/MCP + Playwright + IM Bot SDK

### 4. 本地 vs 云端 (OpenClaw vs Manus)

| 维度 | OpenClaw | Manus |
|------|----------|-------|
| 运行模式 | 开源、本地自托管 | 闭源 SaaS |
| 数据隐私 | 用户完全控制 | 数据托管云端 |
| 成本 | 免费，仅付 API | 付费订阅 |
| 安全风险 | 有，需用户自担 | 平台承担 |
| 上手门槛 | 高 | 开箱即用 |

### 5. Agent grep 式检索 vs 传统 RAG

- Agent grep: 几乎零前置工程、几小时可用、token 消耗高
- 传统 RAG: 需要分块/Embedding/数据库、数天到数周、召回率高
- RAG 已死是夸张墓志铭，现实是工程化与 Agent 模式重新分工

### 6. 测试的局限性

- 1337 个测试文件，6 个层次，覆盖率 70%
- TDD 能守住"别一下子炸掉"的底线，但救不了产品可用性
- AI 能写测试，但难以发现跨文件隐性耦合

### 7. 架构和产品缺位

- 860+ 贡献者，但架构师和产品经理依旧空缺
- 并发控制缺失、Docker 内存泄漏、SSE 流中断等问题
- AI 能写代码，但不能做架构决策

---

## 结论

1. **人 + AI 的项目，规模大就会损失商业级体验** — AI 能快速写代码、跑测试，但架构设计、产品判断仍需人扛

2. **AI 助理演进很快但非一蹴而就** — OpenClaw 是"未来雏形"而非"未来本身"

3. **Skill 模式 vs 传统工程化** — 不是谁替代谁，是场景决定选择：小规模高灵活用 Skill，大规模高频率靠工程化

---

## 相关

- [[OpenClaw]]
- [[Manus]]
- [[RAG]]
- [[AI-Agent]]

---

## 参考链接

- [The RAG Obituary](https://www.nicolasbustamante.com/p/the-rag-obituary-killed-by-agents)
- [Manus 访谈 (Peak)](https://www.xiaoyuzhoufm.com/episode/695331cb2db086f897b50ea9)
