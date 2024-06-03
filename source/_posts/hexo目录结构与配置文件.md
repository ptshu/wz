---
title: hexo目录结构与配置文件
categories:
  - hexo博客
tags:
  - hexo
  - 博客
date: 2023-11-09 21:10:22
top:
---
# 目录结构
## 工程目录
```
├── .deploy		# 需要部署的文件
├── node_modules	# Hexo插件
├── public		# 生成的静态网页文件
├── scaffolds		# 模板
├── source		# 博客正文和其他源文件, 404 favicon CNAME 等都应该放在这里
|   ├── _drafts		# 草稿
|   └── _posts		# 文章
├── themes		# 主题
├── _config.yml		# 全局配置文件
└── package.json
```
<!--more-->
其中scaffolds,source,themes,_config.yml常用。

## 主题目录
```
├── languages		# 国际化
|   ├── default.yml	# 默认
|   └── zh-CN.yml	# 中文
├── layout# 布局
|   ├── _partial	# 局部的布局
|   └── _widget		# 小挂件的布局
├── script		# js脚本
├── source		# 源代码文件
|   ├── css		# CSS
|   |   ├── _base	# 基础CSS
|   |   ├── _partial	# 局部CSS
|   |   ├── fonts	# 字体
|   |   ├── images	# 图片
|   |   └── style.styl	# style.css
|   ├── fancybox	# fancybox
|   └── js		# js
├── _config.yml		# 主题配置文件
└── README.md		# 主题介绍
```
# 配置文件
## 工程配置文件
```
# Site 				# 站点信息
title: DUA'S BLOG		# 标题
subtitle: welcome		# 副标题
description: bug everywhere 	# 描述
author: dua 			# 作者
language: zh-Hans 		# 语言
timezone: Asia/Shanghai 	# 时区

# URL 				# 链接格式
url: http://www.cloudghost.cn/  # 网址
root: /				# 根目录
permalink: post/:title.html	# 文章的链接格式
permalink_defaults:

# Directory 			# 目录
source_dir: source		# 源文件
public_dir: public		# 生成的网页文件
tag_dir: tags 			# 标签
archive_dir: archives 		# 归档
category_dir: categories 	# 分类
code_dir: downloads/code
i18n_dir: :lang 		# 国际化
skip_render:

# Writing 			# 写作
new_post_name: :title.md	# 新文章标题
default_layout: post		# 默认模板
titlecase: false 		# 标题转换成大写
external_link: true 		# 新标签页里打开连接
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight: 			# 语法高亮
  enable: true
  line_number: false 		# 显示行号
  auto_detect: false
  tab_replace:
 
# Home page setting		# 主页设置
index_generator:
  path: ''			# blog index page 的根目录 默认为''
  per_page: 10 			# 每页文章数
  order_by: -date 		# 排序方式 默认按日期降序
  
# Category & Tag 		# 分类和标签
default_category: uncategorized	# 默认分类
category_map:
tag_map:

# Date / Time format 		# 日期时间格式
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination			# 分页
per_page: 20			# 每页文章数, 设置成 0 禁用分页
pagination_dir: page

# Extensions			# 插件和主题
# # 插件: http://hexo.io/plugins/
# # 主题: http://hexo.io/themes/
theme: next

# Deployment			# 部署, Duadua是用户名 
deploy:
  type: git
  repository: git@github.com:Duadua/Duadua.github.io.git
  branch: master

# Disqus			# Disqus评论系统
disqus_shortname: 

# Plugins			# 插件
plugins:			# 插件，例如生成 RSS 和站点地图的
- hexo-generator-feed
- hexo-generator-sitemap
```
## 主题配置文件
```
menu:				# 菜单
  home: /			# 首页
  archives: /archives		# 归档
  about: /about			# 关于
  # commonweal: /404.html	# 公益404
  # tags: /tags			# 标签
  # categories: /categories	# 分类
# # 经典介绍配置
# 小图标
favicon: /favicon.ico

# 默认关键词
keywords: 

# 留空使用默认的, false 禁用, 也可以写指定的地址
rss:

# Icon fonts
# default | linecons | fifty-shades | feather
icon_font: default

# 代码高亮主题 https://github.com/chriskempson/tomorrow-theme
# normal | night | night eighties | night blue | night bright
highlight_theme: normal

# MathJax Support # 数学公式
mathjax: true

# Schemes # 启用主题中的主题Mist
scheme: Mist

# 侧边栏
#  - post    只在文章页面显示
#  - always  所有页面显示
#  - hide    隐藏
sidebar: always

# 自动滚动到"阅读更多"标记的下面
scroll_to_more: true

# 自动给目录添加序号
toc_list_number: true

# 自动截取摘要
auto_excerpt:
  enable: false
  length: 150

# Lato 字体
use_font_lato: true

# Make duoshuo show UA
# user_id must NOT be null when admin_enable is true!
# you can visit http://dev.duoshuo.com get duoshuo user id.
duoshuo_info:
  ua_enable: true
  admin_enable: false
  user_id: 0
  # admin_nickname: ROOT

# # DO NOT EDIT THE FOLLOWING SETTINGS
# # UNLESS YOU KNOW WHAT YOU ARE DOING

# 动画
use_motion: true

# Fancybox 看图插件
fancybox: true

# Static files
vendors: vendors
css: css
js: js
images: images

# Theme version
version: 0.4.5.1
```