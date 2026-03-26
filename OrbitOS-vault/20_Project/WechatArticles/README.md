---
title: WechatArticles
type: project
status: active
area: "[[Writing]]"
created: 2026-03-26
tags: [wechat, content]
---
# WechatArticles

**Objective:** Store and publish WeChat Official Account articles from this vault.

## Folder Structure

Each article lives in its own folder:

```
YYYY-MM-DD-slug/
├── index.md      ← article body (use WechatArticle_Template)
├── imgs/         ← images (cover.png = cover image for WeChat)
└── refs/         ← references, quotes, source material
```

## Workflow

1. Create folder: `YYYY-MM-DD-slug/`
2. Create `index.md` from `WechatArticle_Template`
3. Add cover image as `imgs/cover.png`
4. Write content, place any reference material in `refs/`
5. Post to WeChat draft box:

```
/baoyu-post-to-wechat <path>/index.md
```

## Articles

| Folder | Title | Status | Published |
|--------|-------|--------|-----------|
| 2026-03-26-hello-tommytale | 你好，Tommytale | draft | — |

## Related

- [[99_System/Templates/WechatArticle_Template]]
