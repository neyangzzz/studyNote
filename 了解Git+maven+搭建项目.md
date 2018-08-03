# 入职第二天笔记
## 使用idea新建一个项目，并提交到GitHub

首先建立本地库import into version control—>create git repository
add—>commit—>push

## 了解Git使用规范
git基本命令
新建
1，在当前目录新建一个Git代码库
$ git init

2，新建一个目录，将其初始化为Git代码库
$ git init [project-name]

3，下载一个项目和它的整个代码历史
$ git clone [url]

### 配置
4，显示当前的Git配置
$ git config --list

5，编辑Git配置文件
$ git config -e [--global]

6，设置提交代码时的用户信息
$ git config [--global] user.name "[name]"
$ git config [--global] user.email "[email address]"

### 增加删除
1，添加指定文件到暂存区
$ git add [file1] [file2] ...

2，添加指定目录到暂存区，包括子目录
$ git add [dir]

3，添加当前目录的所有文件到暂存区
$ git add .

4，添加每个变化前，都会要求确认，对于同一个文件的多处变化，可以实现分次提交
$ git add -p

5，删除工作区文件，并且将这次删除放入暂存区
$ git rm [file1] [file2] ...

6，停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached [file]

7，改名文件，并且将这个改名放入暂存区
$ git mv [file-original] [file-renamed]


### 代码提交
1，，提交暂存区到仓库区
$ git commit -m [message]


2，，提交时显示所有diff信息
$ git commit -v


### 分支
1，列出所有本地分支
$ git branch

2，列出所有远程分支
$ git branch -r

3，列出所有本地分支和远程分支
$ git branch -a

4，新建一个分支，但依然停留在当前分支
$ git branch [branch-name]

5，新建一个分支，并切换到该分支
$ git checkout -b [branch]

6，切换到指定分支，并更新工作区
$ git checkout [branch-name]

7，切换到上一个分支
$ git checkout -

8，合并指定分支到当前分支
$ git merge [branch]

9， 删除分支
$ git branch -d [branch-name]

10， 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]

远程同步

1，显示所有远程仓库
$ git remote -v

2，显示某个远程仓库的信息
$ git remote show [remote]

3，增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]

4，取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]

5，上传本地指定分支到远程仓库
$ git push [remote] [branch]

6，推送所有分支到远程仓库
$ git push [remote] --all

### 撤销
1，恢复暂存区的指定文件到工作区
$ git checkout [file]

2，恢复某个commit的指定文件到暂存区和工作区
$ git checkout [commit] [file]

3，恢复暂存区的所有文件到工作区
$ git checkout .

4，重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
$ git reset [file]




## 安装maven
用brew

 
1，编译源代码： mvn compile 

2，编译测试代码：mvn test-compile    

3，运行测试：mvn test   

4，产生site：mvn site   

5，打包：mvn package   

6，在本地Repository中安装jar：mvn install 

7，清除产生的项目：mvn clean   

8，生成idea项目：mvn idea:idea   

9，只打jar包: mvn jar:jar   








