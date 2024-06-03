---
title: 部署Github的Hexo
date: 2022-12-02 19:58:41
categories:
  - hexo博客
tags:
  - GitHub
  - Hexo
top: 
---
#  HEXO博客信息
博客仓库名：ptshu.github.io
#  Hexo连接 Github(博客)
设置用户名和邮箱：
```
git config --global user.name "ptshu"
git config --global user.email "zskang@qq.com"
```
<!--more-->
创建 SSH 密匙：
(如果已经创建了，可以跳过直接用户旧的密匙)
`ssh-keygen -t rsa -C  "zskang@qq.com"`
验证连接：
`ssh -T git@github.com`

#  hexo常用命令
```
hexo new "name"       # 新建文章
hexo new page "name"  # 新建页面
hexo g                # 生成页面
hexo d                # 部署
hexo g -d             # 生成页面并部署
hexo s                # 本地预览
hexo clean            # 清除缓存和已生成的静态文件
hexo help             # 帮助
```



