---
title: git常用命令
date: 2020-06-19 11:50:10
categories: git常用命令
tags:
copyright: false
---
### 已经删除的分支，但是通过git branch -a/r依然存在的解决方案 ###
    通过这个命令查看
        git remote show origin
    通过这个清除
        git remote prune origin
### git使用 ###
    1. 添加指定文件到暂存区
        git add [file1] [file2] ...
    2. 添加指定目录到暂存区，包括子目录
        git add [dir]
    3. 添加当前目录的所有文件到暂存区
        git add .
    4. 添加每个变化前，都会要求确认 对于同一个文件的多处变化，可以实现分次提交
        git add -p
    5. 删除工作区文件，并将这次删除放入暂存区
        git rm [file1] [file2] ...
    6. 停止追踪指定文件，但该文件会保留在工作区
        git rm --cached [file]
    7. 改名文件，并且将这个改名放入暂存区
        git mv [file-original] [file-renamed]
### 代码提交 ###
    1. 提交暂存区到仓库
        git commit -m [message]
    2. 提交暂存区的指定文件到仓库区
        git commit  [file1] [file2] ... -m [message]
    3. 提交工作区自上次commit之后的变化，直接到仓库区
        git commit -a
    4. 提交时显示所有diff信息
        git commit -v
    5. 使用一次新的commit，替代上一次提交，如果代码没有任何新变化，则用来改写上一次commit的提交信息
        git commit --amend -m [message]
    6. 重做上一次commit，并包括指定文件的新变化
        git commit --amend [file1] [file2] ...
### 分支 ###
    1. 列出所有本地分支
        git branch
    2. 列出所有远程分支
        git branch -r
    3. 列出所有本地分支和远程分支
        git branch -a
    4. 新建一个分支
        git branch [branch]
    5. 新建一个分支，并切换到该分支
        git checkout -b [branch]
    6. 新建一个分支，指向指定commit
        git branch [branch] [commit]
    7. 新建一个分支，与指定的远程分支建立追踪关系
        git branch --track [branch] [remote-branch]
    8. 切换到指定分支，并更新工作区
        git checkout [branch]
    9. 切换到上一分支
        git checkout -
    10. 建立追踪关系，在现有分支与指定的远程分支之间
        git branch --set-upstream [branch] [remote-branch]
    11. 合并指定分支到当前分支
        git merge [branch]
    12. 选择一个commit，合并进当前分支
        git cherry-pick [commit]
    13. 删除分支
        git branch -d [branch]
    14. 删除远程分支
        git push origin --delete [branch]
        git branch -dr [remote/branch]
### 标签 ###
    1. 列出所有标签
        git tag
    2. 新建一个tag在当前commit
        git tag [tag]
    3. 新建一个tag在指定commit
        git tag [tag] [commit]
    4. 删除本地tag
        git tag -d [tag]
    5. 删除远程tag
        git push origin :refs/tags/[tagName]
    6. 查看tag信息
        git show [tag]
    7. 提交指定tag
        git push [remote] [tag]
    8. 提交所有tag
        git push [remote] --tags
    9. 新建一个分支，指向某个tag
        git checkout -b [branch] [tag]
### 查看信息 ###
    1. 显示有变更的文件
        git status
    2. 显示当前分支的版本历史
        git log
    3. 显示commit历史，已经每次commit发生变更的文件
        git log --stat
    4. 搜索提交历史，更具关键词
        git log -S [keyword]
    5. 显示某个commit之后的所有变动，每个commit占据一行
        git log [tag] HEAD --pretty=format:%s
    6. 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
        git log [tag] HEAD --grep feature
    7. 显示某个文件的版本历史，包括文件改名
        git log --follow [file]
        git whatchanged [file]
    8. 显示指定文件相关的每一页diff
        git log -p [file]
    9. 显示过去5次提交
        git log -5 --pretty --oneline
    10. 显示所有提交过的用户，按提交次数排序
        git shortlog -sn
    11. 显示指定文件是什么人在什么时间修改过
        git blame [file]
    12. 显示暂存区和工作区的代码差异
        git diff
    13. 显示暂存区和上一个commit的差异
        git diff --cached [file]
    14. 显示工作区与当前分支最新commit之间的差异
        git diff HEAD
    15. 显示两次提交之间的差异
        git diff [first-branch]...[second-branch]
    16. 显示今天你写了多少行代码
        git diff --shortstat "@{0 day ago}"
    17. 显示某次提交的元数据和内容变化
        git show [commit]
    18. 显示某次提交发生变化的文件
        git show --name-only [commit]
    19. 显示某次提交时，某个文件的内容
        git show [commit]:[filename]
    20. 显示当前分支的最近几次提交
        git reflog
    21. 从本地master拉取代码更新当前分支：branch 一般为master
        git rebase [branch]
    
