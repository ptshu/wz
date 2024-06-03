---
title: gitee与github上传Hexo必须修改的文件
date: 2023-11-08 11:51:46
categories:
  - hexo博客
tags: 
  - Hexo
  - gitee
  - github
top:
---
上传之前一定要先修改这两个文件，并且git运行以下命令！
```
github:
git config --global user.name "ptshu"
gitee:
git config --global user.name "ptsh"
```
<!--more-->
根目录\
文件：_config.yml
内容：
```
（135/136行）
valine:
  enable: true # if you want use valine,please set this value is true
  appId: 5eQydp6vwosFE2SwAQvpHOPW-gzGzoHsz # leancloud application app id
  appKey: aBcvJDFuxMP9XFjAojz3SCaN # leancloud application app key
```


根目录\themes\BlueLake（主题目录）
文件：_config.yml
内容：
```
（16行）
url: https://ptsh.gitee.io/  

（106行）
deploy:
  type: git
  repository: git@gitee.com:ptsh/ptsh.git
  branch: master
```


