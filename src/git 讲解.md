
### git 是什么
Git是目前世界上最先进的==分布式==版本控制系统。

svn 是 集中式版本控制系统。


常用命令
---
#### 添加查看
命令 | 说明 |
---|---|---
git config --list | 获取git 的配置项
git config 配置项名 | 获取具体的配置名
git config 配置项名 新名字 | 修改配置项
git init | 初始化本地版本库 
git status| 查看仓库状态
git add .  | 把工作区的所有修改提交到暂存区
git add 文件路径 | 把工作区指定文件提交到暂存区
git commit -m "描述" | 把暂存区的修改提交本地版本库（master分支）
git diff | 查看工作区具体修改
git diff --cached | 查看暂存区具体修改
git pull origin master | 远程代码拉取到本地工作区
git log | 查看历史记录 （在英文状态下Q退出当前状态）
git reflog | 可以查看所有分支的所有操作记录（包括已经被删除的 commit 记录和 reset 的操作）
git commit -am "描述" |  提交工作区自上次commit之后的变化，直接到仓库区（省略git add）
#### 撤销

```
第一种情况：撤销工作区的修改

# git checkout 文件路径
# git checkout . 所有文件

第二种情况：撤销暂存区的修改

# 1. git reset 文件路径 （把暂存区的修改撤回工作区）
# 2. git checkout 文件路径 

第三种情况：版本回退

# git reset --hard HEAD^  //回退到上个版本
# git reset --hard HEAD^^ //上上个版本
HEAD^^^~n //回退到n个版本上

回退到指定版本（回到现在过去）

git reset --hard commit_id(e66aa88...)


如何获取所有版本的commit_id呢？
针对这个需求，需要分两种情况：
*	第一，git bash窗口没有关闭，使用前面查过的commit_id
*	第二，git bash窗口关闭。比如，昨天做的操作，今天后悔了。 使用 git reflog

```


#### 远程仓库操作

命令 | 说明 |
---|---|---
git clone 仓库的地址 | 克隆一个版本库到新的目录 （git init 不要重复使用）
git remote add origin  仓库的地址 | 添加远程仓库地址（链接远程仓库）
git push origin master | 推送到远程服务器
git push -u origin master |如果当前分支与多个主机存在追踪关系，则可以使用-u选项指定一个默认主机，这样后面就可以不加任何参数使用git push。
git remote -v | 查看关联的远程服务器名称，在每一个后面有url
git pull origin master | 远程代码拉取到本地工作区
git pull --rebase origin master | 拉取远程的文件把本地的覆盖
git pull --allow-unrelated-histories | 拉取失败的时候（允许不相关的历史合并）
git remote set-url origin ssh/https地址 | ssh与https互换


#### git 分支管理

命令 | 说明 |
---|---
git branch 分支名 | 创建分支
git branch | 查看本地所有分支 
git branch -r | 查看远程所有分支
git branch -a | 查看本地和远程所有分支
git checkout 分支名 | 切换分支
git merge 分支名 | 合并分支
git checkout -b 分支名 | 创建并切换分支
git branch -d 分支名 | 删除本地分支
git push origin -d 分支名  |删除远程分支
git fetch origin 远程分支:本地分支 | 拉取远分支，并创建本地分支



#### git找回本地误删的文件
1. 首先，我们先用git status 看看工作区的变化


    $ git status


```
On branch master
...
        deleted:  Home/View/index.html
...
```
Home/View/index.html，记住这个。

    $ git reset HEAD Home/View/index.html 

    $ git checkout Home/View/index.html


#### git 中一些选项解释
```
-d  --delete：删除

-D  --delete --force的快捷键

-f  --force：强制

-m  --move：移动或重命名

-M  --move --force的快捷键

-r  --remote：远程

-a  --all：所有

```


#### gitHub 推荐使用 ssh
    公钥和秘钥：任意位置打开 git命令窗口，输入：ssh-keygen 
    一顿回车，之后会看到路径和图形代码，说明成功。
    

命令 | 说明
---|---
pwd | 查看工作目录
cd  [目录位置]  | 切换工作目录
ls [选项]...  [目录或文件名] | 显示某一个文件，或者某一个目录旗下子目录的属性。
du  [选项]...  [目录或文件名] | 统计目录及文件的空间占用情况


##### 命令窗口退出（英文状态下）


```
:wq 强制退出当前

q 退出git log 描述
```
