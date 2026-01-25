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

## 具体的相关重要指令

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



