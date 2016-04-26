title: Hexo发表文章中文分类或中文标签设置
date: 2015-12-24 17:12:01
tags: Hexo
categories:
---
在我们编辑文章的时候，直接在categories:项填写属于哪个分类，但如果分类是中文的时候，路径也会包含中文。
比如分类我们设置的是：
> categories: 编程
那在生成页面后，分类列表就会出现编程这个选项，他的访问路径是：
> */categories/编程
如果我们想要把路径名和分类名分别设置，需要怎么办呢？
<!--more-->
打开根目录下的配置文件_config.yml，找到如下位置做更改：

```
# Category & Tag
default_category: uncategorized
category_map:
	编程: programming
	生活: life
	其他: other
	中文分类: 英文分类
tag_map:
    中文标签: 英文标签
```
在这里category_map:是设置分类的地方，每行一个分类，冒号前面是分类名称，后面是访问路径。
可以提前在这里设置好一些分类，当编辑的文章填写了对应的分类名时，就会自动的按照对应的路径来访问。
