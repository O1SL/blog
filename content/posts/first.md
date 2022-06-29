---
title: "利用Hugo、GitHub、Vercel搭建个人博客"
summary: "搭建一个方便、免费的个人博客"
date: 2022-06-29T10:48:09+08:00
lastmod: 2022-06-29T10:33:37+08:00
draft: false
author: ["WuJunlin"]
tags: 
- Hugo
- Blog
- Github
- Vercel
# description: "搭建一个便于维护、免费的个人博客"
weight:  # 输入1可以顶置文章，用来给文章展示排序，不填就默认按时间排序
comments: false
cover:
    image: "https://icon-1302751266.cos.ap-chengdu.myqcloud.com/%E5%88%A9%E7%94%A8Hugo%E3%80%81GitHub%E3%80%81Vercel%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/cover.png"
    caption: ""
    alt: ""
    relative: false
---
### 前言

之前在少数派上看过一些关于个人博客的文章，心里也有想法搭建个人博客，做一片自留地，来养成自己输出内容、记录生活的习惯，可以是生活感想、观影阅读、可以是业余爱好记录等等。

网站生成方式上，有Wordpress、Hugo、Hexo、Jekyll等一系列方案，网上的入门教程也都比较容易找。

> - Wordpress，老牌建站工具，我在没有搭建博客的时候就听过它的大名，但是它对于个人博客来说就属于杀鸡用牛刀了，可以但是没有必要，毕竟我只需要一些静态页面
> - Hugo、Hexo、Jekyll等我看来都差不多，都比较适合个人的搭建轻量博客

最终选择了Hugo作为我的博客方案，Hugo是一款由Go语言实现的静态网站生成器，编译速度快，简洁。

在部署方式上，我没有选择把博客放在云服务器上，采用了免费的静态网站托管服务，在这个领域也有很多平台。

> - GitHub Pages，大名鼎鼎，但是处于半墙状态，国内访问不是很方便，pass
> - Gitee Pages，国内版GitHub，但是托管个静态网站竟然要我上传身份证正反面以及手持身份证正反面照片！强烈谴责，pass
> - 国内的各家云服务，阿里云、腾讯云，包括腾讯收购的Coding Pages等都有托管服务，可以按需选用

最终使用了一家叫Vercel的服务提供商，来托管我的博客，国内访问速度尚可。不过托管服务是很容易可以更换的，在整个搭建链路中不是特别重要，很容易更换到其他托管服务提供商。

### 最终链路

![chain](https://icon-1302751266.cos.ap-chengdu.myqcloud.com/%E5%88%A9%E7%94%A8Hugo%E3%80%81GitHub%E3%80%81Vercel%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/blod_chain.png#center)

经过两天的摸索，实现了如上图的链路：在本地编辑markdown格式的博客文档，然后利用vscode推送变更到GitHub项目，GitHub项目的更新会自动触发Vercel项目的更新和自动构建，最终更新到博客网站上。在本地完成编辑推送后，约10s，就可以完成整个链路，实现网站内容更新。

### 实现过程

#### Hugo
待续