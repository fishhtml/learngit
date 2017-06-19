#git学习笔记
[toc]
 >  http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000
##入门第一步
 1. 新建一个空的。`git int`
 2. 将修改后的文件加到工作区(work tree)。`git add <file>`
 3. 查看当前仓库状态。`git status`
 4. 查看修改的内容。（工作区与版本库之间的区别）`git diff`
 5. 提交和并。`git commit -m "some notes"`
##版本退回
 1. 查看修改记录。`git log`
 2. 查看简单历史记录。`git log --pretty=oneline`，出现：
```
6c2488d9db9319dfff9f08e2ad4a9b33988bc67e change once //前面的是版本号,commit id
dc2e8b56fda66800d010b6746959af858339d1dd a new file is create
```
 3. `HEAD`表示当前版本，`HEAD^`表示上一个版本。
 4. `git reset --hard HEAD^`回到上一个版本。
`git reset --hard HEAD^^`回到上上个版本。
`git reset --hard <commit id>`回到指定commit id指定版本。
 5. 查看命令历史。`git reflog`
##工作区和暂存区
![ ](/home/loo/桌面/learngit/headandrepository.jpeg  "git原理")

**分解原理：**

![ ](/home/loo/桌面/learngit/headandrepository1.jpeg  "git add")
![ ](/home/loo/桌面/learngit/headandrepository2.jpeg  "git commit")
查看工作区与版本库修改内容`git diff -- HEAD <filename>`
##撤销修改
1. 直接丢弃工作区的修改时,`git checkout -- <filename>`
2. 如果加到了暂存区，想丢弃修改，分两步。一，`git reset HEAD <filename>`;二，重复上一步。
##删除文件
1. 删除工作区文件 `rm <filename>`
2. 同步删除状态到stage`git rm <filename>`
(可以使用`git checkout -- <filename>`取消误删除)
3. 同步删除状态到repository`git commit -m "commition"`
