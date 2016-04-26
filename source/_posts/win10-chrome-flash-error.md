title: Win10 Chrome flash无法加载的解决办法
date: 2015-12-28 11:20:30
tags: Win10
categories:
---
最近突然Chrome打开网站，很多广告和视频都变成空窗，提示“无法加载插件”（"could't load plugins"）。网上搜索了一下，很多都是说内置的flash没启用或者没有更新到最新。
按照这些文章进行操作，要么找不到相应选项，要么就是没效果。
后来猜测是否与权限有关，经过检查发现Flash插件所在目录没有继承到相应权限。
<!--more-->
解决方案：
找到Flash插件所在目录，其中xxx为用户名
C:\Users\xxx\AppData\Local\Google\Chrome\User Data\PepperFlash
该目录下会有一个以Flash的版本号为名称的文件夹，右击该文件夹，点击“属性”，然后点击“安全”
看一下您登陆系统的用户是否有加载该文件夹的权限。若没有权限，则将当前登陆系统使用的用户添加进去，并赋予完全控制的权限了。
此时Chrome打开网站，应该可以正常显示Flash了！