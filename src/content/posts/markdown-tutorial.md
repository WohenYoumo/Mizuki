---
title: Markdown 教程
published: 2026-09-08
pinned: true
description: 一个 Markdown 博客文章的简单示例。
tags: [Markdown, 博客]
category: 教程
licenseName: "GNU Lesser General Public License v3.0"
author: emn178
sourceLink: "https://github.com/emn178/markdown"
draft: false
---

# Markdown 教程

一篇展示如何编写 Markdown 文件的示例文档。本文整合了核心语法与扩展（GFM）。

- [块级元素](#block-elements)
  - [段落与换行](#paragraphs-and-line-breaks)
  - [标题](#headers)
  - [块引用](#blockquotes)
  - [列表](#lists)
  - [代码块](#code-blocks)
  - [水平分割线](#horizontal-rules)
  - [表格](#table)
- [行内元素](#span-elements)
  - [链接](#links)
  - [强调](#emphasis)
  - [代码](#code)
  - [图片](#images)
  - [删除线](#strikethrough)
- [杂项](#miscellaneous)
  - [自动链接](#automatic-links)
  - [反斜杠转义](#backslash-escapes)
- [内联 HTML](#inline-html)

<a id="block-elements"></a>

## 块级元素

<a id="paragraphs-and-line-breaks"></a>

### 段落与换行

<a id="paragraphs"></a>

#### 段落

HTML 标签：`<p>`

由一个或多个空行分隔。（空行指该行除了**空格**或**制表符**外没有任何其他内容。）

代码：

    This will be
    inline.

    This is second paragraph.

预览：

---

This will be
inline.

This is second paragraph.

---

<a id="line-breaks"></a>

#### 换行

HTML 标签：`<br />`

在一行结尾处输入**两个或更多空格**即可换行。

代码：

    This will be not
    inline.

预览：

---

This will be not  
inline.

---

<a id="headers"></a>

### 标题

Markdown 支持两种风格的标题：Setext 和 atx。

<a id="setext"></a>

#### Setext

HTML 标签：`<h1>`、`<h2>`

使用**等号（=）**作为 `<h1>`，**连字符（-）**作为 `<h2>`，数量任意。

代码：

    This is an H1
    =============
    This is an H2
    -------------

预览：

---

# This is an H1

## This is an H2

---

<a id="atx"></a>

#### atx

HTML 标签：`<h1>`、`<h2>`、`<h3>`、`<h4>`、`<h5>`、`<h6>`

在行首使用 1~6 个**井号（#）**，分别对应 `<h1>` ~ `<h6>`。

代码：

    # This is an H1
    ## This is an H2
    ###### This is an H6

预览：

---

# This is an H1

## This is an H2

###### This is an H6

---

你也可以选择性地"闭合"atx 风格的标题。闭合的井号**无需与开头的数量一致**。

代码：

    # This is an H1 #
    ## This is an H2 ##
    ### This is an H3 ######

预览：

---

# This is an H1

## This is an H2

### This is an H3

---

<a id="blockquotes"></a>

### 块引用

HTML 标签：`<blockquote>`

Markdown 使用邮件风格的 **>** 字符来表示块引用。最好手动折行并在每行前都加上 >。

代码：

    > This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
    > consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
    > Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
    >
    > Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
    > id sem consectetuer libero luctus adipiscing.

预览：

---

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
> Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
>
> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
> id sem consectetuer libero luctus adipiscing.

---

Markdown 允许你"偷懒"，只需在硬折行段落的第一行前加 >。

代码：

    > This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
    consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
    Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

    > Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
    id sem consectetuer libero luctus adipiscing.

预览：

---

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
> Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
> id sem consectetuer libero luctus adipiscing.

---

块引用可以嵌套（即在块引用中再放块引用），只需增加 **>** 的层级。

代码：

    > This is the first level of quoting.
    >
    > > This is nested blockquote.
    >
    > Back to the first level.

预览：

---

> This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.

---

块引用中可以包含其他 Markdown 元素，包括标题、列表和代码块。

代码：

    > ## This is a header.
    >
    > 1.   This is the first list item.
    > 2.   This is the second list item.
    >
    > Here's some example code:
    >
    >     return shell_exec("echo $input | $markdown_script");

预览：

---

> ## This is a header.
>
> 1.  This is the first list item.
> 2.  This is the second list item.
>
> Here's some example code:
>
>     return shell_exec("echo $input | $markdown_script");

---

<a id="lists"></a>

### 列表

Markdown 支持有序（编号）和无序（项目符号）列表。

<a id="unordered"></a>

#### 无序列表

HTML 标签：`<ul>`

无序列表使用**星号（\*）**、**加号（+）**和**连字符（-）**。

代码：

    *   Red
    *   Green
    *   Blue

预览：

---

- Red
- Green
- Blue

---

等价于：

代码：

    +   Red
    +   Green
    +   Blue

以及：

代码：

    -   Red
    -   Green
    -   Blue

<a id="ordered"></a>

#### 有序列表

HTML 标签：`<ol>`

有序列表使用数字后跟句点：

代码：

    1.  Bird
    2.  McHale
    3.  Parish

预览：

---

1.  Bird
2.  McHale
3.  Parish

---

有时会意外触发有序列表，例如这样写：

代码：

    1986. What a great season.

预览：

---

1986. What a great season.

---

你可以使用**反斜杠转义（\\）**来转义句点：

代码：

    1986\. What a great season.

预览：

---

1986\. What a great season.

---

<a id="indented"></a>

#### 缩进

<a id="list-blockquotes"></a>

##### 块引用

要在列表项中放置块引用，块引用的 > 分隔符需要缩进：

代码：

    *   A list item with a blockquote:

        > This is a blockquote
        > inside a list item.

预览：

---

- A list item with a blockquote:

  > This is a blockquote
  > inside a list item.

---

<a id="list-code-blocks"></a>

##### 代码块

要在列表项中放置代码块，代码块需要缩进两次——**8 个空格**或**两个制表符**：

代码：

    *   A list item with a code block:

            <code goes here>

预览：

---

- A list item with a code block:

      <code goes here>

---

<a id="nested-list"></a>

##### 嵌套列表

代码：

    * A
      * A1
      * A2
    * B
    * C

预览：

---

- A
  - A1
  - A2
- B
- C

---

<a id="code-blocks"></a>

### 代码块

HTML 标签：`<pre>`

将代码块的每一行缩进至少 **4 个空格**或 **1 个制表符**。

代码：

    This is a normal paragraph:

        This is a code block.

预览：

---

This is a normal paragraph:

    This is a code block.

---

代码块会一直持续到遇到未缩进的行（或文章末尾）。

在代码块中，**& 符号**和**尖括号（< 和 >）**会自动转换为 HTML 实体。

代码：

        <div class="footer">
            &copy; 2004 Foo Corporation
        </div>

预览：

---

    <div class="footer">
        &copy; 2004 Foo Corporation
    </div>

---

以下"围栏式代码块"和"语法高亮"属于扩展，你可以使用其他方式编写代码块。

<a id="fenced-code-blocks"></a>

#### 围栏式代码块

只需用 ` ``` ` 包裹代码（如下所示），无需再缩进 4 个空格。

代码：

    Here's an example:

    ```
    function test() {
      console.log("notice the blank line before this function?");
    }
    ```

预览：

---

Here's an example:

```
function test() {
  console.log("notice the blank line before this function?");
}
```

---

<a id="syntax-highlighting"></a>

#### 语法高亮

在围栏代码块中，添加可选的语言标识符，即可进行语法高亮（[支持的语言](https://github.com/github/linguist/blob/master/lib/linguist/languages.yml)）。

代码：

    ```ruby
    require 'redcarpet'
    markdown = Redcarpet.new("Hello World!")
    puts markdown.to_html
    ```

预览：

---

```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

---

<a id="horizontal-rules"></a>

### 水平分割线

HTML 标签：`<hr />`

在一行上单独放置**三个或更多连字符（-）、星号（\*）或下划线（\_）**。你可以在连字符或星号之间使用空格。

代码：

    * * *
    ***
    *****
    - - -
    ---------------------------------------
    ___

预览：

---

---

---

---

---

---

---

---

<a id="table"></a>

### 表格

HTML 标签：`<table>`

这是一个扩展。

使用**竖线（|）**分隔列，**连字符（-）**分隔表头，并使用**冒号（:）**设置对齐。

外层的**竖线（|）**和对齐是可选的。每个单元格至少需要 **3 个分隔符**来分隔表头。

代码：

```
| Left | Center | Right |
|:-----|:------:|------:|
|aaa   |bbb     |ccc    |
|ddd   |eee     |fff    |

 A | B
---|---
123|456


A |B
--|--
12|45
```

预览：

---

| Left | Center | Right |
| :--- | :----: | ----: |
| aaa  |  bbb   |   ccc |
| ddd  |  eee   |   fff |

| A   | B   |
| --- | --- |
| 123 | 456 |

| A   | B   |
| --- | --- |
| 12  | 45  |

---

<a id="span-elements"></a>

## 行内元素

<a id="links"></a>

### 链接

HTML 标签：`<a>`

Markdown 支持两种风格的链接：行内式和引用式。

<a id="inline-link"></a>

#### 行内式

行内链接格式如下：`[链接文本](URL "标题")`

标题是可选的。

代码：

    This is [an example](http://example.com/ "Title") inline link.

    [This link](http://example.net/) has no title attribute.

预览：

---

This is [an example](http://example.com/ "Title") inline link.

[This link](http://example.net/) has no title attribute.

---

如果引用的是同一服务器上的本地资源，可以使用相对路径：

代码：

    See my [About](/about/) page for details.

预览：

---

See my [About](/about/) page for details.

---

<a id="reference-link"></a>

#### 引用式

你可以预定义链接引用。格式如下：`[id]: URL "标题"`

标题同样可选。引用链接时格式如下：`[链接文本][id]`

代码：

    [id]: http://example.com/  "Optional Title Here"
    This is [an example][id] reference-style link.

预览：

---

[id]: http://example.com/ "Optional Title Here"

This is [an example][id] reference-style link.

---

即：

- 方括号包含链接标识符（**不区分大小写**，可从左边界缩进最多三个空格）；
- 后跟一个冒号；
- 后跟一个或多个空格（或制表符）；
- 后跟链接的 URL；
- 链接 URL 可选地用尖括号包裹；
- 可选地后跟链接的标题属性，用双引号、单引号或圆括号包裹。

以下三种链接定义是等价的：

代码：

    [foo]: http://example.com/  "Optional Title Here"
    [foo]: http://example.com/  'Optional Title Here'
    [foo]: http://example.com/  (Optional Title Here)
    [foo]: <http://example.com/>  "Optional Title Here"

使用一组空的方括号时，链接文本本身会作为名称。

代码：

    [Google]: http://google.com/
    [Google][]

预览：

---

[Google]: http://google.com/

[Google][]

---

<a id="emphasis"></a>

### 强调

HTML 标签：`<em>`、`<strong>`

Markdown 将**星号（\*）**和**下划线（\_）**视为强调标记。**一个分隔符**对应 `<em>`；**两个分隔符**对应 `<strong>`。

代码：

    *single asterisks*

    _single underscores_

    **double asterisks**

    __double underscores__

预览：

---

_single asterisks_

_single underscores_

**double asterisks**

**double underscores**

---

但如果你在 * 或 _ 两侧加上空格，它们会被当作字面字符。

你可以使用反斜杠转义：

代码：

    \*this text is surrounded by literal asterisks\*

预览：

---

\*this text is surrounded by literal asterisks\*

---

<a id="code"></a>

### 代码

HTML 标签：`<code>`

用**反引号（`）**包裹。

代码：

    Use the `printf()` function.

预览：

---

Use the `printf()` function.

---

要在代码行内包含字面反引号字符，可以使用**多个反引号**作为开头和闭合分隔符：

代码：

    ``There is a literal backtick (`) here.``

预览：

---

``There is a literal backtick (`) here.``

---

围绕代码行的反引号分隔符可以包含空格——开头后一个，闭合前一个。这让你可以把字面反引号放在代码行的开头或结尾：

代码：

    A single backtick in a code span: `` ` ``

    A backtick-delimited string in a code span: `` `foo` ``

预览：

---

A single backtick in a code span: `` ` ``

A backtick-delimited string in a code span: `` `foo` ``

---

<a id="images"></a>

### 图片

HTML 标签：`<img />`

Markdown 使用的图片语法意在模仿链接语法，也支持两种风格：行内式和引用式。

<a id="inline-img"></a>

#### 行内式

行内图片语法如下：`![替代文本](URL "标题")`

标题是可选的。

代码：

    ![Alt text](/path/to/img.jpg)

    ![Alt text](/path/to/img.jpg "Optional title")

预览：

---

![Alt text](https://s2.loli.net/2024/08/20/5fszgXeOxmL3Wdv.webp)

![Alt text](https://s2.loli.net/2024/08/20/5fszgXeOxmL3Wdv.webp "Optional title")

---

即：

- 一个感叹号：!；
- 后跟一组方括号，包含图片的 alt 属性文本；
- 后跟一组圆括号，包含图片的 URL 或路径，以及可选的标题属性（用双引号或单引号包裹）。

<a id="reference-img"></a>

#### 引用式

引用式图片语法如下：`![替代文本][id]`

代码：

    [img id]: https://s2.loli.net/2024/08/20/5fszgXeOxmL3Wdv.webp  "Optional title attribute"
    ![Alt text][img id]

预览：

---

[img id]: https://s2.loli.net/2024/08/20/5fszgXeOxmL3Wdv.webp "Optional title attribute"

![Alt text][img id]

---

<a id="strikethrough"></a>

### 删除线

HTML 标签：`<del>`

这是一个扩展。

GFM 增加了删除线的语法。

代码：

```
~~Mistaken text.~~
```

预览：

---

~~Mistaken text.~~

---

<a id="miscellaneous"></a>

## 杂项

<a id="automatic-links"></a>

### 自动链接

Markdown 支持一种快捷方式，为 URL 和邮箱地址创建"自动"链接：只需用尖括号包裹 URL 或邮箱地址即可。

代码：

    <http://example.com/>

    <address@example.com>

预览：

---

<http://example.com/>

<address@example.com>

---

GFM 会自动链接标准 URL。

代码：

```
https://github.com/emn178/markdown
```

预览：

---

https://github.com/emn178/markdown

---

<a id="backslash-escapes"></a>

### 反斜杠转义

Markdown 允许你使用反斜杠转义来生成字面字符，否则这些字符在 Markdown 的格式语法中有特殊含义。

代码：

    \*literal asterisks\*

预览：

---

\*literal asterisks\*

---

Markdown 为以下字符提供反斜杠转义：

| 字符 | 含义 |
|------|------|
| \\   | 反斜杠 |
| \`   | 反引号 |
| \*   | 星号 |
| \_   | 下划线 |
| \{\} | 花括号 |
| \[\] | 方括号 |
| \(\) | 圆括号 |
| \#   | 井号 |
| \+   | 加号 |
| \-   | 减号 |
| \.   | 句点 |
| \!   | 感叹号 |
| \|   | 竖线 |

---

<a id="inline-html"></a>

## 内联 HTML

Markdown 支持在文档中任意位置使用原始的 HTML。绝大多数 Markdown 解析器都会原样保留 HTML 标签，不进行转义。这意味着你可以直接使用 HTML 来实现 Markdown 本身不支持的复杂排版，例如嵌入视频、表单或更精细的样式控制。

示例：

    <div style="color: red;">
      这是一段 <strong>红色加粗</strong> 的文字。
    </div>

预览：

---

<div style="color: red;">
  这是一段 <strong>红色加粗</strong> 的文字。
</div>

---

注意：在 HTML 块内部，Markdown 语法通常不会被解析，会被当作纯文本处理。
