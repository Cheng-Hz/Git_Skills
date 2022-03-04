# Git_Skills

## 廖雪峰 https://www.liaoxuefeng.com/wiki/896043488029600/900003767775424

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
## Q&A

*error: src refspec master does not match any*

*error: failed to push some refs to*

TEST Main

TEST

文件存在冲突，必须手动解决冲突后再提交。`git status`也可以告诉我们冲突的文件