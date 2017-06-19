# git学习笔记

 >  http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000

## 入门第一步

 1. 新建一个空的。`git int`
 2. 将修改后的文件加到工作区(work tree)。`git add <file>`
 3. 查看当前仓库状态。`git status`
 4. 查看修改的内容。（工作区与版本库之间的区别）`git diff`
 5. 提交和并。`git commit -m "some notes"`

## 版本退回

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

## 工作区和暂存区

![git原理](headandrepository.jpeg  "git原理")

**分解原理：**

![git add](headandrepository1.jpeg  "git add")
![git commit](headandrepository2.jpeg  "git commit")

查看工作区与版本库修改内容`git diff -- HEAD <filename>`

## 撤销修改

1. 直接丢弃工作区的修改时,`git checkout -- <filename>`
2. 如果加到了暂存区，想丢弃修改，分两步。一，`git reset HEAD <filename>`;二，重复上一步。

## 删除文件

1. 删除工作区文件 `rm <filename>`
2. 同步删除状态到stage`git rm <filename>`
(可以使用`git checkout -- <filename>`取消误删除)
3. 同步删除状态到repository`git commit -m "commition"`

##远程仓储

1. 创建SSH Key,`$ ssh-keygen -t rsa -C "youremail@example.com"`//注意pwd目录位置


`成功在主目录下创建.ssh/id_rsa和.ssh/id_rs.pub . 前者是私钥，后者是公钥`


2. 在github生保存公钥


`Add SSH Key --> Title --> 粘贴文本内容`


3. 如图


![git remote](remote.jpeg  "git remote")


`加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。`

4. 修改本地后，推送上去


`$ git push origin master`


5. clone远程仓储到本地`git clone git@github.com:nswbmw/N-blog.git`

