title: 使用Hexo搭建Github静态博客
date: 2015-12-21 09:29:55
tags: [Github,Hexo]
---

# 环境搭建
## 安装Git
windows下可以安装msysGit
下载地址:http://msysgit.github.io/
1. 安装过程中，询问是否修改环境变量，选择“Use Git Bash Only”. 即只在msysGit提供的Shell中使用.不会去修改本机的环境变量.
2. 配置行结束标记，保持默认“Checkout Windows-style, commit Unix-style line endings”.
3. 其他基本上都是默认,然后"下一步"

## 安装node.js
下载网站：http://nodejs.org/download/
安装时直接保持默认配置即可。
<!--more-->
## 安装Hexo
配置好GitHub仓库后，双击桌面上的Git Shell，输入npm命令即可安装
```
npm install hexo-cli -g
npm install hexo --save

#如果命令无法运行，可以尝试更换taobao的npm源
npm install -g cnpm --registry=https://registry.npm.taobao.org
```
# Hexo配置
## Hexo初始化
在自己喜欢的位置建立目录
如d:\xxx,然后在此文件夹点右键运行Git Bash.在弹出的窗口运行下列命令:
```
$ hexo init
[info] Copying data
[info] You are almost done! Don't forget to run `npm install` before you start blogging with Hexo!
```
Hexo随后会自动在目标文件夹建立网站所需要的文件。然后按照提示，运行 npm install（在 /D/xxx下）
```
npm install
```
会在D:\xxx目录中安装 node_modules。

## 运行Hexo
Start the server
运行下面的命令（在 /D/xxx下）
```
$ hexo server
[info] Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
```
表明Hexo Server已经启动了，在浏览器中打开http://localhost:4000/，这时可以看到Hexo已为你生成了一篇blog。你可以按Ctrl+C 停止Server。
## 发表文章
Create a new post
新打开一个git bash命令行窗口，cd到/D/xxx下，执行下面的命令
```
$ hexo new "My New Post"
[info] File created at d:\xxx\source\_posts\My-New-Post.md
```
刷新http://localhost:4000/，可以发现已生成了一篇新文章 "My New Post"。
## 生成静态页面
Generate static files
执行下面的命令，将markdown文件生成静态网页。
```
$ hexo generate
```
该命令执行完后，会在 D:\xxx\public\ 目录下生成一系列html，css等文件。
## 编辑文章
hexo new "My New Post"会在D:\xxx\source\_posts目录下生成一个markdown文件：My-New-Post.md
可以使用一个支持markdown语法的编辑器（比如 Sublime Text 2）来编辑该文件。
## 部署到Github
部署到Github前需要配置_config.yml文件，首先找到下面的内容
```
# Deployment
## Docs: http://hexo.io/docs/deployment.html
deploy:
  type:
```
然后将它们修改为
```
# Deployment
## Docs: http://hexo.io/docs/deployment.html
deploy:
  type: github
  repository: git@github.com:cqmoyf/cqmoyf.github.io.git
  branch: master
```
NOTE1:
Repository：必须是SSH形式的url（git@github.com:cqmoyf/cqmoyf.github.io.git），而不能是HTTPS形式的url，否则会出现错误
使用SSH url，如果电脑没有开放SSH 端口，会致部署失败。
fatal: Could not read from remote repository.
Please make sure you have the correct access rights
and the repository exists.
NOTE2：
如果你是为一个项目制作网站，那么需要把branch设置为gh-pages。
## 测试
当部署完成后，在浏览器中打开http://cqmoyf.github.io/,正常显示网页，表明部署成功。
## 总结：部署步骤
每次部署的步骤，可按以下三步来进行。
hexo clean
hexo generate
hexo deploy
## 总结：本地调试
1. 在执行下面的命令后，
```
$ hexo g #生成
$ hexo s #启动本地服务，进行文章预览调试
```
浏览器输入http://localhost:4000，查看搭建效果。此后的每次变更_config.yml 文件或者新建文件都可以先用此命令调试，尤其是当你想调试新添加的主题时。
2. 可以用简化的一条命令
hexo s -g
3. 命令总结
1. 常用命令
hexo new "postName" #新建文章
hexo new page "pageName" #新建页面
hexo generate #生成静态页面至public目录
hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy #将.deploy目录部署到GitHub
hexo help  # 查看帮助
hexo version  #查看Hexo的版本
2. 复合命令
hexo deploy -g  #生成加部署
hexo server -g  #生成加预览
命令的简写为：
hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy
#  配置Hexo
在修改_config.yml配置文件时，在冒号:后面需要保留一个空格，请对比一下下面的区别：

错误的设置：
author:xxx
email:XXX@qq.com
language:zh-CN
正确的设置：
author: xxx
email: XXX@qq.com
language: zh-CN

# 安装插件
[sitemap插件](https://github.com/hexojs/hexo-generator-sitemap)




本文在以下文章的基础上修改而成:

 - [Hexo搭建Github静态博客][1]
 - [Windows下Git安装指南][2]


  [1]: http://www.cnblogs.com/zhcncn/p/4097881.html
  [2]: http://www.cnblogs.com/zhcncn/p/3787849.html