---
type: inbox
created: 2026-03-13
topic: iOS obsidian-git 配置指南
status: captured
source: obsidian-git 官方文档
tags: [obsidian, git, iOS, sync]
---
# iOS obsidian-git 配置指南

## 核心限制

- **不支持 SSH**（isomorphic-git 限制）
- **只能用 HTTPS + Personal Access Token (PAT)** 认证
- 插件在移动端不稳定，大仓库 clone 可能崩溃

---

## 方案一：通过插件直接 Clone（推荐）

1. iOS 安装 Obsidian，新建 vault —— **不要选 "Store in iCloud"**
2. 启用 Community Plugins → 安装并启用 **Git**
3. 进入 Git 插件设置 → **Authentication/Commit Author** 区域
4. 填入：
   - **Username**：你的 GitHub 用户名（`Shawnzeng217`）
   - **Password**：GitHub **Personal Access Token**（不是账号密码）
5. 打开命令面板 → `Git: Clone existing remote repo`
6. 输入：`https://github.com/Shawnzeng217/obsidian-notes.git`
7. 等待 clone 完成，提示重启 Obsidian 时重启

---

## 方案二：通过 Working Copy Clone（大仓库备选）

适用于插件 clone 崩溃的情况。[Working Copy](https://workingcopy.app/) 是付费 App（约 $20）。

1. 安装 Working Copy，用 HTTPS URL + PAT 作为密码 clone 仓库
2. 打开 iOS Files App → 复制仓库文件夹 → 粘贴到 Obsidian vault 位置
3. 打开 Obsidian，安装 Git 插件
4. 在插件设置填入姓名/邮箱 → 命令面板执行 `Pull`

---

## 如何生成 GitHub Personal Access Token

GitHub → Settings → Developer settings → Personal access tokens → Generate new token

最低权限要求：
- Read access to metadata
- Read and Write access to **contents** and commit status

---

## 注意事项

- 桌面端用 SSH，iOS 端用 HTTPS + PAT，两者互不影响
- PAT 只存在 iOS Obsidian 插件设置中，桌面端 SSH 配置不受影响
- 若仓库体量不大，方案一（插件直接 clone）通常可以正常运行
