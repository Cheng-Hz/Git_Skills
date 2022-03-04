# Git_Skills

From 廖雪峰 https://www.liaoxuefeng.com/wiki/896043488029600/900003767775424

## Basic

`git clone git@`

从已有的repo  clone

`git branch -m master main`

`git push -u origin main`

`git checkout -b dev`

相当于
```
$ git branch dev
$ git checkout dev
Switched to branch 'dev'
```

`git branch//查看分支`

`git merge dev//合并分支`

`git branch -d dev//删除dev`

创建并切换到新的dev分支，可以使用：

`$ git switch -c dev`

直接切换到已有的master分支，可以使用：

`$ git switch master`

使用新的`git switch`命令，比`git checkout`要更容易理解

### 小结

查看分支：`git branch`

创建分支：`git branch <name>`

切换分支：`git checkout <name>`或者git switch `<name>`

创建+切换分支：`git checkout -b <name>`或者`git switch -c <name>`

合并某分支到当前分支：`git merge <name>`

删除分支：`git branch -d <name>`

## Conflict

`git log --graph --pretty=oneline --abbrev-commit`

## --no-ff

`git merge --no-ff -m "merge with no-ff" dev`

合并分支时，加上`--no-ff`参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而`fast forward`合并就看不出来曾经做过合并。

## Stash for Bug

修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；

当手头工作没有完成时，先把工作现场`git stash`一下，然后去修复bug，修复后，再`git stash pop`，回到工作现场；

在master分支上修复的bug，想要合并到当前dev分支，可以用`git cherry-pick <commit>`命令，把bug提交的修改“复制”到当前分支，避免重复劳动。

## -D

如果要丢弃一个没有被合并过的分支，可以通过`git branch -D <name>`强行删除

## TEAMWORK
因此，多人协作的工作模式通常是这样：

首先，可以试图用`git push origin <branch-name>`推送自己的修改；

如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；

如果合并有冲突，则解决冲突，并在本地提交；

没有冲突或者解决掉冲突后，再用`git push origin <branch-name>`推送就能成功！

如果`git pull`提示`no tracking information`，则说明本地分支和远程分支的链接关系没有创建，用命令`git branch --set-upstream-to <branch-name> origin/<branch-name>`。

这就是多人协作的工作模式，一旦熟悉了，就非常简单。

小结
查看远程库信息，使用`git remote -v`；

本地新建的分支如果不推送到远程，对其他人就是不可见的；

从本地推送分支，使用`git push origin branch-name`，如果推送失败，先用`git pull`抓取远程的新提交；

在本地创建和远程分支对应的分支，使用`git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致；

建立本地分支和远程分支的关联，使用`git branch --set-upstream branch-name origin/branch-name`；

从远程抓取分支，使用`git pull`，如果有冲突，要先处理冲突。

### Rebase

## tag

`git tag v1.0`

`git push origin <tagname>`


## Q&A

*error: src refspec master does not match any*

*error: failed to push some refs to*

TEST Main

TEST

文件存在冲突，必须手动解决冲突后再提交。`git status`也可以告诉我们冲突的文件

