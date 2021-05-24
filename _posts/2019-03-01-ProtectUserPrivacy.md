---
title: 'Protecting user privacy: an approach for untraceable web browsing history and unambiguous user profiles'
date: 2019-03-1
permalink: /posts/2019/03/protectuserprivacy/
tags:
  - privacy protecting
  - web browing
---


保护用户隐私：一种不可追踪的网络浏览历史和清晰的用户侧写

原文链接[Protecting user privacy: an approach for untraceable web browsing history and unambiguous user profiles](https://arxiv.org/abs/1811.09340)Beigi et al., *WSDM’19*, Arizona State University亚利桑那州立大学

相关论文：[De-anonymizing web browsing data with social networks](https://cs.stanford.edu/~jtysu/2017-04-07.pdf)通过社交网络去网络浏览匿名化 Jessica Su et al., Stanford University

> “除了网络浏览器，用户的历史浏览记录还通过第三方嵌入在网页的跟踪器被记录下来，帮助提高在线广告和网页浏览体验。更多的，网络服务商ISPs，如AT&T Verizon，拥有用户浏览历史的完整权限。FCC's网络隐私保护在2017年3月已经被取缔。新的法律允许ISPs监控，收集，共享和售卖他们用户的在线行为例如详细的网络浏览历史不需要授权和匿名。”

由于缺乏保护，现在需要个体用户保护自己的游览历史。从历史上把进入的信息移走是不可能的，因此唯一能做的是添加噪声。添加噪声使去匿名用户侧写更难，并且可以合理的否认你实际访问了历史上任何给出的链接。但这看起来有点困难，用户并不了解你，但是想到随机不知道的链接会出现在浏览历史上有些不舒适。但是换到对方的角度想想，浏览器插件把你浏览的每个URL反馈给你的社交媒体。我认为很多人对此也会感觉很不舒适。第二点，使用一些个性化来污染历史信息实际是有用的。因此你坑开始查看一些你不太相关的或者不感兴趣的内容。这篇文章通过PBooster系统探索了权衡隐私使用。

> “这篇文章中，我们主要学习以下问题：多少链接和什么链接应该添加到用户的浏览历史中以保护用户隐私的同时保留高可用性。”

如果不考虑客用户仅考虑隐私，随机添加链接是最好的策略，PBooster尝试接近这种结果。

![](/Users/taosuliya/Project/github-page/serea.github.io/images/recipes/PUP/image2.jpeg)

随机链接策略严重的影响的历史的可用性，但是PBooster能够保留大部分的可用性。

![](/Users/taosuliya/Project/github-page/serea.github.io/images/recipes/PUP/image3.jpeg)

## 测量隐私和可用性

##使用PBooster指导隐私与可用性的权衡