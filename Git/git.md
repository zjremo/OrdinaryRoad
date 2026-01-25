# Git

这是有关git的常用指令和学习内容记录

## Github仓库创建关联

### 方法一: GitHub上创建仓库然后克隆到本地直接关联

```bash
git clone https://github.com/zjremo/arch-linux.git
```

克隆到本地后其实就已经关联到了GitHub上的远程仓库

### 方法二: 本地先初始化本地仓库，然后关联远程仓库

```bash
# 假设我们的仓库目录是test/
cd test
# 初始化git本地仓库
git init
# 添加README.md或者全部东西
git add README.md
# 或者
git add .
# 第一次本地提交
git commit -m "first commit"
# 变更master分支为main分支
git branch -M main
# 关联远程仓库
git remote add origin https://github.com/zjremo/test.git
# 推送到远程仓库，-u表示默认记忆推送到后面写的分支(比如此时就是main)
git push -u origin main
```

## 具体的相关重要知识

### 信息初始化

当安装完`Git`应该做的第一件事就是设置你的用户名称与邮件地址。这样做很重要，因为每一个`Git`的提交都会使用这些信息，并且它会写入到你的每一次提交中，不可更改：

```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

使用`--global`选项之后，命令只需要运行一次即可。后面Git提交都会选择这些信息。

```bash
# 查看所有设置的配置
git config --list
http.proxy=http://127.0.0.1:15732
https.proxy=http://127.0.0.1:15732
user.email=3106316195@qq.com
user.name=zjremo

git config user.name
zjremo
```

### 记录每次更新到仓库

#### 文件状态
![file_lifestyle](./img/file_lifestyle.png)
每一个文件都不外乎这两种状态：已跟踪或未跟踪。已跟踪的文件是指那些被纳入了版本控制的文件，在上一次快照中有它们的记录，在工作一段时间后，它们的状态可能处于未修改，已修改或已放入暂存区。工作目录中除已跟踪文件以外的所有其它文件都属于未跟踪文件，它们既不存在于上次快照的记录
中，也没有放入暂存区。初次克隆某个仓库的时候，工作目录中的所有文件都属于已跟踪文件，并处于未修改状
态。编辑过某些文件之后，由于自上次提交后你对它们做了修改，Git 将它们标记为已修改文件。我们逐步将这些修
改过的文件放入暂存区，然后提交所有暂存了的修改，如此反复。

#### 检查当前文件状态

`git status`命令输出十分详细，但其用于比较繁琐，其实可以使用`git status -s`来简化，从而获取更为紧凑的格式输出。

```bash
$ git status -s
M README
MM Rakefile
A lib/git.rb
M lib/simplegit.rb
?? LICENSE.txt
```
其中上面的符号为含义:
```text
1. ??: 目前文件添加之后没有跟踪；
2. _M: 文件被修改但是没有放入暂存区；
3. M_: 文件被修改了并放入暂存区；
4. A: 新添加到暂存区中的文件前面有A标记.
```


## 重要的版本管理指令

| Command   | function    |
|--------------- | --------------- |
| git add file   | add untracked file or unstaged changes   |
| git add .   | add all untracked files and unstaged changes |
| git rm file   | delete file   |
| git rm --cached file   | 不再track这个file，同时工作区不删除这个file   |
| git reset file   | Unstage one file   |
| git branch    | List branches   |
| git branch -d branch_name   |  删除某个分支  |
| git branch -D branch_name   |  强制删除某个分支  |
