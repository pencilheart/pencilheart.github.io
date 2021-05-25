---
title: pjax实现歌曲放不停
date: 2020/3/14 22:36:03
tags: 建站
---
<blockquote class="blockquote-center">谨以此文纪念X一样的我。</blockquote>

<!-- more -->

现在已经实现了[页面内音乐播放](https://pencilheart.github.io/2020-03-14-Blog%E4%B8%AD%E6%8F%92%E5%85%A5%E9%9F%B3%E4%B9%90%E3%80%81%E8%A7%86%E9%A2%91%E3%80%81%E5%9B%BE%E7%89%87%EF%BC%88Hexo+Next%EF%BC%89.html?cache-bust=1584238666378#more)，但是很容易就发现在切换页面时音乐就停了。。。

所以，强迫症患者就找了一下午如何实现跳转页面时音乐不停。先是看很多博文听说了pjax，之后又听说next集成了pjax，就把站点配置文件_config.yml中的pjax打开了，然而，没用。

直到现在！我遇到了[崔庆才老师](https://cuiqingcai.com/7625.html)！！！一语惊醒梦中人！！！

{% asset_img pjax.png 人类之光啊 %}

原来！！！我还没有安装pjax依赖库！瞬间哭了有没有！这回是真的蠢到自己了:joy:

翻开[官文](https://theme-next.org/docs/getting-started/index.html)反思吧，官文写的可是清清楚楚，要下载之后才可使用。。。

{% asset_img next_help.png Next官文 %}

我去学官文了，但愿自己以后长点脑子:dart:

{% note info%}
**后续更新**
{% endnote %}
后面通过翻阅[NEXT官文](https://theme-next.org/docs/third-party-services/external-libraries)，发现相较于下载插件，直接用CDN代理更快更方便。

只需在主题配置文件`_config.yml`中，将`Third Party Plugins & Services Settings`部分的`pjax: true`后，再将`vendors:`中的pjax部分设置为` pjax: https://cdn.jsdelivr.net/npm/pjax@0.2.8/pjax.min.js`即可启用pjax，更加简单快捷。



