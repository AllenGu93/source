---
title: bootstrap之model填坑
date: 2017-03-23 17:30:33
tags: [bootstrap,model]
---

bootstrap是我最早听说的前端框架，以其简单实用，栅格式布局的响应移动端，一度成为搭建后台乃至前台界面的顶梁柱。 之前看过很多次都没有把模态框(model)搞懂，这次来，就是为了填坑。不搞懂，不睡觉。(立FLAG小王子^_^)

!['picture'](https://raw.githubusercontent.com/AllenGu93/imageForHexo/master/WallpaperStudio10-19166.jpg)

对于这个模态框，我想先从最简单的文档开始，然后追溯他的源码。
<!--more-->

>闲话:现在是凌晨快一点，是惰性最凶猛的时候，和别人差距那么大，骚年，继续吧。

对于bootstrap的基本css不想再在这里絮叨，之后会开一个帖子关于自己带有后台管理的博客系统，那里会着重使用这些强大的框架，完成后台的搭建工作。现在就着眼model，goal:实现model的熟练使用，了解model的核心思想。

版本:bootstrap v3, 参考网址([bootstrap中文网](http://v3.bootcss.com/))

模态框的js是model.js，因为是针对此模块的实验，所以只引用此js，但是因为bootstrap的js全部依赖于jquery，所以在引用model.js之前把jquery引进去，否则找不到原因，会很*疼~
用前须知：

>不支持同时打开多个模态框
>千万不要在一个模态框上重叠另一个模态框。要想同时支持多个模态框，需要自己写额外的代码来实现。


>模态框的HTML代码放置的位置
>务必将模态框的 HTML 代码放在文档的最高层级内（也就是说，尽量作为 body标签的直接子元素），以避免其他组件影响模态框的展现和/或功能。





