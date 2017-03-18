1、每个机器都必须自报家门：你的名字和Email地址
	$ git config --global user.name "Your Name"
	$ git config --global user.email "email@example.com"

2、创建仓库
	$ mkdir learngit   建立仓库文件夹
	$ cd learngit      打开文件夹(同时也是打开这样打开其他盘 cd D:)
	$ pwd              用户显示当前目录
	$ git init         把这个目录变成Git可以管理的仓库
	先touch readme.txt
	在$ git add readme.txt   告诉Git，把文件添加到仓库
	$ git commit       告诉Git，把文件提交到仓库

	$ git status   	    让我们时刻掌握仓库当前的状态，查看哪些只是修改过但还没有提交

	$ git diff+文件     看看具体修改了什么内容
















