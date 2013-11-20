##Git的介绍

Git是一个开源的分布式版本控制系统，用以有效、高速的处理从很小到非常大的项目版本管理。

##Git的安装
>````sudo apt-get install git-core #linux````

##Git的初始化和配置
###配置Git

>````git config --global user.name "wallace liu" #配置本地git账户的姓名````

>````git config --global user.email "wallaceliu@anjuke.com" #配置本地git账户的邮件````

###初始仓库
>````git clone git@git.corp.anjuke.com:site/anjuke-broker anjuke_broker #克隆远程库的代码到本地的anjuke_broker目录````

###创建分支
1. 利用iDeliver创建相应的远程分支

2. 取回远程库上的分支,并创建对应的本地分支(假设:远程分支号pmt16825)

>````git fetch origin #取回远程origin库上的分支和更新````

>````git checkout -b lpmt16825 origin/pmt16825 #创建本地的分支lpmt16825,并取回远程origin库pmt16825分支的代码到本地的lpmt16825分支````

>````git checkout lpmt16825 #切换本地工作的分支到lpmt16825````

###Coding
>````.... (假设:更改readme文件)````

###提交代码到本地仓库和远程仓库
>````git add readme #添加修改到git的暂存区````

>````git commit -m "修改了readme文件" #添加修改到git的本地仓库````  

>````git push origin lpmt16825:pmt16825 #将本地lpmt16825的代码更新到远程origin仓库的pmt16825分支````

###合并分支到主线(假设:当前分支是在lpmt16825)
>````git rebase origin/master #将主线上最新的代码更新到当前分支````

>注1: 这里进行了rebase,可以避免后面master分支中````merge lpmt16825````时产生冲突.

>注2: 如果当前分支和主线对同一个文件进行了修改时,就有可能产生冲突,要先用````git mergetool````解决冲突,然后再用````git rebase --continue````继续进行rebase

>注3: 这里也可以利用````git merge````获取主线的最新更新,但是这样会导致后面主线````merge````了当前分支之后,提交线会变得很难看,不便于以后的代码追踪

>````git push origin lpmt16825:pmt16825 -f #强制更新远程库````

>````git checkout master #切换到master分支````

>````git merge lpmt16825 #合并lpmt16825到master分支,这个步骤已经被在iDeliver中实现,并且个人没有权限进行这个操作````

##Git的一些基本命令
git remote [-v] | add | rm         
git branch [-r d D] | [branchname]
git checkout [-b -t]
git add . | [filename]
git commit [-m a]
git push
git merge
git rebase

