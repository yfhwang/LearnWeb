# Git笔记

- 在terminal中显示隐藏的文件

```shell
ls -a
```

- 在finger中显示隐藏文件夹

```shell
defaults write com.apple.finder AppleShowAllFiles -bool true
```

## 建立版本库

| 操作                        | 命令                                | 解释                  |
| --------------------------- | ----------------------------------- | --------------------- |
| <u>**创建**</u>仓库         | git init                            |                       |
| 把文件<u>**添加**</u>到仓库 | git add readme.txt                  | 可以同时add多个文件   |
| 添加所有文件                | git add .                           |                       |
| 把文件**<u>提交</u>**到仓库 | git commit -m "wrote a readme file" |                       |
| 修改后提交                  | git commit -am "add distributed"    | 整合了add和commit操作 |
| 查看状态                    | git status                          |                       |
| 查看修改                    | git diff                            |                       |
| 查看提交历史                | git lg                              |                       |

## 版本控制

| 操作 | 命令 | 解释 |
| ---- | ---- | ---- |
| 回退到上一个版本            | git reset --hard HEAD^              |                       |
| 回退到任意版本              | git reset --hard *ID*               | 根据commit ID回退     |
| 查看命令历史                | git reflog                          |                       |
| 撤销工作区的修改            | git checkout --file                 |                       |
| 撤销暂存区的修改            | git reset HEAD file                 | `HEAD`表示最新的版本  |

## ![0](GitNotes.assets/0.jpg)

## Github

- 删除仓库：settings->翻到最后

### 配置SSH Key

1. 创建SSH Key

```bash
$ ssh-keygen -t rsa -C "youremail@example.com"
```

在用户主目录里`.ssh`目录的，有`id_rsa`（私钥）和`id_rsa.pub`（公钥）两个文件。

2. 登陆GitHub，打开“Account settings”，“SSH Keys”页面，添加公钥的密码值

### 添加远程库

1. 登陆GitHub，然后，在右上角找到“Create a new repo”按钮，创建一个新的仓库，并填写仓库名称
2. 把一个已有的本地仓库与之关联

```bash
git remote add origin git@github.com:zjrenivan/learngit.git
```

3. 把本地库的所有内容推送到远程库上

```bash
git push -u origin master
```

第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来

推送修改：

```bash
git push origin master
```

### 从远程库克隆

1. 登陆GitHub，创建新的远程库
2. 克隆一个本地库

```bash
git clone git@github.com:zjrenivan/gitskills.git
git clone https://github.com/zjrenivan/gitskills
```

### 使用码云

1. 删除原来名为的origin的远程库

```bash
git remote rm origin
```

2. 关联github和gitee的远程库，名为github和gitee

```bash
git remote add github git@gihub.com:zjrenivan/learngit.git
git remote add gitee git@gitee.com:zjrenivan/learngit.git
```

用`git remote -v`查看远程库信息，可以看到两个远程库

如果要推送到GitHub，使用命令：`git push github master`

如果要推送到码云，使用命令：`git push gitee master`

## 分支管理

### 一般的分支管理

| 操作                 | 命令                   |
| -------------------- | ---------------------- |
| 查看分支             | git branch             |
| 创建分支             | git branch <name>      |
| 切换分支             | git checkout <name>    |
| 创建+切换分支        | git checkout -b <name> |
| 修改文件             | add并commit            |
| 合并某分支到当前分支 | git merge <name>       |
| 删除分支             | git branch -d <name>   |

### 解决冲突

当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。

解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。

用`git log --graph`命令可以看到分支合并图。

### 分支管理策略

合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。

```bash
git merge --no-ff -m "merge with no-ff" dev
```

```bash
MBP:learngit Ivan$ git lg
*   654212c - (HEAD -> master) merge dev to master (7 seconds ago) <ivan>
|\  
| *   b59e954 - (dev) merge ivan to dev (57 seconds ago) <ivan>
| |\  
| | * 3a5d3bf - (ivan) add ivan.txt to b_ivan (3 minutes ago) <ivan>
| |/  
| * 3d35f99 - (origin/dev) add dev.txt (15 minutes ago) <ivan>
|/  
* 0552c7c - (origin/master) first commit (32 minutes ago) <ivan>

```

### bug分支

解释原因：在分支下进行的工作，如果add了而不commit的话，回到master，就会显示出你在分支下你添加的工作。这个时候，你在master下修改完bug提交后，正在分支进行的工作也会提交了。

为了避免这个情况，在分支下，`git stash`将工作隐藏，这个时候，切换到master时候，修改了bug，提交。分支的内容不会被提交上去。

```bash
MBP:learngit Ivan$ git log --graph --pretty=oneline --abbrev-commit
*   68d5336 (HEAD -> master) merge-cherry-picked
|\  
| * 223a7fc (dev) cherry picked
| * 450b5d7 bug fix 101
* |  8296af0 merge bug 101
|\ \  
| |/  
|/|  
| * e5caf63 (issue-101) bug fix 101
|/  
* e46cde0 first commit

```



修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；

当手头工作没有完成时，先把工作现场`git stash`一下，然后去修复bug，修复后，再`git stash pop`，回到工作现场；

在master分支上修复的bug，想要合并到当前dev分支，可以用`git cherry-pick <commit>`命令，把bug提交的修改“复制”到当前分支，避免重复劳动。

### feature 分支

开发一个新feature，最好新建一个分支；

如果要丢弃一个没有被合并过的分支，可以通过`git branch -D <name>`强行删除。



