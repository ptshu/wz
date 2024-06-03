---
title: hexo d 上传错误
date: 2024-06-02 19:52:47
categories:
  - hexo博客
tags:
top:
---
hexo d 上传提示错误如下：
Fingerprint:
SHA256:hsN3FpUinGIRpww5UI4YXk4YD/GdIpm5eRoY69NiPEI

fatal: Could not read from remote repository.
<!--more-->
Fingerprint:
SHA256:hsN3FpUinGIRpww5UI4YXk4YD/GdIpm5eRoY69NiPEI

fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
FATAL Something's wrong. Maybe you can find the solution here: https://hexo.io/docs/troubleshooting.html
approve

原因：
您的SSH密钥未经验证
最近的扫描发现了有效的SSH私钥，xx20231026，链接到您的GitHub帐户在提交的内容.为了保护您的数据免受任何未经授权的访问，我们已经撤销了它，因此，您对GitHub的SSH访问可能会中断。

解决方法：
登录github后，approve批准SSH密钥或者生成一个新的SSH密钥