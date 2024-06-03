---
title: Hexo使用心得
date: 2022-12-11 20:54:53
categories:
  - hexo博客
tags:
  - Hexo
top: 1
---
# hexo常用命令
<!--more-->
hexo new "name"       # 新建文章
hexo new page "name"  # 新建页面
hexo g                # 生成页面
hexo d                # 部署
hexo g -d             # 生成页面并部署
hexo s                # 本地预览
hexo clean            # 清除缓存和已生成的静态文件
hexo help             # 帮助

# 文件夹目录说明：
node_modules: 依赖包
public：存放生成的页面
scaffolds：生成文章的一些模板
source：用来存放你的文章
themes：主题
文件_config.yml: 博客的配置文件



#  给文章添加分类和模板
通过对文件头部配置信息中tags 与categories项的修改可以设置文章的标签及分类。
其中标签可以按格式贴现设置多个：
title: Hexo博客新建文章并发布 date: 2018-12-06 12:16:12 tags: - Hexo - Markdown categories: 搭建博客
#  添加“阅读全文”按钮
方法一：在文章任意你想添加的位置添加：<!--more-->
此标签以下内容不展示在列表中，收起为阅读全文效果
方法二：设置首页文章以摘要形式显示，打开主题配置文件，找到auto_excerpt进行修改：
auto_excerpt:
enable: true
length: 150
#  在博文中添加图片
目前有二种方法像博文中添加图片：
方法一
(1)在hexo目录下，安装插件：
npm install hexo-asset-image --save
(2)在source 目录下新建一个img文件夹，把图片放置在里面；
(3)在xxx.md文件中引用图片：`![header]( img/header.jpg)`
方法二：
(1)在全局配置文件（hexo/_config.yml)中将post_asset_folder设置为true；
(2)创建文章（在创建的时候，会在hexo/source/_post目录下，生成一个XXX.md文件和一个XXX的文件夹）：
(3)把XXX这个博文需要展示的图片放在XXX文件夹目录下；
(4)在XXX.md文件中引入图片的方式：`{% asset_img example.jpg This is an example image %}`

# 博客菜单显示中文的设置方法：
1、在博客根目录的_config.yml文件中，找到language项改为zh-CN。
2、主题目录的_config.yml文件中，找到language项改为zh-CN。
注：部分主题的_config.yml文件中没有language项的设置。
#  Hexo与Github的网络教程
使用 Hexo+GitHub 搭建个人免费博客教程（小白向）
https://zhuanlan.zhihu.com/p/60578464
5分钟快速 搭建免费好用的图床（Picx +github）
https://blog.csdn.net/weixin_45701199/article/details/125801816
<!--more-->
报错信息hexo YAMLException: can not read a block mapping entry; a multiline key may not be an implicit key
报错信息是提示hexo的yml配置文件 冒号后面少了空格
解决方案：到提示行将对应的空格补上即可
https://blog.csdn.net/qq_39026548/article/details/104729964

Hexo使用攻略-添加分类及标签
https://www.jianshu.com/p/e17711e44e00

Hexo 改变 tag 因为大小写问题而 404 的解决方法
https://blog.zhheo.com/p/5511910d.html
hexo d 上传后about首字母变大写的原因：第一次上传时是大写，覆盖上传还就按第一次的大写写入。解决方法：把文件夹about重命名为其他（如：about2），hexo d 上传，然后再重命名回about，再hexo d 上传就完美解决了。

为你的Hexo加上评论系统-Valine
https://blog.csdn.net/blue_zy/article/details/79071414

GIT PULL 错误：[REMOTE REJECTED] MASTER -> MASTER (PRE-RECEIVE HOOK DECLINED)
解决办法：关闭分支的保护机制
https://www.freesion.com/article/7986556587/


#  HEXO添加置顶功能
目前已经有修改后支持置顶的仓库，可以直接用以下命令安装。(cmd 到博客根目录，nmp运行)
$ npm uninstall hexo-generator-index
$ npm install hexo-generator-index-pin-top
然后在需要置顶的文章的Front-matter中加上top: true即可。

比如下面这篇文章：
---
title: hexo+GitHub博客搭建实战
date: 2017-09-08 12:00:25
categories: 博客搭建系列
top: true
---
到目前为止，置顶功能已经可以实现了。


#  node_modules瘦身方法
首先，说明下node_modules文件夹的作用：下载了npm或gulp的一些插件后，打开node_modules可以发现，里面有很多的文件夹，会导致我们将项目拷贝给别人的时候，传输速度会很慢。在拷贝给别人项目的时候，node_modules这个文件夹是不需要一起拷贝的，因为有package.json、package-lock.json。
package.json记录当前项目所依赖模块的版本信息，更新模块时锁定模块的大版本号（版本号的第一位）。package-lock.json记录了node_modules目录下所有模块的具体来源和版本号以及其他的信息，就不做详细讲解了（相信写代码的一看就能大概明白），也可以参考：https://blog.csdn.net/qq_34295211/article/details/103858589
详细步骤如下：(初次尝试时 请先备份！请先备份！请先备份！)
npm install rimraf -g   		//安装rimraf工具
rimraf node_modules     		//使用rimraf删除node_modules文件
npm cache clean --force		//清除缓存
npm config set registry https://registry.npm.taobao.org	//设置国内镜像，防止下载缓慢卡住
npm  install			//初始化项目

每次上传项目至服务器备份时，删除node_modules文件夹，要修改项目时再重新初始化项目，安装依赖包。

另外，npm prune 命令的功能是根据package.json里的依赖项，删除不需要的模块文件。
执行npm audit fix，可以查看是否少了什么组件

#  极狐GitLab与GitLab的区别
一、产品方面
GitLab 在全球范围内有三个版本：社区版（CE）、企业版（EE）、极狐版 (JH)。极狐GitLab（极狐版JH）是在中国大陆和港澳地区发行的企业级GitLab版本，拥有GitLab技术和品牌独家授权，基于GitLab EE和极狐(GitLab)持有独立知识产权的——JH代码仓库构建，由极狐(GitLab)公司在国内独立运营。
极狐GitLab支持私有化部署（self-managed）版本和SaaS服务。极狐GitLab的企业级订阅许可证、源代码管理、支付系统等均在中国境内管理，受中国法律保护。
二、代码及仓库管理方面
极狐(GitLab)公司与GitLab公司使用两个独立的代码仓，极狐(GitLab)的代码仓存放在中国境内。
GitLab社区版（CE）和企业版（EE）的更改将单向镜像到极狐发行版——极狐GitLab（JH），极狐GitLab版本的更改则会以社区贡献的形式反哺，通过GitLab维护者的审批后合并到GitLab。
三、SaaS 服务方面
极狐GitLab的SaaS服务和GitLab Inc.的SaaS服务（GitLab.com）不共享任何基础设施、网络连接、系统、服务、数据或资源。极狐(GitLab)作为一家独立的中国公司，将在国内管理自己的技术和基础设施。

#  解决需要输入git(或者hexo)的用户名和密码
原因：是因为用 https 协议进行本地仓库和远程仓库的连接，https协议每次都需要进行用户验证，如下修改解决问题，换成ssh方式：
把https://gitee.com/ptsh/ptsh.git
改成git@gitee.com:ptsh/hexo.git
git:在cmd控制台添加或者修改远程仓库命令
添加：git remote add origin git@gitee.com:ptsh/hexo.git
修改：git remote set-url origin git@gitee.com:ptsh/hexo.git
hexo:修改根目录_config.yml配置

deploy:

type: git

repo: git@gitee.com:ptsh/hexo.git （将地址换成自己的地址）

branch: master

更改完远程仓库链接，第一次使用Git的clone或者push命令连接Gitee时，会得到一个警告。
这是因为Git使用SSH连接，而SSH连接在第一次验证Gitee服务器的Key时，需要你确认Gitee的Key的指纹信息是否真的来自Gitee的服务器，输入yes回车即可。Git会输出一个警告，告诉你已经把Gitee的Key添加到本机的一个信任列表里了：这个警告只会出现一次，后面的操作就不会有任何警告了。


#  Valine禁止某页面评论

在 Hexo 博客中，评论的功能在所有页面都默认开启，但是有的时候我们在页面上不需要显示评论功能，例如分类，标记页面我们并不需要评论功能。通过comments属性设置true或false控制该页面或者是文章的评论功能是否打开，如下：
---
title: Tags
date: 2019-12-19 16:10:19
type: "tags"
comments: false
---

#  使用git add 报错
提示错误信息(warning)，报错：
	warning: LF will be replaced by CRLF in.idea/inspectionProfiles/profiles_settings.xml.
	The file will have its original line endings in your working directory
解决方法：
执行git add . 命令之前先执行 以下命令，可成功解决
git config core.autocrlf

# 静态HTML网页部署到github/gitee后中文乱码  
解决方法如下：  
1、将html文件用记事本方式打开  
2、html设置编码utf8的方法：首先打开HTML文件；然后在head之间添加语句  
`<meta http-equiv="Content-Type" content="text/html; charset=utf-8">`  
即可。  
3、点击另存为，跳出另存为界面，最下方有编码选项，选择“UTF-8”，将html文件保存（或直接存为原文件后选替换） 

# hexo的安装、初始化和远程配置
```
npm install hexo-cli -g  # 无法执行 hexo 命令则运行此命令
```
## 应该是hexo没有安装成功，可以尝试使用国内的cnpm来安装，与npm安装hexo的命令一样，将npm改成cnpm即可
安装cnpm
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
npm install hexo-deployer-git --save # 安装git插件
git config --global user.email zskang@qq.com # 设置gitee邮箱（gitee的注册邮箱）
git config --global user.name ‘ptsh’ # 设置用户名（git的注册昵称）
hexo -v # 查询hexo的配置和是否安装成功
```