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

	①、工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。
	②、Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。

	1、第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区
	2、第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。


	git diff HEAD -- 文件名   查看工作区和版本库里面最新版本的区别




5、撤销修改

	①、$ git checkout -- 文件名   文件在工作区的修改全部撤销，这里有两种情况
	     1、一种是文件自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态
	
	     2、一种是文件已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态

	总之，就是让这个文件回到最近一次git commit或git add时的状态


	②、git reset HEAD 文件         (HEAD表示最新版本)

		1、既可以回退版本，也可以把暂存区的修改回退到工作区



6、删除文件

		$ rm 文件名                     删除文件
		$ git rm 文件名			从版本库中删除该文件




7、远程仓库

				（远程仓库名）
		$ git remote add origin git@github.com:myLB/文件名.git

		$ git push -u origin master      把本地库的所有内容推送到远程库上

		$ git push origin master -f      强行让本地分支覆盖远程分支

		$ git pull origin master         抓取并合并远程仓库全部内容
       ($ git fetch origin <name> 这个更安全些,可以查看更新情况，然后再决定是否合并)
		
		$ git clone git@github.com:myLB/文件名.git

		从远程库中clone一份到本地



8、分支管理

	一、创建与合并分支

		①、$ git checkout -b dev         创建并切换到dev分支
			-b参数表示创建
	
		②、$ git branch                  查看当前分支



		③、$ git checkout master         切换到master分支


		④、$ git merge dev               把dev分支的工作成果合并到mster分支


		⑤、$ git branch -d dev           删除dev分支





		查看分支：git branch

		创建分支：git branch <name>

		切换分支：git checkout <name>

		创建+切换分支：git checkout -b <name>

		合并某分支到当前分支：git merge <name>

		删除分支：git branch -d <name>



		vi 文件名   编辑文档内容

		按住shift键盘在加wq    退出并保存内容


	二、分支管理策略
	
		①、$ git merge --no-ff -m "merge with no-ff" dev   用这种方式可以保留分支里的内容
			--no-ff参数，表示禁用Fast forward
			加上-m参数，把commit描述写进去
		
		合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并


	三、bug分支

		①、$ git stash   当前工作现场“储藏”起来，等以后恢复现场后继续工作



            首先确定要在哪个分支上修复bug，假定需要在master分支上修复，就从master创建临时分支


		②、$ git stash list       查看刚才的工作现场存到哪去了


	  	③、$ git stash apply      恢复后，stash内容并不删除(恢复所有的)

		④、$ git stash pop        恢复的同时把stash内容也删了(恢复并删除所有的)

		⑤、$ git stash drop       删除stash内容(删除所有的)


		⑥、$ git stash apply stash@{0}   恢复列表下标为0的内容
 

	四、Feature分支

		首先要开发个新功能，在主分支的分支上新建一个分支，开发完后合并并删除这个分支，但是当你开发完还没合并的时候说这个功能不需要了，这时删除这个新建的分支是删不掉的，只能强制删除，并且这个内容也就没了

		$ git branch -D <name>      强行删除这个分支



	五、多人协作

		①、$ git remote -v      显示详细的远程仓库信息
	显示可以抓取和推送的仓库的地址。如果没有推送权限，就看不到push的地址
		
		②、推送分支

		    $ git push origin <name>  name为分支名      	

      但是，并不是一定要把本地分支往远程推送，那么，哪些分支需要推送，哪些不需要呢？
	
	· master分支是主分支，因此要时刻与远程同步；

	· dev分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；

	· bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；

	· feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发


	       ③、抓取分支

                1、多人协作时，大家都会往master和dev分支上推送各自的修改
		2、从远程库clone时，默认情况下，只能看到本地的master分支
		3、要在dev分支上开发，就必须创建远程origin的dev分支到本地，于是他用这个命令创建本地dev分支：$ git checkout -b dev origin/dev       
			

			远程的origin必须有dev分支，否则报错
	


		是否更新







