title: 解决 Github Pages 百度收录及国内访问
date: 2015-12-21 11:52:12
tags: [Github,Gitcafe,百度]
---
2016.03.10更新
由于gitcafe被coding收购,所以将原文gitcafe替换为coding.
把博客同时发布到github pages和coding-page ~~gitcafe-pages~~.然后使用dnspod设置域名解析,国内线路解析到coding-page ~~gitcafe-pages~~,国外线路解析到github.
<!--more-->
实现方法
前提是已配置好本地环境.
# 1.  准备条件
一个github账户
一个coding ~~gitcafe~~账户
一个dnspod账号
一个域名
git客户端

# 2. 初始操作
我们在github和coding ~~gitcafe~~上面把自己的博客搭建起来,首先要建仓库.
github:
首先登录你的github,然后新建一个公共仓库,仓库名是你的用户名加上github.io
`yourname.github.io`,我的用户名是cqmoyf

coding ~~gitcafe~~:
操作方法差不多,不过有点区别是,gitcafe新建的公开项目,是和用户名一致的,比如我的用户名是cqmoyf,那我新建的仓库名就是cqmoyf
仓库新建成功后,你获取到的链接应该是类似下面的
```
https://github.com/cqmoyf/cqmoyf.github.io.git
https://gitcafe.com/cqmoyf/cqmoyf.git
```
这就是你的两个page对应的仓库.
# 3. 搭建博客
3.1 搭建github pages
当你的仓库建好了,我们就开始搭建博客,网上文章很多
按照上面的教程一步一步,就能搭建好博客,然后你就可以访问你的gihub pages了,访问链接就是http://yourname.github.io
现在我们开始搭建gitcafe上面的pages了.由于hexo现在已经支持多发布,所以很简单,我们只需要配置deploy的信息,修改_config.yml.添加gitcafe的仓库信息.我的修改结果如下:
```
deploy:
  - type: git
    repo: 'https://github.com/Jackroyal/Jackroyal.github.io.git'
    branch: master
  - type: git
    repo: 'https://gitcafe.com/Jackroyal/Jackroyal.git'
    branch: gitcafe-pages
```
尤其需要注意的是,两个的branch是不同的,github默认分支是`master`,gitcafe默认分支是`gitcafe-pages`.

3.2.  添加gitcafe的ssh公钥
3.2.1.  查看本地公钥
我们打开你使用的git终端,首先切回用户目录,然后进入.ssh目录,里面就有公钥和私钥
我们就是要读取后缀是.pub的那个文件
3.2.1 添加公钥到gitcafe
我们在这里来设置gitcafe的公钥.
PS:需要注意的是,公钥后面的chen@chen-pc是不需要的,我的带上以后,gitcafe说是公钥非法,不过不怕,gitcafe会帮你正确格式化
反正就是把公钥加上去,就ok了
3.4 同步博客到gitcafe
上面的配置好了以后,我们就可以把博客内容同步到gitcafe了,方法很简单,执行
```
hexo d -g
```
然后就可以啦.

# 4. 配置域名
首先你得有个域名
4.1 修改域名注册的解析服务器
我们在要把域名解析服务,设置到dnspod,因为他是国内的,而且服务很好.我们登录自己的域名管理后台,选择对应的域名进行管理,然后找到nameservers的设置
修改的值是
```
f1g1ns1.dnspod.net
f1g1ns2.dnspod.net
```
常见的域名注册商修改到dnspod,官方提供了教程
改完以后可能要等一段时间才能生效,最多72小时
ok,改完以后,这边就完了,我们登录dnspod
4.2 修改dnspod解析记录
我们登录dnspod,然后添加域名
如果4.1中的设置生效了,你的域名就会添加成功了,我们直接进行下一步,修改解析记录
我们一共添加了4条记录,其中一条泛解析和www解析是针对国内的使用默认线路,所以指向gitcafe;1条泛解析和www解析是针对国外的,所以指向github.
就是添加
```
@       CNAME  默认  gitcafe.io.
www     CNAME  国外  cqmoyf.github.io.
www     CNAME  默认  gitcafe.io.
@       CNAME  国外  cqmoyf.github.io.
```

其他设置项目默认就行了,上面的配置完了,如果你走国外ip访问你的域名的话,会出现404,因为我们还差一步.走国内线路访问一样会出错,都是没绑定的结果.
4.3 添加github的CNAME文件,添加gitcafe自定义域名
我们先来配置github的CNAME文件,官网有个教程配置CNAME文件.说白了,就是在你的网站根目录,添加一个名为CNAME的文件,里面的内容就是你的域名
```
cqtjwz.com
```
没有任何多余的信息

上面的配置现在访问没问题,但是你一重新发布博客,就需要重新手动添加CNAME文件,太麻烦.
一劳永逸的方法,在你的hexo目录下的source目录中,新建一个CNAME文件夹,然后他每次在你发布博客的时候,都会在你的网站根目录生成一个CNAME文件.
现在github的配置彻底结束.

接下来配置gitcafe:
我们在gitcafe的项目主页,点击项目设置
然后我们点击pages服务标签,然后添加自己的域名,这些域名是我们之前在dnspod中设置了解析的

#5. 总结
本文内容在以下文章基础上修改而成:
* [解决 Github Pages 禁止百度爬虫的方法](http://bblove.me/2015/11/25/how-to-solve-the-problem-that-github-blocks-the-baidu-spider/)


