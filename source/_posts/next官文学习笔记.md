---
title: next官文学习笔记
date: 2020/3/15 15:27:27
tags: 建站
---
<blockquote class="blockquote-center">学习官文，增强自信</blockquote>

<!-- more -->
## note

{% note success %}
Success Header
{% endnote %}

```
<!--源代码-->
{% raw %}
{% note success %}
Success Header
{% endnote %}
{% endraw %}
```

```
<!--格式-->
{% raw %}
{% note [class] [no-icon] %}
Any content (support inline tags too.io).
{% endnote %}

[class]   : default | primary | success | info | warning | danger.
[no-icon] : Disable icon in note.
{% endraw %}
```

## tabs

{% tabs Sixth unique name %}
<!-- tab Solution 1@text-width -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab Solution 2 @amazon -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab Solution 3@bold -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

```
<!--源代码-->
{% raw %}
{% tabs Sixth unique name %}
<!-- tab Solution 1@text-width -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab Solution 2 @amazon -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab Solution 3@bold -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}
{% endraw %}
```

```
<!--格式-->
{% raw %}
{% tabs Unique name, [index] %}
<!-- tab [Tab caption] [@icon] -->
Any content (support inline tags too).
<!-- endtab -->
{% endtabs %}
{% endraw %}
```



## button

{% btn , click, github fa-fw fa-lg, NexT source code %}

```
<!--源代码-->
{% raw %}{% btn , click, github fa-fw fa-lg, NexT source code %}{% endraw %}
```

```
<!--格式-->
{% raw %}
{% button url, text, icon [class], [title] %}
<!-- Tag Alias -->
{% btn url, text, icon [class], [title] %}
{% endraw %}
```