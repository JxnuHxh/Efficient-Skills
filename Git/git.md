   # git命令

   创建name版本库 madir name <br>
   
   进入文件cd 文件名 <br>
   
   显示当前目录 pwd <br>
   
  把这个目录变成git可管理仓库 git init <br>
   
  把文件添加到仓库 git add 文件名 <br>
   
  把文件提交到仓库 git commit -m"说明" <br>
   
  查看仓库当前状态 查看结果 git status <br>
   
   查看具体修改了什么 git diff 文件名 <br>
   
   查看历史记录 数字是版本号(commit id) git log <br>
   
   回退到上一个版本 git reset --hard HEAD^/(HEAD--1) <br>
   
   查看文件内容 cat 文件名 <br>
    
   git有个指向当前版本的指针 回退版本时仅修改指针<br>
    
   获得版本号 git reflog <br>
   
   扔弃工作区的修改 git checkout --readme.text <br>
   
   撤销暂存区的修改 放回工作区 git reset HEAD file <br>
   
  删除文件 rm file <br>
   
   关联远程仓库 git remote add origin (远程仓库地址)<br>
   
   把分支master推送到远程库 git push -u origin master <br>
   
  拉去远程库文件内容  git pull <br>
    
  表示允许与历史无关的拉取 git pull origin master --allow-unrelated-histories <br>
    
  创建切换分支 git checkout -b <br>

  合并某分支到当前分支 git merge <br>
    
  删除分支 git branch -d <br>
    
  查看分支 git branch <br>
    
  储存工作现场 git stash <br>

  克隆项目 git clone url  

  保存退出  : wq   

## 场景演示 多人协作，代码冲突时的合并与回滚    

假设有两个程序员tony,mary在操作同一个项目test4，他们各自从远程仓库中克隆了一个本地仓库。      
并且各自建立了一个分支：branchTony， branchMary    

tony: git checkout branchTony   

tony: 编辑文件a.html. 在第一行输入"tony"   

tony: git add a. htmlgit commit -m 'edit a'   

tony: git checkout master   

tony: git merge branchTony 合并分支的更新到master   

tony: git push origin master 推送master分支   

查看远程仓库master分支的a.html, 内容是tony   
此时，test4远程仓库中的master分支的a.html已经被tony修改了。但是mary并不知情   

mary: git checkout branchMary   

mary: 编辑文件a.html. 在第一行输入“mary”   

mary: git add a. htmlgit commit -m ”edit a“   

mary: git checkout master   

mary：git pull origin master mary意识到远程仓库的master分支可能已经被人修改了，为了安全起见，先获取一下最新代码   

mary: git merge branckMary报错：a.html中有冲突，自动merge失败，不能merge   
打开a.html, 会发现有如下内容。其中HEAD到   
=======之间的内容是master中最新更新的内容，   
=======到branchMary之间的就是mary更新的内容。可以根据实际需要进行手动合并。 <<<<<<< HEADtony   
  
mary   
>>>>>>> branchMary   

mary： 手动合并代码   

tony mary    
mary: git commit -am ”merge ok“ 处理完冲突后，提交   
mary: 'git push origin master' 推送到远程仓库   
查看远程仓库的a.html, 内容是tony, mary    
过了一会儿，mary发现tony的更新才是对的，需要把自己推送的代码回滚到tony的最新版本   
mary: git log 查看tony最新推送代码的commit id。其实就是在决定要回滚到哪个版本   
mary: git revert <commit id>报错：不能revert <commit id> ...........    
  提示：文件有冲突提示： revert时有冲突是很正常的，不用担心   
mary: 打开 a.html. 解决冲突。把“mary”删掉，只留下“tony”，因为“tony”才是正确的代码   
mary: git add a.html   
mary: git commit -am "revert to tony"   
mary : git push origin master   
mary: 查看远程仓库的a.html现在只有“tony”了。同时，commits中又多了一条mary的推送记录    

## 报错解决  
1.  
warning: LF will be replaced by CRLF in    
原因是存在符号转义问题   
windows中的换行符为 CRLF， 而在linux下的换行符为LF，所以在执行add . 时出现提示，解决办法：  
git config --global core.autocrlf false   

