---
type: inbox
created: 2026-03-12
topic: 朋友圈文案 - OrbitOS + Happy CLI 工作流
status: captured
tags: [朋友圈, writing, 知识管理, AI笔记]
---
# 朋友圈：OrbitOS + Happy CLI 工作流

最近在折腾 AI 辅助工作流，几个工具分头摸索，今天突然发现能串起来用。

研究带有自动化技能的 AI 工作流仓库时，发现了 OrbitOS vault——一套跑在 Obsidian 上的知识管理结构，Inbox 捕想法、Daily 写日记、Project 管项目、Wiki 存知识，全部双向链接，配套一批 slash commands 直接调用 AI 来处理笔记。一直在找一个真正适合自己的知识管理系统，这套结构算是目前用过最顺手的——不强迫你按固定格式记，但又有足够的骨架让内容自然沉淀。想把 Obsidian 同步到 GitHub 备份，找到了 obsidian-git 插件，装上去就能自动 commit + push。研究怎么用手机远程调用本地大模型，找到了 Happy CLI，登录后手机直接连本地的 Claude 或 Gemini，AI 可以读写本地文件，不走云端。

三件事分别做完，今天想着能不能接在一起：Happy 远程调用本地 AI → AI 操作 OrbitOS vault 里的笔记 → 在此基础上我自己加了一个 `/sync` 命令，底层调用 obsidian-git，一句话把所有改动推到 GitHub。AI 笔记这件事以前总觉得噱头大于实用，但当 AI 能直接理解你的笔记结构、按你的习惯帮你整理和归档，感觉就不一样了。

实测：手机打开 Happy，让 AI 往 Inbox 里建了一个笔记，发一句 `/sync`，几秒后 GitHub 上就有了这条提交记录——全程没碰电脑。

上手有一定门槛，但配置一次之后基本是自动运转的状态。感兴趣可以聊。

每个工具单独用都觉得有意思，但真正串起来的那一刻才明白自动化的意义不在于省了几步操作，而是几个系统开始互相感知、协同工作——那种感觉完全不一样。
