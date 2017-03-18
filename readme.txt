1、每个机器都必须自报家门：你的名字和Email地址
	$ git config --global user.name "Your Name"
	$ git config --global user.email "email@example.com"

2、创建仓库
	$ mkdir learngit        建立仓库文件夹
	$ cd learngit           打开文件夹(同时也是打开这样打开其他盘 cd D:)
	$ pwd                   用户显示当前目录
	$ git init              把这个目录变成Git可以管理的仓库
	先touch readme.txt
	在$ git add readme.txt          告诉Git，把文件添加到仓库
	$ git commit -m "这里是注释"    告诉Git，把文件提交到仓库

	$ git status   	        让我们时刻掌握仓库当前的状态，查看哪些只是修改过,但还没有提交

	$ git diff+文件         看看具体修改了什么内容

3、版本回退
	
	$ git log               显示从最近到最远的提交日志


	①、这个是回到以前版本

	$ git reset --hard HEAD^ 
	（^代表上一个版本 ^^上上版本 往上100个可以这样写HEAD~100）


	②、这个是指定回到未来的某个版本
	
	$ git reset --hard+commit id 
	（这个commit id可以用git log查看版本库的状态）

	$ git  reflog            显示你的每一次命令


4、工作区和暂存区

	1、第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区
	2、第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。



