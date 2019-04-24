# Github分支

## 分支
创建一个叫做“feature_x”的分支，并切换过去：
`git checkout -b feature_x`  
切换回主分支：
`git checkout master`  
再把新建的分支删掉：
`git branch -d feature_x`  
除非你将分支推送到远端仓库，不然该分支就是 不为他人所见的：  
`git push origin <branch>`  

## 更新与合并
要更新你的本地仓库至最新改动，执行：  
`git pull`  
以在你的工作目录中 获取（fetch） 并 合并（merge） 远端的改动。  
要合并其他分支到你的当前分支（例如 master），执行：  
`git merge <branch>`  
在这两种情况下，git 都会尝试去自动合并改动。遗憾的是，这可能并非每次都成功，并可能出现冲突（conflicts）。 这时候就需要你修改这些文件来手动合并这些冲突（conflicts）。改完之后，你需要执行如下命令以将它们标记为合并成功：  
`git add <filename>`  
在合并改动之前，你可以使用如下命令预览差异：  
`git diff <source_branch> <target_branch>`  

## log
如果你想了解本地仓库的历史记录，最简单的命令就是使用:   
`git log`  
你可以添加一些参数来修改他的输出，从而得到自己想要的结果。 只看某一个人的提交记录:  
`git log --author=bob`  
一个压缩后的每一条提交记录只占一行的输出:  
`git log --pretty=oneline`  
或者你想通过 ASCII 艺术的树形结构来展示所有的分支, 每个分支都标示了他的名字和标签:   
`git log --graph --oneline --decorate --all`  
看看哪些文件改变了:   
`git log --name-status`  
这些只是你可以使用的参数中很小的一部分。更多的信息，参考：  
`git log --help` 
 
## 替换本地改动  
假如你操作失误（当然，这最好永远不要发生），你可以使用如下命令替换掉本地改动：  
`git checkout -- <filename>`  
此命令会使用 HEAD 中的最新内容替换掉你的工作目录中的文件。已添加到暂存区的改动以及新文件都不会受到影响。  

假如你想丢弃你在本地的所有改动与提交，可以到服务器上获取最新的版本历史，并将你本地主分支指向它：  
`git fetch origin`  
`git reset --hard origin/master`  

## 实用小贴士
内建的图形化 git：
`gitk`  
彩色的 git 输出：
`git config color.ui true`  
显示历史记录时，每个提交的信息只显示一行：
`git config format.pretty oneline`  
交互式添加文件到暂存区：
`git add -i`  
