---
title: Hexo文章加密插件：hexo-blog-encrypt
date: 2024-03-04 20:26:02
categories:
  - hexo博客
tags:
top:
---
1、安装插件
首先运行以下命令，安装设置密码所需要的插件：
```
npm install hexo-blog-encrypt
```
如果安装不成功，可能是nodejs的版本过低。
最新下载地址：https://nodejs.org/download/
<!--more-->
2、修改配置
在根目录的配置文件_config.yml中添加以下代码：
```
encrypt:
  enable: true
```
3、博客文章添加加密字段
设置加密之后，不要忘记在新建博文的时候，在头部添加加密的设置信息：
```
password: 设置的密码
abstract: 摘要中密码提示内容
message: 输入密码界面提示说明
wrong_pass_message: 输入密码错误的提示内容
```
如果插件已优化（汉化），则博文头部添加密码即可：
```
password: 设置的密码
```
4、对博文禁用加密
只需要将博文头部的 password 设置为 `""` 即可取消加密.

5、插件优化（汉化）
修改以下文章内容：
```
\node_modules\hexo-blog-encrypt\lib\hbe.js
      hideButton.textContent = '重新加密文章';

\node_modules\hexo-blog-encrypt\index.js

const defaultConfig = {
  'abstract': '文章已被加密，请不要打开查看！',
  'message': '请在这里输入密码！',
  'theme': 'default',
  'wrong_pass_message': '抱歉, 这个密码看着不太对, 请再试试！',
  'wrong_hash_message': 'OOPS, these decrypted content may changed, but you can still have a look.',
  'silent': false,
};
```