# git
### 1. git reflog
>记录在这个git仓库里面的每一次操作，基本的形式就是:提交的索引号，相对于HEAD指针的位置，操作的命令以及commit时候的信息
### 2. git checkout -- 撤销工作目录中的修改。前提是这个文件还没有被添加到暂存区。如果被添加到暂存区，则可以先使用git reset HEAD命令
		将暂存区的文件，撤销到工作区，然后再使用这个命令撤销修改
>注意：git checkout . 是将工作目录所有文件的修改，都进行撤销。git checkout [filename] 是将制定的filename文件进行撤销修改
### 3. git rm [filename] -- 从git仓库中删除指定名字的文件。
>这个命令会将工作目录中的文件删除，有的时候会提示使用-f选项，强制的删除制定的文件
### 4. git remote add -- 使本地的仓库和远程仓库进行关联。
>关联的基本格式就是：git remote add [选项] name url。其中：name这个选项要和远程仓库分支的名称相同（不然就是添加远程仓库）。通过url将本地的分支和远程仓库的分支建立起关联之后，当我们通过git push origin 远程仓库分支的名称。才能够将我们的代码push到远程分支上，用我们自己随意取的是不能push上去的。
### 5. git clone url -- 从远程仓库copy一份到本地仓库
### 6. git push name branchname -- >将本地的修改push到远程仓库里面去，name指的是远程仓库的名称，默认是origin。branchname指的是远程仓库中的分支的名称，默认值master(这两个名称在我们创建好远程仓库的时候自动的设置好了，我们clone本地的时候，也会有一个master分支，同时和远程的master分支做关联)
### 7. git branch [branch-name] -- 这条命令主要是用于创建分支的
>分两种情况使用，如果没有指定分支的名称，那么，则是查看本地有多少分支以及当前处于哪个分支上。如果指定了分支的名称，则是创建一个新的本地分支
### 8. git checkout <branch-name> 
>这个命令主要是用于切换到指定的分支的。这个命令的后面如果跟着的是文件的名称，则是用于撤销修改的。
### 9. git checkout -b [branch-name]
>这个命令主要是用于创建并切换分支的，这个命令其实是git branch [branch-name]和git checkout [branch-name]的综合使用
### 10. git branch -- 用于查看当前的分支，并同时列出所有的分支
>指定参数-a可以查看远程的分支的信息
### 11. git merge --no-ff [branch-name] -- 合并指定分支到当前的分支
>如果你只有一个commit，可以使用 git cherry-pick [分支名，或者commitID]
### 12. git branch -d <branch-name>:删除本地的分支
>注意，如果你正在删除的分支还没有被其它分支合并过，那么我们可以运行git branch -D <branch-name>来强制的删除分支
### 13. git push origin :[远程分支的名称]：这个命令主要是用于删除远程分支
>注意，远程分支的名称之前有一个空格和冒号。
### 14. git push origin [本地分支的名称]:[远程分支的名称]：将本地仓库推送到远程仓库上去
##git的一些高级用法
### 1. git [命令的名称] --help
>这个命令主要是用于获取一条命令的具体的用法
### 2. git blame [文件的名称]
>查看指定文件的每一行的最后一次被更新的信息
### 3. git remote add [仓库的名称] [仓库的地址]
>这条命令主要是用于添加一个远程仓库，添加好之后，我们就可以使用git fetch [仓库的名称]来追踪远程仓库了
### 4. git remote show：列出所有的远程仓库的名称
### 5. git remote rename [旧仓库的名称] [新仓库的名称]
>这条命令主要是给远程仓库更改名称
### 6. git remote remove [仓库名称]
>这条命令主要是用于删除远端的仓库。这个操作除了会删除与这个仓库所有的分支和配置信息
### 7. git remote show [仓库的名称]：这个命令主要是用于列出远程仓库
>如果没有指定远程仓库的名称，则会列出所有的远程仓库的名称，如果，指定了某一个远程仓库的名字，那么则会给出这个远程仓库的相关信息以及配置信息
### 8. git remote set-url [仓库名称] [新仓库地址]：这个命令主要是用于更新特定远程仓库下面的部分仓库地址
>其中的仓库地址可以是正则表达式
### 9. git remote set-url --delete [仓库名称] [仓库地址]--(8和9暂时不理解)
### 10. git branch [branchname] [commitID]：基于当前分支的某次ID来创建一个新的分支
>这个命令所创建的分支的工作区和指定的commitID时候的工作区的状态是一样的
### 11. git branch (-m | -M) [旧分支的名称] [新分支的名称]
>这个命令主要用于修改分支的名称。如果你所修改的分支指定的名称已经存在的话，-m是不会修改分支的名称的，同时会给出提示。-M则会强制的覆盖已经有的分支