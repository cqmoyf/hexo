title: 利用GitHub实现电脑间同步Blog源文件
date: 2016-04-26 17:43:38
tags: [Github]
categories:
---
## 利用GitHub实现电脑间同步Blog源文件
1. 在github下建立一个新的repository ，名叫hexo（与hexo文件夹名一样即可）。
2. 在本地进入hexo文件夹，用命令git init创建仓库
<!--more-->
3. 设置远程仓库地址，并更新  
  
  ```
  git remote add origin git@github.com:cqmoyf/hexo.git
  git pull origin master
  ```

4. 修改.gitignore文件（如果没有，请创建），在里面加入public/和.deploy/，因为这两个文件夹是每次generate和deploy都会更新，对我们没用，因此忽略这两个文件的更新。tips:此处最好不要用windows自带记事本打开，因为默认的回车符不一样，会导致无法生效，可以使用sublime或notepad。

5. 使用命令git add .，将所有文件提交到缓存区。

6. 使用命令git commit -m "add all files" ，将这些文件提交到本地仓库。

7. 使用命令git push origin master，将本地仓库的改动推送到github仓库。

现在在任何一台电脑，只需要  
git clone https://github.com/cqmoyf/hexo.git，  
就可以将hexo的源文件复制到本地了。  
之后，当写博客后，只需要git add .  
再git commit -m  
再git push origin  
即可提交到远程仓库。  
当远程仓库有更新时，使用git pull origin master或者git fetch就可以同步代码到本地了。

参考资料:  
[使用GitHub来管理博客源文件][1]
[1]: http://wuchong.me/blog/2014/01/17/use-github-to-manage-hexo-source/