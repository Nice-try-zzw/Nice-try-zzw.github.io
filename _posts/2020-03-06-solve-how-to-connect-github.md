---
layout:     post                    # 使用的布局（不需要改）
title:      "成功解决国内登录github？"               # 标题 
subtitle:   "What happened" #副标题
date:       2020-03-05              # 时间
author:     "Nice_try"                      # 作者
header-img: "img/blog03.jpg"    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
    - blog
    - 经验
---

**下面是事情脉络（非解决方法）**  
在昨天pull和push的时候   试了很多次  都是无法连接到github（github desktop）  
后来我把库在本地保存了然后remove  
尝试重新clone的时候  
又开始报错（试了不少次）  
没得办法  去官网修改试试  
报错：连接超时  
然后就开始了 百度大法  
记得之前我修改了hosts文件  
而且修改了之后速度是真好  
然后我又尝试去看看hosts有没有更新  
还别说   真有变化   但手动更新后  仍是报错   
更新完DNS缓存后也是超时  
**直到昨天我把我修改的hosts文件内容给删了**（解决方法）  
而且速度杠杠的  
不知道为啥

本人在hosts（默认位置是C:\Windows\System32\drivers\etc）添加内容是（修改需要管理员权限）   
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200306082211488.png)
后来把这些为了提升连接github的速度而添加的内容删了  
在cmd中输入ipconfig /flushdns（记得更新）   
流畅进入github官网 

>若干小时后反馈：出现了一次连接超时  且当时ping也请求超时了  在我执行一次更新缓存后  勉强登上了网站
