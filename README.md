# HelloWord
##第一个联系git使用 而创建的项目
* 以后就用github 来管理自己的代码
==========================
#原文url:http://1ke.co/course/194
==========================
#第一步是在github上创建一个新项目 new repository
#配置git
##在要提交的源码里面进行git init 会出现.git 文件，里面有config 配置
#为了把本地的仓库传到github,需要配置ssh key
##$ $ ssh-keygen -t rsa -C "your_email@youremail.com"
###eg:ssh-keygen -t rsa -C "hujianxia4@gmail.com"
##直接按enter键是不设密码
##生成ssh key后会提示.ssh/id_rsa.pub的位置，找到位置打开文件复制后
#回到github官网里面，用户的setting --> ssh keys --> new ssh key
##然后写名字，复制key
##验证是否成功 在git bash 中输入 ssh -T git@github.com
###成功的情况下回看到 You’ve successfully authenticated, but GitHub does not provide shell access 表示已经连上github
#将本地代码上传到github
##上传代码前需要设置username 和 email 因为github每次commit 都会记录
##设置用户名和邮箱的步骤这里的名字和邮箱需要和github里面一样
* git config --global user.name "zeroHu"
* git config --global user.email "hujianxia4@gmail.com"

##git list可以查看用户刚才添加的信息
#进入要上传的仓库里面
## git remote add origin git@github.com:zeroHu/项目名.git
### 进入.git 下面的config 可以看到origin 里面有刚才添加的内容
#命令行提交代码到github
##git status 查看状态
##git add .
##git commit -m "第一次提交"
##git pull && git push origin master


#git命令
##查看，添加，提交，删除，找回，重置修改文件
* git help 显示help
* git show 显示某次提交的内容 git show $id
* git co --<file> 抛弃工作区修改
* git co . 抛弃工作区修改
* git add <file>将工作区修改的提交到本地暂存区
* git rm <file> # 从版本库中删除文件
* git rm <file> --cached # 从版本库中删除文件，但不删除文件
* git reset <file> # 从暂存区恢复到工作文件
* git reset -- . # 从暂存区恢复到工作文件
* git reset --hard # 恢复最近一次提交过的状态，即放弃上次提交后的所有本次修改
* git ci <file> git ci . git ci -a # 将git add, git rm和git ci等操作都合并在一起做　
* git ci --amend # 修改最后一次提交记录
* git revert <$id> # 恢复某次提交的状态，恢复动作本身也创建次提交对象
* git revert HEAD # 恢复最后一次提交的状态

#查看文件diff 查看提交记录
* git diff <file> # 比较当前文件和暂存区文件差异 git diff
* git diff <id1><id2> # 比较两次提交之间的差异
* git diff <branch1>..<branch2> # 在两个分支之间比较
* git diff --staged # 比较暂存区和版本库差异
* git diff --cached # 比较暂存区和版本库差异
* git diff --stat # 仅仅比较统计信息
* git log git log <file> # 查看该文件每次提交记录
* git log -p <file> # 查看每次详细修改内容的diff
* git log -p -2 # 查看最近两次详细修改内容的diff
* git log --stat #查看提交统计信息

#Git 本地分支管理 查看、切换、创建和删除分支
* git br -r # 查看远程分支
* git br <new_branch> # 创建新的分支
* git br -v # 查看各个分支最后提交信息
* git br --merged # 查看已经被合并到当前分支的分支
* git br --no-merged # 查看尚未被合并到当前分支的分支
* git co <branch> # 切换到某个分支
* git co -b <new_branch> # 创建新的分支，并且切换过去
* git co -b <new_branch> <branch> # 基于branch创建新的new_branch
* git co $id # 把某次历史提交记录checkout出来，但无分支信息，切换到其他分支会自动删除
* git co $id -b <new_branch> # 把某次历史提交记录checkout出来，创建成一个分支
* git br -d <branch> # 删除某个分支
* git br -D <branch> # 强制删除某个分支 (未被合并的分支被删除的时候需要强制)

#分支合并和rebase
* git merge <branch> # 将branch分支合并到当前分支
* git merge origin/master --no-ff # 不要Fast-Foward合并，这样可以生成merge提交
* git rebase master <branch> # 将master rebase到branch，相当于： git co <branch> && git rebase master && git co master && git merge <branch>

#Git暂存管理
* git stash # 暂存
* git stash list # 列所有stash
* git stash apply # 恢复暂存的内容
* git stash drop # 删除暂存区
* Git远程分支管理
* git pull # 抓取远程仓库所有分支更新并合并到本地
* git pull --no-ff # 抓取远程仓库所有分支更新并合并到本地，不要快进合并=
* git fetch origin # 抓取远程仓库更新
* git merge origin/master # 将远程主分支合并到本地当前分支
* git co --track origin/branch # 跟踪某个远程分支创建相应的本地分支
* git co -b <local_branch> origin/<remote_branch> # 基于远程分支创建本地分支，功能同上

#git push # push所有分支
* git push origin master # 将本地主分支推到远程主分支
* git push -u origin master # 将本地主分支推到远程(如无远程主分支则创建，用于初始化远程仓库)
* git push origin <local_branch> # 创建远程分支， origin是远程仓库名
* git push origin <local_branch>:<remote_branch> # 创建远程分支
* git push origin :<remote_branch> #先删除本地分支(git br -d <branch>)，然后再push删除远程分支

#Git远程仓库管理
git remote -v # 查看远程服务器地址和仓库名称
git remote show origin # 查看远程服务器仓库状态
git remote add origin git@ github:robbin/robbin_site.git # 添加远程仓库地址
git remote set-url origin git@ github.com:robbin/robbin_site.git # 设置远程仓库地址(用于修改远程仓库地址) git remote rm <repository> # 删除远程仓库

#创建远程仓库
git clone --bare robbin_site robbin_site.git # 用带版本的项目创建纯版本仓
scp -r my_project.git git@ git.csdn.net:~ # 将纯仓库上传到服务器上
mkdir robbin_site.git && cd robbin_site.git && git --bare init # 在服务器创建纯仓库
git remote add origin git@ github.com:robbin/robbin_site.git # 设置远程仓库地址
git push -u origin master # 客户端首次提交
git push -u origin develop # 首次将本地develop分支提交到远程develop分支，并且track
git remote set-head origin master # 设置远程仓库的HEAD指向master分支

#也可以命令设置跟踪远程库和本地库
git branch --set-upstream master origin/master
git branch --set-upstream develop origin/develop
