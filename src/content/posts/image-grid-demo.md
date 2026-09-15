---
title: "图片画廊网格：语法与完整示例"
published: 2026-09-09
description: "一份关于图片画廊网格的语法、参数、裁剪、响应式行为、图注与灯箱导航的完整指南。"
tags: [Markdown, 画廊, 图片网格, 演示]
category: "教程"
licenseName: "MIT License"
draft: false
---

## 目录

- [极简语法](#minimal-syntax)
- [参数一览](#parameters-at-a-glance)
- [图注与 Alt 文本](#captions-and-alt-text)
- [布局与裁剪](#layout-and-cropping)
- [默认配置](#default-configuration)
- [三列竖图：3:4](#three-column-portraits-34)
- [三列横图：16:9](#three-column-landscapes-169)
- [两列方形图：1:1](#two-column-squares-11)
- [四列使用 contain](#four-columns-with-contain)
- [单列细节图](#single-column-detail-image)
- [稀疏的五列行](#sparse-five-column-row)
- [六列混合图片](#mixed-images-in-six-columns)
- [四列方形图：1:1](#four-column-squares-11)
- [六列横图：16:9](#six-column-landscapes-169)
- [三列竖图：3:4（六张）](#three-column-portraits-34-six)
- [边缘敏感内容：cover 与灯箱](#edge-critical-content-cover-and-lightbox)
- [极端比例使用 contain](#extreme-ratios-with-contain)
- [透明图片](#transparent-images)
- [灯箱导航](#lightbox-navigation)
- [检查清单](#checklist)



`:::grid` 是博客的图片画廊容器指令。它把普通 Markdown 图片排列成宽高比一致、响应式的网格，并自动启用灯箱浏览。可用于文章配图、截图、作品集或小相册。

同一画廊内的图片使用相同的卡片比例。默认情况下，居中裁剪会填满每张卡片并保持每行整齐；点击图片会在灯箱中打开完整的原始图片。每个画廊都有独立的灯箱分组，不会与文章中的其他图片混在一起。

> 本文既是功能文档，也是视觉测试页。请在桌面、平板和手机宽度下查看示例，然后点击任意图片以验证灯箱分组。

## 极简语法

<a id="minimal-syntax"></a>

在 `:::grid` 与结束标记 `:::` 之间直接写入 Markdown 图片：

````markdown
:::grid
![Image description](./image-1.webp)

![Image description](./image-2.webp)
:::
````

每张图片必须独占一个段落，图片之间留空行。画廊内只放图片；段落、列表和代码块请写在容器外面。

下面是极简语法的效果。不带参数时，网格默认使用三列、`16/10` 比例和 `cover` 填充。

:::grid
![极简语法效果：第一张图](/images/demos/image-grid-demo/landscape-1.webp)

![极简语法效果：第二张图](/images/demos/image-grid-demo/landscape-2.webp)
:::

## 参数一览

<a id="parameters-at-a-glance"></a>

在开头指令后的花括号中写入全部参数：`:::grid{parameter="value"}`。

| Parameter | Allowed values | Default | 说明 |
| --- | --- | --- | --- |
| `columns` | Integers from `1` to `6` | `3` | 桌面端每行的列数。无效值回退为 `3`。 |
| `aspect` | A positive ratio, such as `16/9`, `3/4`, or `1/1` | `16/10` | 显示的卡片比例，非原始图片比例。 |
| `fit` | `cover`, `contain` | `cover` | 图片填充方式。`cover` 裁剪以填满；`contain` 保留完整图片，可能留有空白。 |

完整示例：

````markdown
:::grid{columns="3" aspect="16/9" fit="cover"}
![First image](./image-1.webp "Optional caption")

![Second image](./image-2.webp "Optional caption")

![Third image](./image-3.webp "Optional caption")
:::
````

下面使用上述三列横图语法。请对比卡片比例、列数，以及标题优先于 alt 文本作为图注的效果：

:::grid{columns="3" aspect="16/9" fit="cover"}
![参数示例：第一张横图](/images/demos/image-grid-demo/landscape-1.webp "Landscape caption 1")

![参数示例：第二张横图](/images/demos/image-grid-demo/landscape-2.webp "Landscape caption 2")

![参数示例：第三张横图](/images/demos/image-grid-demo/landscape-3.webp "Landscape caption 3")
:::

## 图注与 Alt 文本

<a id="captions-and-alt-text"></a>

图片的 alt 文本既作为无障碍替代文本，也作为默认图注。当图片带有可选的 title 时，则改用 title 作为图注：

```markdown
![Text used for accessibility](./image.webp "Caption shown below the image")
```

在同一行中，图注与每张卡片的底部对齐。图注换行不会让其他卡片浮动到不同高度。像 `3:4`、`16:9` 这样的比例文本可直接写在正文、标题和 alt 文本中，无需转义。

本例演示了默认的 alt 文本图注、显式 title 图注，以及较长图注的底部对齐：

:::grid{columns="3" aspect="1/1"}
![这张图没有 title，因此 alt 文本即为图注](/images/demos/image-grid-demo/square-1.webp)

![第二张方形图，带无障碍 alt 文本](/images/demos/image-grid-demo/square-2.webp "This title is displayed as the caption")

![一张 3:4 海报的无障碍描述](/images/demos/image-grid-demo/square-3.webp "This is a longer caption for checking that every caption remains aligned to the bottom of its card when it wraps")
:::

## 布局与裁剪

<a id="layout-and-cropping"></a>

桌面布局使用 `columns` 指定的列数。宽度低于 `768px` 时，网格最多两列；低于 `480px` 时切换为一列。卡片包装器固定 `aspect` 比例并裁剪圆角，图片则填满卡片，不带主题默认的外边距。

- 选择 `cover`：推荐默认值。图片从中心裁剪以填满卡片，使画廊看起来整齐一致。
- 选择 `contain`：显示完整的原始图片，不裁剪。当比例与卡片不同时，主题背景会透出；适用于不能裁剪的图片。
- 若想完整显示图片且不留空白，可将 `aspect` 设为接近原始图片比例，或将图片单独放入一个网格。

下面两例把相同的竖图放入 `16/9` 卡片，分别使用 `cover` 与 `contain`。前者裁剪，后者保留完整图片并留有背景空间。

````markdown
:::grid{columns="3" aspect="16/9" fit="cover"}
![Image description](./image-1.webp "Optional caption")

![Image description](./image-2.webp "Optional caption")
:::

:::grid{columns="3" aspect="16/9" fit="contain"}
![Image description](./image-1.webp "Optional caption")

![Image description](./image-2.webp "Optional caption")
:::
````

:::grid{columns="3" aspect="16/9" fit="cover"}
![cover 效果：第一张](/images/demos/image-grid-demo/default-portrait-1.webp "Cover: center crop")

![cover 效果：第二张](/images/demos/image-grid-demo/default-portrait-2.webp "Cover: fill the card")

![cover 效果：第三张](/images/demos/image-grid-demo/default-portrait-3.webp "Cover: a more consistent layout")
:::

:::grid{columns="3" aspect="16/9" fit="contain"}
![contain 效果：第一张](/images/demos/image-grid-demo/default-portrait-1.webp "Contain: preserve the complete original")

![contain 效果：第二张](/images/demos/image-grid-demo/default-portrait-2.webp "Contain: empty space may appear")

![contain 效果：第三张](/images/demos/image-grid-demo/default-portrait-3.webp "Contain: suitable for edge details")
:::

## 默认配置

<a id="default-configuration"></a>

Without attributes, the default is three columns, a `16/10` ratio, and `cover` cropping. 这三张竖图用于验证默认裁剪与图注。

````markdown
:::grid
![Image description](./image-1.webp)

![Image description](./image-2.webp)

![Image description](./image-3.webp)
:::
````

:::grid
![默认配置：竖图一](/images/demos/image-grid-demo/default-portrait-1.webp)

![默认配置：竖图二](/images/demos/image-grid-demo/default-portrait-2.webp)

![默认配置：竖图三](/images/demos/image-grid-demo/default-portrait-3.webp)
:::

## 三列竖图：3:4

<a id="three-column-portraits-34"></a>

使用 `aspect="3/4"` 时，三张竖图会填满比例一致的纵向卡片。若原始图片比例不同，`cover` 会从中心裁剪边缘。

````markdown
:::grid{columns="3" aspect="3/4"}
![Portrait image description](./portrait-1.webp)

![Portrait image description](./portrait-2.webp)

![Portrait image description](./portrait-3.webp)
:::
````

:::grid{columns="3" aspect="3/4"}
![3:4 测试图一](/images/demos/image-grid-demo/default-portrait-1.webp "Portrait 1")

![3:4 测试图二](/images/demos/image-grid-demo/default-portrait-2.webp "Portrait 2")

![3:4 测试图三](/images/demos/image-grid-demo/default-portrait-3.webp "Portrait 3")
:::

## 三列横图：16:9

<a id="three-column-landscapes-169"></a>

本组在三列布局中演示常见的视频封面比例。当横图比例接近卡片比例时，裁剪最少。

````markdown
:::grid{columns="3" aspect="16/9"}
![Landscape image description](./landscape-1.webp)

![Landscape image description](./landscape-2.webp)

![Landscape image description](./landscape-3.webp)
:::
````

:::grid{columns="3" aspect="16/9"}
![16:9 测试图一](/images/demos/image-grid-demo/feature-landscape-1.webp)

![16:9 测试图二](/images/demos/image-grid-demo/feature-landscape-2.webp)

![16:9 测试图三](/images/demos/image-grid-demo/feature-landscape-3.webp)
:::

## 两列方形图：1:1

<a id="two-column-squares-11"></a>

需要较大预览卡片时，两列效果很好。第三张图片会移到下一行。最后一行保持网格轨道宽度，而不会拉伸图片去填满整行。

````markdown
:::grid{columns="2" aspect="1/1"}
![Square image description](./square-1.webp)

![Square image description](./square-2.webp)

![Square image description](./square-3.webp)
:::
````

:::grid{columns="2" aspect="1/1"}
![1:1 测试图一](/images/demos/image-grid-demo/mixed-square-1.webp)

![1:1 测试图二](/images/demos/image-grid-demo/mixed-square-2.webp)

![1:1 测试图三](/images/demos/image-grid-demo/mixed-square-3.webp)
:::

## 四列使用 contain

<a id="four-columns-with-contain"></a>

`fit="contain"` 不会裁剪原始图片。当图片比例与卡片比例不同时，主题背景会透出。这是有意为之，并非布局问题。同时也验证四列网格与独立灯箱分组互不干扰。

````markdown
:::grid{columns="4" aspect="16/9" fit="contain"}
![Image description](./image-1.webp)

![Image description](./image-2.webp)

![Image description](./image-3.webp)
:::
````

:::grid{columns="4" aspect="16/9" fit="contain"}
![contain：竖图一](/images/demos/image-grid-demo/default-portrait-1.webp)

![contain：竖图二](/images/demos/image-grid-demo/default-portrait-2.webp)

![contain：竖图三](/images/demos/image-grid-demo/default-portrait-3.webp)
:::

## 单列细节图

<a id="single-column-detail-image"></a>

当图片需要更大阅读尺寸时，单列是合适的选择。它在桌面、平板和手机上都保持一列，灯箱中仍可查看原始图片。

````markdown
:::grid{columns="1" aspect="16/9"}
![Image description](./detail.webp)
:::
````

:::grid{columns="1" aspect="16/9"}
![单列测试图](/images/demos/image-grid-demo/feature-landscape-1.webp)
:::

## 稀疏的五列行

<a id="sparse-five-column-row"></a>

五列用于验证更高的支持列数。仅有三张图片时，最后一行保持左对齐，而不会拉伸图片。

````markdown
:::grid{columns="5" aspect="1/1"}
![Thumbnail description](./thumb-1.webp)

![Thumbnail description](./thumb-2.webp)

![Thumbnail description](./thumb-3.webp)
:::
````

:::grid{columns="5" aspect="1/1"}
![五列测试图一](/images/demos/image-grid-demo/mixed-square-1.webp)

![五列测试图二](/images/demos/image-grid-demo/mixed-square-2.webp)

![五列测试图三](/images/demos/image-grid-demo/mixed-square-3.webp)
:::

## 六列混合图片

<a id="mixed-images-in-six-columns"></a>

六列是当前的最大值。混合横图与竖图可验证 `cover` 裁剪、窄卡片上的图注，以及密集的桌面布局。为保证文章可读性，通常更推荐两到四列。

````markdown
:::grid{columns="6" aspect="1/1"}
![Image description](./image-1.webp)

![Image description](./image-2.webp)

![Image description](./image-3.webp)

![Image description](./image-4.webp)

![Image description](./image-5.webp)

![Image description](./image-6.webp)
:::
````

:::grid{columns="6" aspect="1/1"}
![六列测试图一](/images/demos/image-grid-demo/default-portrait-1.webp)

![六列测试图二](/images/demos/image-grid-demo/default-portrait-2.webp)

![六列测试图三](/images/demos/image-grid-demo/default-portrait-3.webp)

![六列测试图四](/images/demos/image-grid-demo/feature-landscape-1.webp)

![六列测试图五](/images/demos/image-grid-demo/feature-landscape-2.webp)

![六列测试图六](/images/demos/image-grid-demo/feature-landscape-3.webp)
:::

## 四列方形图：1:1

<a id="four-column-squares-11"></a>

四张等比例的方形图是典型的四列布局。桌面端一行显示四张；平板折成两列，手机为一列。

````markdown
:::grid{columns="4" aspect="1/1"}
![Square image description](./square-1.webp)

![Square image description](./square-2.webp)

![Square image description](./square-3.webp)

![Square image description](./square-4.webp)
:::
````

:::grid{columns="4" aspect="1/1"}
![方形图一](/images/demos/image-grid-demo/square-1.webp)

![方形图二](/images/demos/image-grid-demo/square-2.webp)

![方形图三](/images/demos/image-grid-demo/square-3.webp)

![方形图四](/images/demos/image-grid-demo/square-4.webp)
:::

## 六列横图：16:9

<a id="six-column-landscapes-169"></a>

六列横图非常适合缩略图预览、作品集和截图索引。即便原始比例略有差异，`cover` 也能一致地填满每张 `16/9` 卡片。

````markdown
:::grid{columns="6" aspect="16/9"}
![Landscape image description](./landscape-1.webp)

![Landscape image description](./landscape-2.webp)

![Landscape image description](./landscape-3.webp)

![Landscape image description](./landscape-4.webp)

![Landscape image description](./landscape-5.webp)

![Landscape image description](./landscape-6.webp)
:::
````

:::grid{columns="6" aspect="16/9"}
![横图一](/images/demos/image-grid-demo/landscape-1.webp)

![横图二](/images/demos/image-grid-demo/landscape-2.webp)

![横图三](/images/demos/image-grid-demo/landscape-3.webp)

![横图四](/images/demos/image-grid-demo/landscape-4.webp)

![横图五](/images/demos/image-grid-demo/landscape-5.webp)

![横图六](/images/demos/image-grid-demo/landscape-6.webp)
:::

## 三列竖图：3:4（六张）

<a id="three-column-portraits-34-six"></a>

这六张竖图演示了人物、海报或手机截图的常见布局。图片排成两行三列，图注与底部对齐。

````markdown
:::grid{columns="3" aspect="3/4"}
![Portrait image description](./portrait-1.webp)

![Portrait image description](./portrait-2.webp)

![Portrait image description](./portrait-3.webp)

![Portrait image description](./portrait-4.webp)

![Portrait image description](./portrait-5.webp)

![Portrait image description](./portrait-6.webp)
:::
````

:::grid{columns="3" aspect="3/4"}
![竖图一](/images/demos/image-grid-demo/portrait-1.webp)

![竖图二](/images/demos/image-grid-demo/portrait-2.webp)

![竖图三](/images/demos/image-grid-demo/portrait-3.webp)

![竖图四](/images/demos/image-grid-demo/portrait-4.webp)

![竖图五](/images/demos/image-grid-demo/portrait-5.webp)

![竖图六](/images/demos/image-grid-demo/portrait-6.webp)
:::

## 边缘敏感内容：cover 与灯箱

<a id="edge-critical-content-cover-and-lightbox"></a>

这些图片在边缘附近含有重要文字或细节。`cover` 能保持网格整齐，但可能裁掉这些边缘；点击图片可在灯箱中查看未裁剪的原始图。对边缘敏感图片请使用清晰的图注，或改用下面的 `contain`。

````markdown
:::grid{columns="3" aspect="16/9" fit="cover"}
![Edge-critical content](./critical-1.webp "Open the lightbox to view the complete edge content")

![Edge-critical content](./critical-2.webp "Open the lightbox to view the complete edge content")

![Edge-critical content](./critical-3.webp "Open the lightbox to view the complete edge content")
:::
````

:::grid{columns="3" aspect="16/9" fit="cover"}
![边缘敏感图一](/images/demos/image-grid-demo/critical-1.webp "Open the lightbox to view the complete edge content")

![边缘敏感图二](/images/demos/image-grid-demo/critical-2.webp "Open the lightbox to view the complete edge content")

![边缘敏感图三](/images/demos/image-grid-demo/critical-3.webp "Open the lightbox to view the complete edge content")
:::

## 极端比例使用 contain

<a id="extreme-ratios-with-contain"></a>

对于横幅、长截图等极端比例的图片，`contain` 会显示完整的原始图。与 `cover` 不同，它可能会留出主题背景空间，但绝不会裁剪内容。

````markdown
:::grid{columns="3" aspect="16/9" fit="contain"}
![Complete screenshot description](./wide-1.webp)

![Complete screenshot description](./wide-2.webp)

![Complete screenshot description](./wide-3.webp)
:::
````

:::grid{columns="3" aspect="16/9" fit="contain"}
![极端比例图一](/images/demos/image-grid-demo/extreme-1.webp)

![极端比例图二](/images/demos/image-grid-demo/extreme-2.webp)

![极端比例图三](/images/demos/image-grid-demo/extreme-3.webp)
:::

## 透明图片

<a id="transparent-images"></a>

透明图片会透出卡片的主题背景。这个单列 `contain` 示例便于观察透明区域、原始边缘和灯箱行为。

````markdown
:::grid{columns="1" aspect="16/9" fit="contain"}
![Transparent image description](./transparent.webp)
:::
````

:::grid{columns="1" aspect="16/9" fit="contain"}
![透明背景测试图](/images/demos/image-grid-demo/transparent-1.webp)
:::

## 灯箱导航

<a id="lightbox-navigation"></a>

点击网格中任意图片即可打开 Fancybox 灯箱。在其中可缩放、旋转、进入全屏、查看缩略图，并用方向键导航。导航仅限于当前 `:::grid` 容器：例如点击“16:9 测试图一”只会打开本节另外两张横图。

同一文章中的普通 Markdown 图片仍被单独处理，不会被加入任何网格画廊。

## 检查清单

<a id="checklist"></a>

1. Images in each grid have consistent dimensions, with captions below the cards.
2. Images scale slightly on hover; after clicking, they can be zoomed, rotated, and navigated with the keyboard.
3. Clicking "16:9 test image one" lets the lightbox browse only the other two landscape images in that section.
4. Below 768px, grids use at most two columns; below 480px, they use one column.
5. Portrait images in "Four Columns with `contain`" are fully visible with empty space and no cropping.
6. Five- and six-column grids retain their specified column count on wide screens, then collapse to two or one column according to the responsive rules.
