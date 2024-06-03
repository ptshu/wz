---
title: 部署Gitee的Git和Hexo
date: 2023-10-29 19:58:41
comments: false
categories:
  - hexo博客
tags:
  - Git
  - Gitee
  - Hexo
top: 
---
#  HEXO博客信息
博客域名：https://ptsh.gitee.io
备份仓库：https://gitee.com/ptsh/hexo/
<!--more-->
# 部署git到Gitee
环境搭建
Hexo 基于 Node.js，搭建过程中还需要使用 npm（Node.js 已带） 和 git，因此先搭建本地操作环境，安装 Node.js 和 Git。
Node.js：https://nodejs.org/zh-cn
Git：https://git-scm.com/downloads
下载 Node.js 和 Git 程序并安装，一路点 “下一步” 按默认配置完成安装。

安装完成后，Win+R 输入 cmd 并打开，依次输入 `node -v、npm -v 和 git -v` 并回车，如下图出现程序版本号即可。
![](img/hjdj.jpg)
 
码云官网:https://gitee.com/

第二步：生成ssh公钥/私钥对。

（1）先查看之前是否已经生成过公钥，私钥对。
打开文件夹 ： C:\Users\用户名.ssh

如果有上面三个文件，说明已经生成过。则不需要再生成。不需执行下面的步骤。可直接从下面的第（4）小步操作。

（2）配置Git的用户名，邮箱名。（注意这里的配置是对Git软件的配置只配置一次即可，第四步的远程仓库是对每个本地仓库的配置，也就是每创建一个git本地仓库都要配置）
```
git config --global user.name "用户名（最好是gitee的用户名）"
git config --global user.email "邮箱（gitee注册的邮箱）"
然后执行下面命令，查看是否配置成功
git config --list
出现配置的结果成功。
注意：按字母键（Q）退出
```


（3）执行生成密钥对命令。
`
ssh-keygen -t rsa -C "邮箱"
`

执行命令，并按回车3下（有提示你是否需要设置密码，所以直接回车跳过，如果设置了每次使用Git会提示输入密码）
然后去C:\Users\用户名.ssh文件夹下会有这三个文件


（4）打开id_rsa.pub的公钥文件，复制里面的内容


（5）打开Gitee的个人设置界面，点击左下方的ssh公钥：
粘贴公钥，填写标题，点击确定。


ssh登录整个详细过程介绍，可参考：
https://www.jianshu.com/p/a3c3628d710b
https://www.jianshu.com/p/9998d4d3ba04
https://blog.csdn.net/qq_23167527/article/details/80614454
https://blog.csdn.net/weixin_42201180/article/details/117809437

第三步：使用git推送到远程库。

（1）在gitee创建仓库

然后，按如下方式创建仓库：

（2）在当前工作目录打开cmd，初始化为git本地库。
这个工作目录是要推送的文件所在的文件夹。
使用命令(注意有个 .)：

`
git init .
`

(3)使用命令查看本地仓库git是否配置过远程仓库。

`
git remote -v
`

（4）没有配置过远程仓库。
打开上面Gitee创建的仓库，按照下图复制ssh地址。

然后，在cmd控制台添加远程仓库命令

```
git remote add origin <你的项目地址> 
//注:项目地址形式为:https://gitee.com/xxx/xxx.git或者 git@gitee.com:xxx/xxx.git
已存在远程仓库，则修改远程仓库命令
git remote set-url origin <你的项目地址>
git remote set-url origin git@gitee.com:ptsh/hexo.git
（项目ptsh存放hexo 博客，项目hexo存放hexo 源文件）
```

克隆远程仓库内容
`git clone git@gitee.com:ptimg/ptimg.git`
克隆远程仓库内容
`git clone git@gitee.com:ptimg/ptimg.git`

（5）最后就是基本的推送命令了。
```
git add .
git commit -m "第一次提交"
git push origin master
```

直接执行push命令会出问题：


因为gitee创建的和本地的不是同一个库，所以冲突。如果使用git clone不会出这个问题。可使用下面的命令解决：

`
git pull origin master --allow-unrelated-histories
`

然后再执行push命令：

`
git push origin master
`

这时执行上面push命令 如果还报错：

则再将本地的文件提交到本地仓库，再到远程仓库，即(orgin是添加在git 的远程仓库名， master是远程仓库当当前所在的分支）：
```
git add .
git commit -m “ptshucn”
git pull origin master --allow-unrelated-histories
git push origin master
```



# 部署Hexo到Gitee
修改根目录_config.yml配置
```
deploy:
type: git
repo: git@gitee.com:ptsh/hexo.git （将地址换成自己的地址）
branch: master
```
然后在blog的根目录执行命令：
```
npm install hexo-cli -g  # 无法执行 hexo 命令则运行此命令
```
安装 hexo 时报错：hexo: command not found
应该是hexo没有安装成功，可以尝试使用国内的cnpm来安装，与npm安装hexo的命令一样，将npm改成cnpm即可
安装cnpm
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
npm install hexo-deployer-git --save # 安装git插件
git config --global user.email zskang@qq.com # 设置gitee邮箱（gitee的注册邮箱）
git config --global user.name ‘ptsh’ # 设置用户名（git的注册昵称）
hexo deploy # 上传到gitee
```
然后选择gitee pages服务，然后选择开启 或 更新即可。

网络教程：使用 Hexo+GitHub 搭建个人免费博客教程（小白向）
https://zhuanlan.zhihu.com/p/60578464

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

