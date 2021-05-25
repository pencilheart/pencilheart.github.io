---
title: Blog中插入音乐、视频、图片（Hexo+Next）
date: 2020/3/14 13:03:03
tags: 建站
---

<blockquote class="blockquote-center">本着“有官方教程绝不可劲bb”的原则，以下问题官文很好懂的会直接甩链接，接好。</blockquote>

<!-- more -->

本文使用的环境是Hexo4.2和Next7.7.2

{% note default no-icon%}
## 1 音乐
{% endnote %}

{% note success %}
### 1.1 全局音乐
{% endnote %}
这一节总结自[博麓吹笛分](https://hakurei.red/2019/11/25/%E4%B8%BAHexo%E5%8D%9A%E5%AE%A2%E6%B7%BB%E5%8A%A0%E5%85%A8%E5%B1%80APlayer%E6%92%AD%E6%94%BE%E5%99%A8/#Show-me-the-CODE)社和[惶心](https://cloud.tencent.com/developer/article/1157669)两位大佬以及[Aplayer官文](https://aplayer.js.org/#/zh-Hans/?id=%E5%8F%82%E6%95%B0)和[Meting官文](https://github.com/metowolf/MetingJS)，再结合刚学的pjax做个总结，实现全局音乐不停歇。

想要实现全局音乐，首先需要两个插件[Aplayer](https://aplayer.js.org/#/zh-Hans/?id=%E5%8F%82%E6%95%B0)和[Meting](https://github.com/metowolf/MetingJS)。直接将下面代码copy到`\themes\next\layout\_layout.swig` 即可(直接找CDN，无需将插件安装到本地，省事还快，才发现的一大宝藏)：


```html
<!-- require APlayer -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/aplayer@1.10.1/dist/APlayer.min.css">
<script src="https://cdn.jsdelivr.net/npm/aplayer@1.10.1/dist/APlayer.min.js"></script>
<!-- require MetingJS-->
<script src="https://cdn.jsdelivr.net/npm/meting@1.2/dist/Meting.min.js"></script> 

<div class="aplayer" 
data-id="2533852173" 
data-server="netease" 
data-type="playlist" 
data-fixed="true" 
data-autoplay="true" 
data-order="list" 
data-volume="0.7" 
data-theme="#FADFA3" 
date-preload="auto" > 
</div>
```

{% asset_image metingjs.png 选项列表，可自行设置%}

那么要想实现全局页面切换歌不停，就得借助[pjax插件](https://github.com/defunkt/jquery-pjax)。移步[可集成pjax实现跨页面歌不停](https://pencilheart.github.io/2020-03-14-pjax%E5%AE%9E%E7%8E%B0%E6%AD%8C%E6%9B%B2%E6%94%BE%E4%B8%8D%E5%81%9C.html?cache-bust=1584281905370#more)可瞬间解决全局歌停的问题。

### 1.2 blog内音乐

#### 1.2.1 安装[hexo-tag-aplayer插件](https://github.com/MoePlayer/hexo-tag-aplayer)

   `npm install --save hexo-tag-aplayer`

#### 1.2.2 在站点配置文件_config.yml中敲入

```
aplayer:
  meting: true
```

#### 1.2.3 blog中敲入代码`{% raw %}{% meting id, server, type%}{% endraw %}`就可使用 MetingJS 播放器了

```markdown
<!-- 本blog音乐源代码 -->
{% meting "2533852173" "netease" "playlist" %}
```

>`{% raw %}{% meting id, server, type%}{% endraw %}`格式解释:
>* id就是歌曲或播放列表的id，打开音乐的网页地址栏的数字就是id
>* serve就是在`netease, tencent, kugou, xiami, baidu`中选你的平台
>* type就是在`song, playlist, album, search, artist`选对应的类型。


>想高级设置进阶的参见[hexo-tag-aplayer中文文档](https://github.com/MoePlayer/hexo-tag-aplayer/blob/master/docs/README-zh_cn.md)中 **MetingJS 支持 (3.0 新功能)** 栏目


### 1.3 侧边栏音乐（外链，受版权影响）

在\themes\next\layout\_macro\sidebar.swig中加入一行网易云外链，外链链接直接网页访问你的歌单旁边就有。

{% asset_img neteasy.png %}

```markdown
<!--本主页侧边栏音乐的源代码-->
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=298 height=52 src="//music.163.com/outchain/player?type=0&id=4913366898&auto=0&height=32"></iframe>
```

>外链这种方法有个弊端，就是在歌单内播到版权音乐时会自动停止。本来侧边栏也想用上面blog的aplayer插件，但是失败告终，所以侧边栏只能用外链方法将就。

### 1.4 页脚音乐（外链，受版权影响）

代码和上面一样，依然使用外链，只不过目录改为`\themes\next\layout\_partials\footer.swig` ，代码敲在最后一行就可以。

{% note default no-icon%}
## 2 视频（外链）
{% endnote %}

和侧边栏音乐一样，使用外链。


<iframe src="//player.bilibili.com/player.html?aid=5256249&cid=8541950&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>

```markdown
<!--本视频链接的源代码-->
<iframe src="//player.bilibili.com/player.html?aid=5256249&cid=8541950&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
```

b站嵌入代码获取方式如下图：

{% asset_img viedo.png %}

{% note default no-icon%}
## 3 图片
{% endnote %}

借鉴[Hexo官方插图教程](https://hexo.io/zh-cn/docs/asset-folders.html)搞定！

设置站点配置文件_config.yml中post_asset_folder: true，之后在Blog中敲入代码`{% raw %}{% asset_img 文件名.jpg 显示的小标题 %}{% endraw %}`就ok了。

附：

```markdown
<!--上节b站图片的源代码-->
{% asset_img viedo.png %}
```

>不推荐`![](/images/image.jpg)`的方法，说实话，我用了没成功:joy:。

{% note info %}
## 推这篇Blog时遇到的问题
{% endnote %}

[Hexo代码块中含有{}无法显示的解决办法](https://hexo.io/zh-cn/docs/troubleshooting.html) **泄露（Escape）内容** 部分

