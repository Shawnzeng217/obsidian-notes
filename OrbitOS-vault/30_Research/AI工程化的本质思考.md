---
area: AI工程化
tags: [ai, engineering, prompt, agent]
created: 2026-04-09
status: processed
---
# AI工程化的本质思考

## Definition

每一个基础大模型都有自己的脾气。同一个Prompt，在不同模型上跑出来的效果可能完全不一样，因为每个模型的训练数据、微调目标都不同，它们理解指令的方式也会不一样。研究发现，大模型对Prompt本身非常敏感，哪怕只是改个格式，性能都可能明显变化。

## Key Points

- **Instruction、Skill、Agent、Harness** 等新名词，本质上都是在"调教"模型，让它更贴近我们的任务目标
- 这种调教往往是**模型相关的**：在A模型上很好用的Prompt或Agent设计，换到B模型上可能完全不work
- 对更强的模型来说，花里胡哨的结构有时反而会限制它发挥，不如简单指令效果好

## Examples

- 在Prompt中增加详细的思维链示例，对某些模型有效但对更强的模型可能是束缚
- 为低能力模型设计的few-shot示例，在高能力模型上反而可能导致格式依赖

## Related Concepts

- [[Prompt Engineering]]
- [[LLM]]
- [[AI-Agent]]

## References

- Source: Shawn (WeChat)