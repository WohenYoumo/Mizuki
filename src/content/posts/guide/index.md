---
title: "撰写博客文章"
published: 2024-04-01
description: "关于文章结构与 frontmatter 的通用示例。"
image: "./cover.webp"
tags: ["示例", "写作", "Markdown"]
category: "指南"
draft: false
licenseName: "MIT License"
---


本博客模板基于 [Astro](https://astro.build/) 构建。本文是一个简短的通用示例，展示一篇文章的文件结构与常用 frontmatter。完整的最新 schema 与 Markdown 语法，请参见[内容创作指南](../../../../docs/CONTENT_AUTHORING.md)。

## 通用 frontmatter

## 目录

- [通用 frontmatter](#common-frontmatter)
- [文章文件放在哪里](#where-to-place-the-post-files)

<a id="top"></a>

<a id="common-frontmatter"></a>

```yaml
---
title: "An Example Article"
published: 2026-08-01
updated: 2026-08-08
description: "A short summary for previews."
image: ./cover.webp
tags: [Example, Guide]
category: Guides
draft: false
comment: true
---
```

| Attribute     | Description                                                                                                                                                                                                 |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `title`       | 文章的标题。                                                                                                                                                                                      |
| `published`   | 文章发布的日期。                                                                                                                                                                            |
| `pinned`      | 是否将本文置顶在文章列表顶部。                                                                                                                                                   |
| `priority`    | 置顶文章的优先级。数值越小优先级越高（0、1、2……）。                                                                                                                          |
| `description` | 文章的简短描述，显示在首页。                                                                                                                                                   |
| `image`       | 文章的封面图路径。<br/>1. 以 `http://` 或 `https://` 开头：使用网络图片<br/>2. 以 `/` 开头：对应 `public` 目录下的图片<br/>3. 以上前缀都没有：相对于当前 markdown 文件 |
| `tags`        | 文章的标签。                                                                                                                                                                                       |
| `category`    | 文章的分类。                                                                                                                                                                                   |
| `licenseName` | 文章内容的许可证名称。                                                                                                                                                                      |
| `author`      | 文章的作者。                                                                                                                                                                                     |
| `sourceLink`  | 文章内容的来源链接或参考。                                                                                                                                                          |
| `draft`       | 若文章仍是草稿，则不会显示。                                                                                                                                                    |

## 文章文件放在哪里

<a id="where-to-place-the-post-files"></a>

将文章文件放在 `src/content/posts/` 目录下。你可以创建子目录，以组织文章及其本地资源。

```
src/content/posts/
├── example.md
└── guides/
    ├── cover.webp
    └── index.md
```

像 `./cover.webp` 这样的相对图片路径，会从当前文章文件所在位置开始解析。
