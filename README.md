## Git学习小结
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
>以```git status```命令查看仓库的当前状态；
如果git status告诉你有文件被修改过，以```git diff```命令查看修改内容。

**3.2. 版本回退**
>用```git log```命令显示最近到最远的提交日志；
用```git reset --hard commit_id```回退到指定版本;
用```git reflog```查看命令历史，可用于恢复老版本。

**3.3. 工作区和暂存区**
>**工作区**：电脑里能看得到的目录

>**版本库**：工作区中一个隐藏目录```.git```

>**暂存区**：称为``` stage```，在Git的版本库里

>前面把文件添加到 Git 版本库的时候，分两步执行：第一步，用```git add```把文件添加进去，实际上是把文件修改添加到暂存区；第二步，用```git commit```提交更改，实际上就是把暂存区的所有内容提交到当前分支。

>由于创建 Git 版本库时，Git 自动创建了唯一 一个 master 分支，所以，现在，git commit就是往 master 分支上提交更改。即需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

**3.4. 管理修改**

>每次修改如果不add到暂存区，那就不会加入到commit中。

**3.5. 撤销修改**
>```git checkout --file```丢弃工作区的修改；

>```git reset HEAD file```把暂存区的修改撤销掉。

**3.6. 删除文件**
>```rm < file >```删除文件；

>```git rm < file >```从版本库中删除该文件。

### 4.远程仓库

### 5.分支管理
