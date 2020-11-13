---
layout: categories
title: Markdown文本和排版
author: jianxiaochong
date: 2020-08-08 11:33:00 +0800
categories: [Blogging, Demo]
tags: [typography]
math: true
image: /assets/img/sample/devices-mockup.png
---

这个Jekyll模板完全兼容Markdown语法。现在，让我们看看文本和排版。

## 标题

---

# H1

<h2 data-toc-skip>H2</h2>

<h3 data-toc-skip>H3</h3>

<h4>H4</h4>

---

## 段落

我似浮云独自游

悠然溪谷群山中，

霎时美景入bai眼帘，

金色水仙朵朵开，

遍布湖畔树bai荫下，

摇曳风中舞翩翩，

璀璨漫漫如繁星。

## 列表

###有序列表

1.第一项

2.第二项

3.第三项



### 无序列表

- item 1
	- sub item 1
	- sub item 2

- item 2

## 整块引用

>此行显示块引号。

## 表格

|公司|联系人|国家|
|:-----------------------------|:-----------------|--------:|
|Nike | 耐克 |美国|
|Adidas|阿迪达斯|德国|
|Huiwei| 华为|中国|

## 链接

<http://127.0.0.1：4000>

## 脚注

Click the hook will locate the footnote[^footnote].

## 图像

![Desktop View](/assets/img/sample/mockup.png)

## 内联代码

这是一个例子`Inline Code`

## 数学

The mathematics powered by [**MathJax**](https://www.mathjax.org/):

$$ \sum_{n=1}^\infty 1/n^2 = \frac{\pi^2}{6} $$

When \\(a \ne 0\\), there are two solutions to \\(ax^2 + bx + c = 0\\) and they are

$$ x = {-b \pm \sqrt{b^2-4ac} \over 2a} $$

## 代码段

### 普通

```

这是一个常见的代码片段，没有语法突出显示和行号。

```

### 特定语言

#### console

```
$ date
Sun Nov  3 15:11:12 CST 2019
```


####

```terminal
$ env |grep SHELL
SHELL=/usr/local/bin/bash
PYENV_SHELL=bash
```

#### Ruby

```
def sum_eq_n?(arr, n)
  return true if arr.empty? && n == 0
  arr.product(arr).reject { |a,b| a == b }.any? { |a,b| a + b == n }
end
```

#### Shell

```
if [ $? -ne 0 ]; then
    echo "The command was not successful.";
    #do the needful / exit
fi;
```

#### Liquid

{% raw %}
```
{% if product.title contains 'Pack' %}
  This product's title contains the word Pack.
{% endif %}
```
{% endraw %}

#### HTML

```
<div class="sidenav">
  <a href="#contact">Contact</a>
  <button class="dropdown-btn">Dropdown
    <i class="fa fa-caret-down"></i>
  </button>
  <div class="dropdown-container">
    <a href="#">Link 1</a>
    <a href="#">Link 2</a>
    <a href="#">Link 3</a>
  </div>
  <a href="#contact">Search</a>
</div>
```

**Horizontal Scrolling**

```
<div class="panel-group">
  <div class="panel panel-default">
    <div class="panel-heading" id="{{ category_name }}">
      <i class="far fa-folder"></i>
      <p>This is a very long long long long long long long long long long long long long long long long long long long long long line.</p>
      </a>
    </div>
  </div>
</div>
```




## 反脚注



[^footnote]：脚注源。
