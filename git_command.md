Git常用命令总结

# diff
- 查看本地修改
>**git diff .** 
>**git --ignore-space-change --ignore-all-space .** //忽略空格的改动，包括格式的改动，比如DOS/UNIX的区别

# 撤销修改有几种类型
## push后的撤销，如果是临时的branch，还没有pull request的，可以删除临时branch，重新拉一个branch，如果已经merge到其它分支了，这种情况下唯一的办法就是重新提交代码，把之前的改动拖动回退，别无它法
## 对于commit之后还没有push的改动，使用git reset --soft HEAD^或者git reset --hard HEAD^，详见下面的解释
## 对于add或者是staged的修改，可以使用git restore --staged来从暂存区回退到工作区
## 对于还在工作区没有到暂存区的，想回退，可以直接git checkout来，不过要小心所有的修改都会被清空

# add
* 把修改从工作区提交到暂存区
* git add . 把当前目录下所有的改动，包括modified,new file都会被提交到暂存区
* 如果只想提交修改过的文件，可以用git add -u .

# commit
- git commit之后想撤销
> **git reset --soft HEAD^**
> 注： 仅仅是撤回commit操作，您写的代码依然保留。不删除工作空间改动代码。
> **git reset --hard HEAD^**
> 注：删除工作空间改动代码

- git commit之后想修改注释
> **git commit --amend**

# checkout
- 没有commit想撤销本地的修改
> **git checkout    .**

# log
- `-n`：指定log输出数量，直接在log命令之后加`-n`参数即可，n表示要输出的数量
>**git log -2**
- `--stat`：是在git log的基础上输出文件增删改的统计数据。
>**git log -2 --stat**
- `-p`：控制输出每个commit具体修改的内容，输出的形式以diff的形式给出
>**git log -1 -p**
- `show`：同git log -p输出类似，只不过它只显示一个commit的内容，如果不指定commit hash, 它默认输出HEAD指向commit的内容.
>**git show**
- `shortlog`：这个命令用来输出汇总信息，以作者进行分类。
>**git shortlog**
- `--author`：加--author用来过滤commit,限定输出给定的用户
>**git log --author="Michael Yang"**
- ^origing：查看本地commit，但没有push到远程库上的记录
>**git log branch_name ^origin/branch_name**
>or
>**git status; git cherry -v**
- `--name-only, --name-status:` 显示修改文件列表
>**git log -2 --name-only**
>**git log -2 --name-status**
- 如何使git log只显示修改的文件，不显示commit id和commit message?
>**git log --name-only --format=''**
> git fetch 过后显示diff且只显示文件名
>**git log --name-only --format='' master..origin/master**
- git log  搜索删除的行提交记录
>**git log -S "abcdef" filename**

[git log 详解 原文链接](https://blog.csdn.net/jjlovefj/article/details/86476925)

# blame
- 先查看某行代码的修改记录
>**git blame file_name**
- 然后用show查看具体修改信息
>**git show commitID**


# reflog
- `-n`：指定reflog输出数量，直接在relog命令之后加`-n`参数即可，n表示要输出的数量
>**git reflog -2**
- `--date==iso`：显示时间
>**git reflog -2 --date=iso**

[git reflog 原文链接](https://www.itranslater.com/qa/details/2119006622956651520)

# branch
- `branch`：显示当前本地的分支信息，同时会标注当前所在的分支，源信息保存。
>**git branch**
- `checkout`：切换branch
>**git checkout patch/ss-1.1.1.0**
- 本地新建分支并push到remote
>**git checkout -b patch/ss-1.1.1.1**
>**git push origin patch/ss-1.1.1.1:patch/ss-1.1.1.1**
- 删除branch
>**git branch -D patch/ss-1.1.1.1**
>**git push origin --delete patch/ss-1.1.1.1**

[git branch原文链接](http://oldjiang.tech/architure/git.html#git-branch)

# patch
```bash
git clone git://github.com/ariejan/imdb.git
cd imdb/
git checkout -b fix_empty_poster
vi README.md
git commit -m "first commit"
vi README.md
git commit -m "second commit"
git format-patch master --stdout >fix_empty_poster.patch
git checkout master
git apply --stat fix_empty_poster.patch 
git apply --check fix_empty_poster.patch 
git am --signoff < fix_empty_poster.patch
git log -3
```
[git format-patch原文链接](https://www.devroom.io/2009/10/26/how-to-create-and-apply-a-patch-with-git/)

# cherry-pick
- 从别的branch把commit拿到当前branch
```bash
#单独合并一个提交
git cherry-pick commitHash
#同上，不同点：保留原提交者信息。
git cherry-pick -x commitHash
#Git从1.7.2版本开始支持批量cherry-pick，就是一次可以cherry-pick一个区间的commit。
#start-commitHash到end-commitHash之间(左开右闭，不包含start-commitHash)的提交cherry-pick到当前分支；
git cherry-pick start-commitHash..end-commitHash
#有"^"标志的表示把start-commitHash到end-commitHash之间(闭区间，包含start-commitHash)的提交cherry-pick到当前分支。
git cherry-pick start-commitHash^..end-commitHash
```
# config
- git 为不同的项目设置不同的用户名和邮箱
- 找到项目所在目录下的 .git/文件夹，进入.git/文件夹，然后执行如下命令分别设置用户名和邮箱：
- 配置git diff 显示tab为4个空格
```bash
git config user.name "abc"
git config user.email "abc@example.com"
git config --global core.pager 'less -x1,5'
```
- 然后执行命令查看config文件：cat config
- warning: in the working copy of ‘XXX.py’, LF will be replaced by CRLF the next time Git touches it
```bash
git config --global core.autocrlf false
```
# rebase
- 从主分支rebase过来
```bash
git checkout patch/sss
git rebase master
```

# 组合命令
- 查找某个文件在哪个branch上新加了关键字
```bash
git branch -r | xargs -i git blame {} filename | grep keyword
```

# Windows下git bash
- git config
```bash
git config --list --show-origin //可以查看配置文件存放路径，依次是--system,--global,--local, local的优先级最高，会覆盖global和system的同名配置，其次是global，会覆盖system的同名配置
git config --list --system
git config --list --global
git config --list --local
```

