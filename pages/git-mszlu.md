- 全局配置
  
  ```shell
  git config --global user.name "usename"
  git config --global user.email "email"
  ```
# 创建远程仓库

在GitHub或着gitee创建远程仓库
# 创建本地仓库

```Shell
mkdir 仓库名称 #创建仓库
cd 仓库名称 # 进入仓库
git init # git 初始化
touch README.md # 新建README.md文件
git add README.md # 将README.md添加到暂存区
git commit -m "first commit" # 提交到本地仓库
git remote add origin 远程仓库地址 # 关联远程仓库，取别名为origin
git push -u origin "master" # 提交到origin仓库的master分支，-u为初始化远程仓库的意思，该远程仓库未初始化且第一次提交可以添加
```


`git init`:当前目录变成Git可以管理的仓库

`git add`：把文件添加到本地仓库的暂存区

`git commit`：把文件提交到本地仓库，注意必须加 -m 后面跟着本次提交的内容说明

`git remote`：将本地仓库和远程仓库链接起来 origin是远程仓库的名称，git的默认，可以理解为给远程仓库起了个别名

`git push`:将本地仓库的内容变更 提交到远程仓库 origin就代表远程仓库，master代表分支，第一次提交需要加上`-u`参数，git会将本地仓库的master分支和远程仓库的master分支做一个关联

`git status`：查看状态
# 工作区与暂存区

先来理解一下Git工作区、暂存区和版本股的概念
- 工作区：就是你在电脑里能看到的目录
- 暂存区：英文叫stage或index。一般存放在.git目录下的index文件(.git/index)中，所以我们把暂存区有时也叫做索引(index)。
- 版本库：工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本哭。
# 版本回退

`git log`：查看历史记录

`git reset`：git reset命令用于回退版本，可以指定退回某一次提交的版本

reset有三个参数：

1. `--mixed`
默认，可以不用带该参数，用于重置暂存区的文件与上一次的提交（commit）保持一致，工作区文件内容保持不表。

2. `--soft`
参数用于回退到某个版本，暂存区不会重置，工作区也不会改，版本回退（git log版本截止到回退的版本）

3. `--hard`
参数撤销工作区中所有未提交的修改内容，将暂存区与工作区都回到上一次版本，并删除之前的所有信息提交
示例：

```Shell
git reset --hard origin/master #将本地的状态回退到和远程的一样
```


`注意：`谨慎使用-hard参数，他会删除回退点之前的所有信息，一定要在使用--hard之前，先把本地的代码提交到远程仓库