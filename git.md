# Git快速上手
## Git是什么
* git是一个**分布式**的**版本控制**软件
* 版本控制是什么？
  * 快速回到指定版本
  * 记录修改历史，比如：某一行是谁修改的？某一次修改了哪些内容？
* 优点：
  * 高效管理代码版本
  * 远程同步
  * 强大的分支功能
  * 提高多人协作效率
* 分布式是什么意思？
  * 集中式：所有的版本都存在一台机器上（有一个中心节点）
  ![集中式](pic/集中式.png)
  * 分布式：每台使用版本控制的机器上都保存了所有版本（去中心化）
  ![分布式](pic/分布式.png)
  * 优点：可用性好
    * 一台机器上的版本丢失可以从其他机器恢复
    * 不依赖于特定机器

## Git中的基本概念
* 提交(commit)：代码仓库中的一个版本
* 仓库：保存所有版本的地方
* 暂存区：暂时存放要保存到仓库里的内容
* 工作区：写代码的地方
* 在仓库里新增一个提交的过程：
  1. 在工作区修改（添加/删除）
  2. 以文件为单位，将修改的文件提交到暂存区
  3. 将暂存区中的文件打包，提交到仓库中
* ![提交过程](./pic/提交过程.png)

## Git基本使用
* 新建仓库：`git init`
* 查看工作区状态：`git status`
* 将修改提交到暂存区：`git add`
* 将暂存区的修改打包，形成仓库中的一条新提交：`git commit`
* 查看修改历史：`git log`
* 切换到历史版本：`git checkout`
* stash区：`git stash`

## 远程仓的使用
* github和gitee是什么？
  * github和gitee是开源社区，可以认为是远程代码仓库，但功能远超远程仓库
  * 开源社区还可以向开发者提交bug反馈，提新的需求，在该项目下讨论交流，向该项目提交合并请求
* 新建远程仓
* 向远程仓推送代码：`git push <server-name> <branch-name>`
* 从远程仓拉取代码：`git pull [<server-name> <branch-name>]`
* 总结
  ![总结](pic/总结.png)

## 分支的基本思想
* 分支是什么？
  * 像树枝分叉一样，树枝长到某个节点后会分出树杈，分叉后两个树枝都在各自向前生长
  * ![分支](pic/分支.png)
* 分支的应用场景：
  1. 多人并行开发时，基于相同的版本，各自拉分支开发
  2. 开发新功能时，从稳定的分支上拉取出一个新的分支开发
* 优点：
  1. 多人同时开发独立功能，提高协作效率
  2. 能够帮助保证代码质量，方便CICD（持续集成、持续发布）进行版本管理

## Git分支操作
* 新建分支：`git branch <branch-name>`
* 查询已有分支：`git branch`
* 将其他分支的修改应用到当前分支：`git cherry-pick <commit-id-start>..<commit-id-end>`
* 切换分支：
  * `git checkout <branch-name>`
  * `git checkout -b <new-branch-name>`
* 合并分支：
  * `git merge <dst-branch-name>`
  * `git rebase <dst-branch-name>`
* 删除分支：`git branch -d <branch-name>`

## 冲突
* 产生原因：
  * 两次提交中对同一个文件的**同一行**进行了不同的修改
  * 在合并的时候git不知道应该选择(选择其一？还是保留两者？)
* 如何解决：
  1. 使用命令`git status`查看哪些文件产生了冲突
  2. 打开该文件搜索`<<<<<<<`找到冲突位置，git会使用特殊符号标识冲突部分
  3. 解决冲突
  4. 将冲突文件添加至暂存区
  5. 继续冲突前的步骤
* 如何避免产生冲突：
  * 如果两个人的提交经常产生冲突，说明二者的功能划分不够独立，考虑是不是设计问题

## 拓展资料
* [指令快速查询手册(图形版)](https://ndpsoftware.com/git-cheatsheet.html#loc=index;)
* [Learn Git Branching](https://learngitbranching.js.org/?locale=zh_CN)
* [指令快速查询手册(文字版)](https://training.github.com/downloads/zh_CN/github-git-cheat-sheet/)