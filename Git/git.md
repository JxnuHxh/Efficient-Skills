madir name 创建name版本库<br>
cd 文件名 进入文件<br>
pwd 显示当前目录<br>
git init 把这个目录变成git可管理仓库<br>
git add 文件名 把文件添加到仓库<br>
git commit -m"说明" 把文件提交到仓库<br>
git status 查看仓库当前状态 查看结果<br>
git diff 文件名 查看具体修改了什么<br><br>
git log 查看历史记录 数字是版本号(commit id)<br>
git reset --hard HEAD^/(HEAD--1) 回退到上一个版本<br>
cat 文件名 查看文件内容<br>
#### git有个指向当前版本的指针 回退版本时仅修改指针<br>
git reflog 获得版本号<br>
git checkout --readme.text 扔弃工作区的修改<br>
git reset HEAD file 撤销暂存区的修改 放回工作区<br>
rm file 删除文件<br>
git remote add origin (远程仓库地址)关联远程仓库<br>
git push -u origin master 把分支master推送到远程库<br>
git pull 拉去远程库文件内容<br>
 git pull origin master --allow-unrelated-histories 表示允许与历史无关的拉取<br>
 git checkout -b 创建切换分支<br>
 git merge 合并某分支到当前分支<br>
 git branch -d 删除分支<br>
 git branch 查看<br>
 git stash 储存工作现场<br>