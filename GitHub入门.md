# GitHub  

## 一、准备工作
（1）在 https://github.com 网站上注册一个账号并设置用户名、密码，新建一个repository

（2）在网站 http://msysgit.github.io/ 上下载git，并安装

## 二、设置SSH
### 1、首先在本地创建ssh key，使用下面的命令：
`$ ssh-keygen -t rsa -C "your_email@youremail.com"`  
后面的参数`your_email@youremail.com`改为你在github网站上注册的邮箱，之后要求确认路径和输入密码（密码就是网站上自己设置的密码），之后一路默认。成功之后可以在`C://Users/.ssh`下找到`id_rsa.pub`文件，打开全部复制。

回到github网页版，点击头像 `--> Settings --> SSH和GPG keys --> New SSH key`，粘贴上之前复制的密钥内容。如下图：


为了验证是够成功，在git bash下输入下面的命令：

`$ ssh -T git@github.com ` 
第一次会提示是够`continue`，输入“yes”，接着会看到“`You've successfully authenticated, but GitHub does not provide shell access`”，表示连接成功。

### 2、设置username和email，github每次commit都会记录他们。使用下面的命令：

```
$ git config --global user.name "your name"  
$ git config --global user.email "your_email@youremail.com"  
```
`yourname`是网页上的用户名，`your_email@youremail.com`是用户注册的邮箱。

## 三、上传本地文件到远程仓库
这里只讲述最简单的上传，所以采用了一种比较固定的模式，其他再多些的用法可自行搜索，只是成功上传了的一个流程（弄了好久，终于成功了..^_^..），说明：下面的内容几乎来自http://blog.csdn.net/sinat_33366020/article/details/73732769，非常感谢作者！！

### 1、先进入项目文件夹
比如我想把python下面的test文件夹及test文件夹下的文件上传，则进入python文件夹内（如上传python下面的文件及文件夹，则需要进入python的上一级目录），使用cd命令。

### 2、通过git init把当前目录变成git可以管理的仓库
使用如下命令：

`git init`  
可以使用`ls -a`查看当前文件夹下是否包括一个`.git`的文件夹，若包含，则成功。
### 3、把文件添加到本地版本库
使用命令`git add`添加文件；添加到暂存区里面去，如果add后面加入的是“.”，则意味着需要添加当前文件夹下的所有文件，若只想添加`/python/test/note.txt`这个文件，则只需要将"."改成当前路径（/test/note.txt）即可，命令如下：

`git add .`  
### 4、用命令`git commit`把文件提交到仓库
如下命令：

`git commit -m 'note'`  
引号里面的是提交的说明，如果忘记带参数-m，则会自动打开vim编辑器。
### 5、关联到远程仓库
使用下面的命令：

`git remote add origin 你的远程库地址`  
如：

`git remote add origin https://github.com/nnaa/helloworld.git ` 
`nnaa`是你的用户名，`helloworld`是新建的仓库名称。
如果发现上面步骤写错了，则使用下面的命令：

`git remote rm origin   //删除origin`  
`git remote add origin https://github.com/nana/demo.git   //重新添加origin`  
### 6、远程库与本地同步合并
（如果远程库不为空必须做这一步，否则后面的提交会失败）

`git pull --rebase origin master`  
### 7、将最新的修改推送到远程仓库
使用下面的命令：
`git push -u origin master`  
其中，`origin`是远程仓库名字; `master`是远程仓库所属分支

注意: 我们第一次push的时候,加上`-u`参数,Git就会把本地的master分支和远程的master分支进行关联起来,我们以后的push操作就不再需要加上`-u`参数了

如果出现类似下面内容：


```
Username for 'https://github.com': shiren1118  
Password for 'https://shiren1118@github.com':  
To https://github.com/shiren1118/iOS_code_agile.git  
 ![rejected]        master -> master(non-fast-forward)  
error: failed to push some refs to'https://github.com/shiren1118/iOS_code_agile.git'  
hint: Updates were rejected because the tip of yourcurrent branch is behind  
hint: its remote counterpart. Merge the remote changes(e.g. 'git pull')  
hint: before pushing again.  
hint: See the 'Note about fast-forwards' in 'git push--help' for details.
```  
则输入命令下列命令即可：


`git push -u origin master -f`     
## 四、拷贝其他git文件
如果从在git服务器所在主机上的其他账户获取git服务器上面文件，则直接用gitclone + git仓库的路径，即：

`git clone /nnaa/sample.git`（将仓库地址复制）  