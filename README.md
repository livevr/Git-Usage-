###Git工具

####mac平台
推荐命令行+sourcetree，sourcetree为图形界面工具。
####Windows平台
推荐GitBash+TortoiseGit，GitBash中可以使用命令行，TortoiseGit为图形界面工具。

####Git 相关概念
远端remote：git服务器端，代码在github上存放的位置，remote默认命名为origin。

本地local：用户的本地端。

分支branch：一个代码仓库可以有多个分支，每个分支可以完成各自的任务，便于多人协作。

fork：在远端自己的名下生成一个代码的拷贝。

克隆clone：从远端代码仓库克隆代码到本地。

拉pull：从远端拉代码到本地。

推push：从本地推代码到远端。

提交commit：__将修改提交到本地__

取fetch：将远端代码取到本地的FETCH_HEAD分支中（这是临时分支，可以基于这个分支创建新的分支）。

合并申请pull request：请求合并代码，从a仓库的branch1分支发送给b仓库的branch2分支，a仓库是从b仓库fork的。需要在github网站上操作。

合并merge：在自己的仓库修改了本地a文件，提交到本地，拉取远端的a文件，修改会自动合并。

冲突conflict：合并时发现远端的文件也已经被修改，而且与本地的修改冲突时就会产生冲突，需要用户手动解决冲突。

子模块submodule: 可以把其他代码库作为自己代码库的子模块。

####Git常用命令
克隆代码仓库:git clone https://github.com/livevr/Git-Usage-

查看远端代码库地址：git remote -v

添加一个远端代码库的地址：git remote add name address

拉指定分支：git pull [repo_name [branch_name] ]

获取远端分支（不合并）：git fetch repo_name [branch_name]

更新子模块：git submodule update --init

提交代码：git commit -a -m 'comment'其中-a表示全部提交

推代码到远端: git push repo_name [branch_name]，注意我们要求只推到自己的远端。

分支切换：git checkout branch_name

####使用步骤

1. fork主仓库代码
2. 从自己的代码库clone代码到本地，如git clone https://github.com/super626/Git-Usage-
3. 本地代码修改并提交到本地git commit -a -m '本次修改内容'
4. 本地代码推送到远端git push origin [bran_name]
5. 登录到https://github.com/super626/Git-Usage-，点击New pull request发送PR到主仓库，写清楚修改内容。
6. 有合并权限的人在https://github.com/livevr/Git-Usage-审核该PR并合并confirm merge。

####多任务协作开发git使用
git远端可以多个分支同时开发
1. 获取远端branch1分支 git fetch reopname branch1
2. 基于branch1分支建立自己的分支 git checkout -b localbranchname FETCH_HEAD
3. 也可以把刚创建的localbranch合并到已有的分支中，sourcetree有界面操作，merge后看是否有冲突，有则需要解决，冲突的部分会标记出来，源码看是包含>>>>>>>>>>>>和<<<<<<<<<<<<<<<<<<<的部分
3. 在自己的本地分支上修改，提交本地修改git commit -a -m 'comment'
4. 之后与上一节的使用相同

####issue相关
缺陷管理github有自己的issue系统。我们先沿用它。

1. 创建issue，例如对于我们当前的代码库，https://github.com/livevr/Git-Usage-/issues，New Issue写清楚标题和内容，如果是bug描述清楚bug的重现方式。
2. Issue也可以指派给指定的人。
3. 解决每个issue的问题时都创建自己新的本地分支。
4. PR与issue的关联，我们发送的PR可以与指定的issue关联或者关闭掉指定的issue。在发送PR的页面的comment内容里边用#issue no.关联相应的issue，fix #issue no.关闭相应的issue。也可以手动关闭issue。
5. issue的好处是把bug或者任务跟我们的PR自动关联，很方便查询到那部分修改修复了这个bug。
