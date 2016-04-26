title: Mac下搭建Hexo博客教程
date: 2016-04-26 17:19:58
tags: [Hexo,Github]
categories:
---
1. 安装Git   
` brew install git #Mac电脑使用brew安装 `
2. 安装Node.js
网上有些教程说是用brew安装可能会出问题，所以我直接到官网下载安装
<!--more-->
[下载地址](https://nodejs.org/en/download/)  
使用以下命令验证是否安装成功

  ```
  node -v  
  npm -v 
  ```
3. 安装hexo  
  刚开始使用命令  
  
  ```
  npm install -g hexo-cli
  ```
  进行安装产生以下报错信息
  
	```
	npm ERR! tar.unpack untar error /Users/my/.npm/hexo-cli/1.0.1/package.tgz
	npm ERR! Darwin 15.4.0
	npm ERR! argv "/usr/local/bin/node" "/usr/local/bin/npm" "install" "-g" "hexo-cli"
	npm ERR! node v4.4.3
	npm ERR! npm  v2.15.1
	npm ERR! path /usr/local/lib/node_modules/hexo-cli
	npm ERR! code EACCES
	npm ERR! errno -13
	npm ERR! syscall mkdir
	
	npm ERR! Error: EACCES: permission denied, mkdir '/usr/local/lib/node_modules/hexo-cli'
	npm ERR!     at Error (native)
	npm ERR!  { [Error: EACCES: permission denied, mkdir '/usr/local/lib/node_modules/hexo-cli']
	npm ERR!   errno: -13,
	npm ERR!   code: 'EACCES',
	npm ERR!   syscall: 'mkdir',
	npm ERR!   path: '/usr/local/lib/node_modules/hexo-cli',
	npm ERR!   fstream_type: 'Directory',
	npm ERR!   fstream_path: '/usr/local/lib/node_modules/hexo-cli',
	npm ERR!   fstream_class: 'DirWriter',
	npm ERR!   fstream_stack: 
	npm ERR!    [ '/usr/local/lib/node_modules/npm/node_modules/fstream/lib/dir-writer.js:35:25',
	npm ERR!      '/usr/local/lib/node_modules/npm/node_modules/mkdirp/index.js:47:53',
	npm ERR!      'FSReqWrap.oncomplete (fs.js:82:15)' ] }
	npm ERR! 
	npm ERR! Please try running this command again as root/Administrator.
	
	npm ERR! Please include the following file with any support request:
	npm ERR!     /Users/my/npm-debug.log
	```
	后来在官网去看了看加上sudo后可以正常安装。
4. 配置hexo目录  
在电脑上你愿意的一个位置建立一个文件夹，名字任意，然后在该目录下执行以下指令  
hexo init   
npm install #初始化依赖  
hexo g #根据当前目录下文件生成静态网页  
hexo s #启动服务器  
就可以在浏览器中输入localhost:4000查看本地博客了。要注意的是，所有的hexo指令都必须在你所建立的目录下执行。  
5. 配置SSH keys
首先，打开的你终端（Mac），输入如下代码：  
` cd \~/. ssh `  
这行代码能够帮助你检查电脑上现有的SSH key。  
如果提示：No such file or directory说明没有key文件，输入以下代码生成新的key文件：
` ssh-keygen -t rsa -C "邮件地址@youremail.com" `
这里的邮件地址填自己注册时的邮件地址，注意大小写，双引号不能省略，终端会返回代码让你确定文件名及加密串，一路回车就好。
找到本机上的id_rsa.pub文件，打开它（建议使用Sublime Text）复制里面的代码，记得不要多复制空格或换行，添加到github和coding

6. 配置config.yml  
修改config.yml最下方的  
type:github  
repo:自己的仓库。  
然后运行

```  
npm install hexo-deployer-git --save  
hexo d  
```
就会上传到github  