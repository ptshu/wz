---
title: valine错误
date: 2024-06-02 19:33:23
categories:
  - hexo博客
tags:
top:
---
valine提示以下错误：
Code 504: The app is archived, please restore in console before use. 
<!--more-->
![](img/2024/06/valine1.png)
原因是：valine超过30天没有使用被停止，存储服务数据已归档（连续30天无API请求）
![](img/2024/06/valine2.png)
解决办法：点上图中的激活，然后等10-30分钟后就激活成功。

