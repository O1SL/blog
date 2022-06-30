---
title: "利用Hugo、GitHub、Vercel搭建博客"
summary: "搭建一个方便、免费的个人博客"
date: 2022-06-29
lastmod: [":git", "date", "publishDate"]
draft: false
author: ["WuJunlin"]
enableCoverzoom: true
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
## 前言

之前在少数派上看过一些关于个人博客的文章，心里也有想法搭建个人博客，做一片自留地，来养成自己输出内容、记录生活的习惯，可以是生活感想、观影阅读、可以是业余爱好记录等等。

网站生成方式上，有Wordpress、Hugo、Hexo、Jekyll等一系列方案，网上的入门教程也都比较容易找。

> - Wordpress，老牌建站工具，我在没有搭建博客的时候就听过它的大名，但是它对于个人博客来说就属于杀鸡用牛刀了，可以但是没有必要，毕竟我只需要一些静态页面
> - Hugo、Hexo、Jekyll等，都是适合个人博客的轻量构建方案，网上有较多的对比，但我主要考虑外观

最终选择Hugo作为我的博客方案，Hugo是一款由Go语言实现的静态网站生成器，编译速度快，简洁。

在部署方式上，我没有选择把博客放在云服务器上，采用了免费的静态网站托管服务，在这个领域也有很多平台。

> - GitHub Pages，大名鼎鼎，但是处于半墙状态，国内访问不是很方便，pass
> - Gitee Pages，国内版GitHub Pages，但是托管静态网站竟然要我上传身份证正反面以及手持身份证正反面照片！强烈谴责，pass
> - 国内的各家云服务，阿里云、腾讯云，包括腾讯收购的Coding Pages等都有托管服务，可以按需选用

最终使用了一家叫Vercel的服务提供商，来托管我的博客，在国外，不过国内访问速度尚可。不过托管服务是很容易可以更换的，在整个搭建链路中不是特别重要，很容易更换到其他托管服务提供商。

## 最终链路

<img loading="lazy" src="https://icon-1302751266.cos.ap-chengdu.myqcloud.com/%E5%88%A9%E7%94%A8Hugo%E3%80%81GitHub%E3%80%81Vercel%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/blod_chain.png" type="" alt="chian" class="medium-zoom-image">

## 实现过程

### Hugo

安装Hugo环境，MacOS下可使用brew安装

```shell
brew install hugo
```

建立站点

```shell
hugo new site new_site
```

然后程序会自动生成相关目录

```shell
▸ archetypes/ #包括内容类型，在创建新内容时自动生成内容的配置
▸ content/    # 网站内容，全部使用markdown格式
▸ layouts/    # 网站模板文件，决定内容如何呈现
▸ static/     # 图片、css、js 等静态资源
▸ themes/     # 存放主题
config.toml   # 是网站的主配置文件
```

本地调试

```shell
hugo server -D
```

然后可以在 [http://localhost:1313/](http://localhost:1313/) 查看博客网站并进行调试

为了博客美观，还需要一个主题，可以去主题网站下载相关文件，然后放在themes目录下，再根据需要修改调试网站样式

### GitHub

GitHub在整个链路中充当一个中间商的角色，作为中转仓库

在GitHub建立一个项目，利用git或者vscode等工具，链接本地环境和远程分支，这样就可以把本地的更新推送到Github中

### Vercel

注册账号后，链接GitHub
<img loading="lazy" src="https://icon-1302751266.cos.ap-chengdu.myqcloud.com/%E5%88%A9%E7%94%A8Hugo%E3%80%81GitHub%E3%80%81Vercel%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/vercel1.png" type="" alt="vercel1" class="medium-zoom-image">

创建新项目并导入上一步在GitHub中创建的项目，相关设置如图
<img loading="lazy" src="https://icon-1302751266.cos.ap-chengdu.myqcloud.com/%E5%88%A9%E7%94%A8Hugo%E3%80%81GitHub%E3%80%81Vercel%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/vercel2.png" type="" alt="vercel2" class="medium-zoom-image">

在第三个部分要注意，需要设置Hugo的版本，不然Vercel会使用低版本来构建，可能会报错失败

<img loading="lazy" src="https://icon-1302751266.cos.ap-chengdu.myqcloud.com/%E5%88%A9%E7%94%A8Hugo%E3%80%81GitHub%E3%80%81Vercel%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/vercel3.png" type="" alt="vercel3" class="medium-zoom-image">

然后点击Deploy开始运行，构建完成后，就可以通过Vercel给出的域名访问博客了，但是为了方便，还可以设置到自己的域名下面。

首先到解析服务提供商处，添加1条域名解析记录，类型为 **_CNAME_** 指向 **_cname.vercel-dns.com._** 再到Vercel的项目设置中绑定域名，值得注意的一点是，设置域名后，需要在Hugo的config文件中将baseURL设置为你的域名，这样就可以实现用自己的域名访问博客了。

至此整个链路基本构建完毕，本文只记录了大致的思路和方向，由于不是一篇教程，所以略去了很多细节，尤其是在Hugo环节，作为一个完全不懂任何前端知识的小白，真的发现有很多坑！

> **最后立一个flag：认真写博客，记录生活**
