---
title: github pages+阿里云域名绑定搭建个人博客
author: 古朋
header-img: post-bg-2015.jpg
tags:
  - github
date: 2017-03-27 14:43:52
---
一直想整出一个个人博客出来玩玩，于是就查了些资料，发现在域名绑定个人博客这一块的资料比较杂，试了很多次才成功，所以写出篇文章供大家更方便的操作。

## 1.获取github pages的ip地址

打开你的电脑的命令行工具，ping你的github地址，忽略“/”后面的路径，比如我的github pages地址是[huyuee.github.io/blog](huyuee.github.io/blog)，那么我需要ping的地址就是huyuee.github.io，如下图：

![image](https://cloud.githubusercontent.com/assets/12147318/24323059/f0607102-11aa-11e7-88ac-7043065de086.png)


我得到了我的github pages的ip地址：151.101.100.133

## 2.配置阿里云域名解析

进入你的阿里云的解析域名列表，选择你想要解析的域名，点击后面的解析。如下图所示：

![image](https://cloud.githubusercontent.com/assets/12147318/24323086/6dc683fc-11ab-11e7-854f-d0db969f43aa.png)


然后点击添加解析，因为我的ip地址是151.101.100.133，所以我添加了两条解析记录。如下图所示：

![image](https://cloud.githubusercontent.com/assets/12147318/24323066/01644df2-11ab-11e7-9f02-ca3a1544ded8.png)

## 3.配置github pages的custom domain

进入你的github pages的仓库，然后在设置里面将的你的域名的地址，添加到custom domain中，然后保存即可。如下图所示：


![image](https://cloud.githubusercontent.com/assets/12147318/24323070/084fb192-11ab-11e7-8300-39e790b17cdf.png)


设置到这个地方，你现在访问你的域名地址，比如我的是www.huyuee.com。就能看到你的github pages了！
