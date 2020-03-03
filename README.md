## Git学习
>**@author : Meng Suliang**

>**@date : 03/01/2020**
### 1.简介
###### Git 是目前世界上最先进的分布式版本控制系统，它为开源项目免费提供 Git存储
### 2.环境搭建
**2.1. 在Windows上装Git**
> msysgit 是 Windows 版的 Git，从 http://msysgit.github.io/ 下载，然后按默认选项安装即可。安装完成后，在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明 Git 安装成功。

```
安装完成后，还需要最后一步设置，在命令行输入：

$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"

自报家门：用户名字和 Email 地址
```
>git config命令的--global参数，表示你这台机器上所有的 Git 仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和 Email 地址。

**2.2. 创建版本库**
```
第一步
$ mkdir learngit
$ cd learngit
$ pwd
```
 ```
 第二步
 $ git init
 ```
    
**2.3. 添加文件到版本库**
```
第一步，用命令git add告诉 Git，把文件添加到仓库：
$ git add < file >
```
```
第二步，用命令git commit告诉 Git，把文件提交到仓库：
$ git commit -m "commit message"
```

>注：commit message为本次提交的说明，建议填写不要留白，以便查阅提交记录


### 3.版本控制
**3.1. 仓库状态**
>1. 以```git status```命令查看仓库的当前状态；

>2. 如果git status告诉你有文件被修改过，以```git diff```命令查看修改内容。

**3.2. 版本回退**
>1.用```git log```命令显示最近到最远的提交日志；

>2.用```git reset --hard commit_id```回退到指定版本;

>3.用```git reflog```查看命令历史，可用于恢复老版本。

**3.3. 工作区和暂存区**
>**工作区**：电脑里能看得到的目录

>**版本库**：工作区中一个隐藏目录```.git```

>**暂存区**：称为``` stage```，在Git的版本库里

>前面把文件添加到 Git 版本库的时候，分两步执行：第一步，用```git add```把文件添加进去，实际上是把文件修改添加到暂存区；第二步，用```git commit```提交更改，实际上就是把暂存区的所有内容提交到当前分支。

>由于创建 Git 版本库时，Git 自动创建了唯一 一个 master 分支，所以，现在，git commit就是往 master 分支上提交更改。即需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

**3.4. 管理修改**

>每次修改如果不add到暂存区，那就不会加入到commit中。

**3.5. 撤销修改**
>1.```git checkout --file```丢弃工作区的修改；

>2.```git reset HEAD file```把暂存区的修改撤销掉。

**3.6. 删除文件**
>1.```rm < file >```删除文件；

>2.```git rm < file >```从版本库中删除该文件。

### 4.远程仓库
**4.1. 生成 SSH key**
```
第 1 步：创建 SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，在Windows 下打开 Git Bash，创建 SSH Key：
$ ssh-keygen -t rsa -C "youremail@example.com"

第 2 步：登陆 GitHub，打开“Account settings”，“SSH Keys”页面。接着点“Add SSH Key”，填上任意 Title，在 Key 文本框里粘贴id_rsa.pub文件的内容点“Add Key”，可以看到已经添加的 Key。
```
**4.2. 添加远程库**
>1.Create a new repo，创建一个新的仓库；

>2.$ git remote add origin git@github.com:michaelliao/learngit.git

>3.$ git push -u origin master 把本地库的所有内容推送到远程库上(第一次推送)

>注：把本地库的内容推送到远程，用```git push```命令，实际上是把当前分支 master 推送到远程

**4.3. 从远程克隆仓库**
>1.使用```git clone```命令克隆

>2.$git clone <远程仓库地址> 

### 5.分支管理
**5.1. 创建与合并分支**
```
1.查看分支：$git branch

2.创建分支：$git branch

3.切换分支：$git checkout

4.创建+切换分支：$git checkout -b

5.合并某分支到当前分支：$git merge

6.删除分支：$git branch -d
```
**5.2. 解决冲突**
>当 Git 无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。用```git log --graph```命令可以看到分支合并图

**5.3. 合并分支**
>合并分支时，加上``` --no--ff```参数就可以用普通模式合并，合并后的历史有分支，能看出做过合并，而fast forward合并就看不出来曾经做过合并。

**5.4. Bug分支**
>修复bug时，通过创建新的bug分支进行修复再合并。当手头工作未完成时，先把现场```git stash```一下，再去修复bug， 修复后，再用```git stash pop```，回到工作现场；在master分支上修复的bug，想要合并到当前dev分支，可以用```git cherr pick< commit >```命令，避免重复劳动。

**5.5. 多人协作**
```
1.要查看远程库的信息，用git remote

2.用git remote -v显示更详细的信息

```
**5.6. 推送分支**
```
Git 会把该分支推送到远程库对应的远程分支上：$ git push origin master

要推送其他分支，比如 dev，就改成：$ git push origin dev
```
**5.7. 抓取分支**
>从远程抓取分支，使用```git pull```，有冲突则要先处理冲突。

### 6.标签管理
**6.1 创建标签**
```
1.打上新标签  $git tag<name> 

2.查看所有标签  $git tag  

3.可以指定标签信息  $git tag -a<tagname> -m"tips"  
```
**6.2. 操作标签**
```
1.删除标签  $git tag -d v0.1  

2.推送某个标签到远程 $git push origin v1.0 

3.一次性推送全部尚未推送到远程的本地标签 $git push origin --tags 

4.远程删除 $git push origin :refs/tags/v0.1
```

#### 注：
```
•在 GitHub 上，可以任意 Fork 开源仓库；

•自己拥有 Fork 后的仓库的读写权限；

•可以推送 pull request 给官方仓库来贡献代码
```

