---
title: 如何写一篇新文章
author: jianxiaochong
date: 2020-08-08 14:10:00 +0800
categories: [博客、教程]
tags: [writing]
---

## 命名和路径

创建一个名为`YYYY-MM-DD的新文件-标题.扩展名`并将其放在根目录的“_post/”中。请注意，“EXTENSION”必须是“md”和“markdown”之一。从“v2.4.1”开始，您可以在“_posts/”下创建子目录来对文章进行分类。

## 前题

基本上，你需要填充，如下图所示：[正面内容](https://jekyllrb.com/docs/front-matter/)

```yaml
---
title: TITLE #标题
date: YYYY-MM-DD HH:MM:SS +/-TTTT #时间
categories: [TOP_CATEGORIE, SUB_CATEGORIE] #顶级类别，次级类别
tags: [TAG]     #标记名应始终为小写
---
```

> **注**：posts的***layout***默认设置为`post`，因此不需要在Front Matter block中添加变量***layout***。

### date (日期时区)

为了准确记录帖子的发布日期，您不应该只设置`_配置yml`但也要在前面的“date”字段中提供邮政的时区。格式：`+/-TTTT`，例如`+0800`。

###  Categories and Tags (类别和标记)

每个帖子的“categories”设计为最多包含两个元素，“tags”中的元素数量可以是零到无穷大。

属于同一*类别*/*标签*的帖子列表记录在单独的页面上。同时，这些*category*/*tag*type页面的数量等于所有帖子的“categories`/`tags”元素的数量，这意味着这两个数字必须完全相同。

例如，假设有一个帖子前面有一个内容：

```
类别：【动物、昆虫】
标签：蜜蜂
```

那么我们应该在根目录的“categories”文件夹中放置两个*category*类型的页面，并在根目录的“tags”文件夹中放置一个*tag*type页面：

```
.
├── categories
│   ├── animal.html         # 类别类型页
│   └── insect.html
├── tags
│   └── bee.html            # 标记类型页
...
```
    
而*category*type页面的内容是

```
---
layout: category
title: CATEGORY_NAME        # 例如昆虫
category: CATEGORY_NAME     # 例如昆虫
---
```

*tag*type页面的内容是

```
---
layout: tag
title: TAG_NAME             # 例如蜜蜂
tag: TAG_NAME               # 例如蜜蜂
---
```

随着帖子数量的增加，类别和标签的数量将增加数倍！如果我们仍然手动创建这些*category*/*tag*类型的文件，这显然是一项非常耗时的工作，而且很可能会错过其中的一些文件，例如，当您从帖子或其他地方单击丢失的“category”或“tag”链接时，浏览器会向您投诉“404找不到”。好消息是我们有了一个可爱的脚本工具``u scripts/sh/create_页码.sh`完成无聊的任务。基本上我们会通过`运行.sh`, `建筑.sh`, `部署.sh`或者`发布.sh`放在“tools/”中而不是单独运行它。查看它的用例[这里]（{{“/posts/gettingstarted/#deployment”| relative_url}}）。

## 上次修改日期

根据帖子的最新git提交日期获取帖子的最后修改日期，所有帖子的修改日期设计为存储在``u data文件中/更新.yml`. 则该文件的内容可能如下：

```
-
  filename: getting-started             # 没有日期和扩展名的post文件名
  lastmod: 2020-04-13 00:38:56 +0800    # 上次修改日期
-
  ... 
```

您可以选择手动创建此文件，但更好的方法是让它由脚本工具自动生成，并使用``u scripts/sh/dump_上一个mod.sh`生下来就是为了这个！类似于其他脚本（`create_页码.sh`)上面提到过，它也是从其他高级工具调用的，所以不必单独使用。

当某些帖子自发布日期起被修改，并且文件``u数据/更新.yml`如果创建正确，则桌面视图的右侧面板中将显示一个标签为**最近更新**的列表，其中记录了最近修改的五篇文章。

## 目录

默认情况下，**T**table**o**f**C**contents（TOC）显示在公告的右侧面板上。如果要全局关闭，请转到`_配置yml`并将变量“toc”的值设置为“false”。如果要关闭特定帖子的TOC，请将以下内容添加到post的[Front Matter](https://jekyllrb.com/docs/front-matter/):

```
---
toc: false
---
```


## 评论

与TOC类似，研究(https://discus.com/)默认情况下，在每个post中加载comments，全局开关由file中的变量“comments”定义`_配置yml` . 如果要关闭特定帖子的评论，请将以下内容添加到帖子的**首页**中：

```
---
comments: false
---
```


## 数学

出于网站性能的原因，默认情况下不会加载数学特性。但它可以通过以下方式实现：

```
---
math: true
---
```

## 预览图像

如果要将图像添加到文章内容的顶部，请通过以下方式指定图像的url：

```
---
image: /path/to/image-file
---
```


## 固定柱

您可以将一个或多个帖子固定在主页的顶部，固定的帖子将根据发布日期按相反的顺序排序。启用方式：

```
---
pin: true
---
```

## 代码块

Markdown symbols<code class=“highlighter rouge”>```</code>可以轻松地创建代码块，如下例所示。

```
这是一个常见的代码片段，没有语法突出显示和行号.
```

## 特定语言

使用<code class=“highlighter rouge”>``语言</code>可以得到带有行号和语法突出显示的代码片段。

>**注意**：此主题中不允许使用`{% raw %}{%{% endraw %} highlight LANGUAGE {% raw %}%}{% endraw %}` 或者 `{% raw %}{%{% endraw %} highlight LANGUAGE linenos {% raw %}%}{% endraw %}！

```
# Yaml code snippet
items:
    - part_no:   A4786
      descrip:   Water Bucket (Filled)
      price:     1.47
      quantity:  4
```

#### Liquid Codes

如果要显示**Liquid**代码段，请用`{%raw%}{%endraw%}raw{%raw%}%}{%endraw%}`和{%raw%}{%endraw%}{%raw%}%}{%endraw%}{%endraw%}`.

{% raw %}
```liquid
{% if product.title contains 'Pack' %}
  This product's title contains the word Pack.
{% endif %}
```
{% endraw %}


## 了解更多

有关Jekyll帖子的更多信息，请访问[Jekyll Docs:posts](https://jekyllrb.com/docs/posts/).

