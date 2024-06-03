---
title: tags与categories的用法
date: 2023-11-07 20:59:52
categories:
  - hexo博客
tags:
  - tags
  - categories
top:
---
在hexo中使用tags与categories往往需要使用多标签和多分类,这里记录一下它们的用法。
# tag用法：
```
tags:
- 123
- 456
tags: [123, 456]
多标签写法，这2种都是一样的效果，用哪个都可以，建议使用列表[]式，直观清晰。
```
<!--more-->
# categories用法：
```
这是默认的写法，给文章添加一个分类。
categories: 123
这会将文章分类123/456子分类目录下。
categories: [123, 456]
这会将文章分类到123/456子分类目录下。
categories:
- 123
- 456
多标签写法，文章被分类到123、456以及123的自分类789这3个分类下面，官方指定写法。
categories:
- [123]
- [456]
- [123, 789]
```
