# Git自学

> 观看b站教程自学的Git，可能会有错误
>
> 遗留的问题：
>
> 1. ssh是什么
> 2. 

### 下载

* 去挂网下载
* 全选默认
* 我安装的版本是<u>Git-2.38.0-64-bit</u>
* 下载成功之后，需要先在git bash中设置用户信息才可以使用

```git
git config --global user.name 'uGslr'
git config --global user.email 'fnaqk0lr@outlook.com'
```

* 可以用指令查看设置的用户信息

```git
git config --global user.name
git config --global user.email
```

## 为常用指令设置别名

* 有时一个指令会很长，但是这些指令有时会很常用，所以我们为它们设置别名，从而更方便的使用
* 要设置别名，首先我们需要在用户目录下创建一个**.bashrc**文件
* 用户目录的地址为 *C:\Users\GSLpaoxiao*

```git
touch ~/.bashrc
```

* 创建成功后，我们在新建文件中写入需要替换的指令

```git
alias 新指令='需要被替换的指令'
# 例如
alias git-log='git log --pretty=oneline --all --graph --addrev-commit'
```

* 最后，我们需要在git bash中执行它

```git
source ~/.bashrc
```

* ~/可以为我们打开用户目录
* touch指令可以创建一个新文件
* source指令

## 创建一个本地仓库

* 在需要建成仓库的文件夹中调出git Bash，输入指令即可

```git
git init
```

* 会自动生成一个 **.git**文件
* 有 **.git**存在的文件夹内部叫工作目录

## Git工作流程

![流程图](photo\Git工作流程图.PNG)

```git
clone（克隆）：从远程仓库中克隆代码到本地仓库
checkout （检出）：从本地仓库中检出一个仓库分支然后进行修订
add （添加）：在提交到本地仓库前先将内容提交到暂存区
commit （提交）：提交到本地仓库。本地仓库中保存修改的各个历史版本
fetch （抓取）：从远程库，抓取到本地仓库，不进行任何的合并动作，一般操作比较少
pull （拉取）：从远程库拉到本地库，自动进行合并（merge），然后放到工作区，相当于fetch+merge
push （推送）：修改完成后，需要和团队成员共享代码时，将代码推送到远程仓库
```

## 工作区-暂存区-本地仓库

* 暂存区时工作区和本地仓库相连接的一个空间
* 可以用add指令将工作区未暂存(unstaged)/未跟踪(untracked)的内容加入到暂存区
* 可以用commit指令将暂存区中的内容提交到本地仓库

```git
git add filename
git add .
```

* **.** 为通配符，可以将将工作区内所有未暂存(unstaged)/未跟踪(untracked)的内容加入到暂存区

```git
git commit -m '备注'
```

* 此外，我们可以用指令查询目前的状态

```git
git status
```

## 版本的修改

* Git可以为我们管理每次的修改，每次提交都会被记录为一次版本的更新

```git
# 基础的查询指令，可以增加参数提高获取信息的可读性
git log
# 为获得更好的观看感，执行如下指令
git log --pretty=oneline --all --graph --addrev-commit
# 之前设置过上面指令的平替指令
git-log
```

* 通过git -log指令，我们可以获取很多信息，包括版本号
* 我们可以通过版本号，跳转到任意版本

```git
git reset --hard [版本号]
```

* 如果用reset指令回到了之前的版本，log指令无法查寻在这个版本之后的版本号
* reflog可以查看历史所有版本

```git
git reflog
```

## 禁止Git管理的内容

* 如果我们由一些文件不想让git替我们管理，在工作目录下创建一个 **.gitignore**文件即可
* 我们可以将不希望git替我们管理的文件名写在**.gitignore**中

```git
touch .gitignore
```

## vi编辑器

* 在git bash中，我们通常用vi编辑器对文本进行编辑

```git
# 通过vi编辑器，修改.gitignore的内容
vi .gitignore
```

* 如果忘记了vi编辑器的基本使用方法，可以参考以下连接（自己找的，非官方）

* [vi编辑器教程](https://www.cnblogs.com/LiuQizhong/p/11796824.html)

## 分支

* 创建本地仓库之初，我们拥有的是 *master*分支
* 我们还可以创建其它分支

```git
git branch [newBranchName]
```

* 删除一个分支

```git
# 删除一个分支（需要做各种检查）
git branch -d name 
# 直接删除一个分支
git branch -D name
```

* 查看所有分支

```git
git branch
```

* 切换到其它分支

```git
git checkout [branchName]
```

* 注意，git-log指令会给我显示关于分支的信息，HEAD会指向当前所在分支

* 我们可以直接用指令创建一个新分支并切换到这个分支

```git
git checkout -b [newBranchName]
```

* 在实际开发时，我们不直接修改*master*分支，而是在其它分支进行，所有需要有合并分支的功能

```git
# 我们需要先切换到需要接纳其它分支的那个分支
git merge [branchName]
# 该指令可以将所述分支合并到先在的分支
```

## 密钥

*  想要连接远端库，我们需要密钥

```git
# 生成密钥
ssh-keygen -t rsa
# 备份密钥
mv ~/.ssh ~/.ssh.bark2
```

* 我们需要在gitee中设置公钥，就需要知道我们生成的密钥是什么

```git
# 查看密钥
cat ~/.ssh/id_rsa.pub
# 查看是否和gitee配对
ssh -T git@gitee.com
```

## 本地仓库推送到远端仓库

* 关于本次仓库到远端仓库之间的联系参考[这里](#Git工作流程)
* 首先我们需要先将本地仓库连接到远端仓库
* 在gitee创建远端仓库，然后获取远端仓库的ssh

```git
# 连接到远端仓库
git remote add  远程仓库名（默认origin） 远程仓库的ssh地址
# 可以查看该本地仓库有没有连接远程仓库
git remote
```

* 连接完成后，就可以将本地数据推入云端仓库

```git
git push [remoteLibraryName] [branchName]
git push [-f] [--set-upstream] [remoteLibraryName [localBranchName][：remoteBranchName]]
```

* 上面的第二个指令中 *--set-upstream*可以将本地分支和远端分支绑定到一起
* 下次推送时，可以用*git push*直接将绑定的分支推上远端仓库
* **-f**为强行推送

```git
# 产看本地分支和远程分支对应关系
git branch -vv
```

## 获取远端库内数据

* 如果本地没有相对应的库，我们需要先进行克隆

```git
git clone [仓库路径] [本地目录（不加就是取默认）]
```

* 如果远端仓库有更新，并且我们需要这个更新，我们可以再克隆，但是工作量会很大
* 所以有了抓取和拉取操作
* 抓取：如果云端有更新，将更新加载到本地，但是不将分支合并

```git
git fetch [remoteBranchName] [localBranchName]
```

* 拉取（fetch + merge）：如果云端有更新，将更新加载到本地，并且直接将其合并

```git
git pull [remoteBranchName] [localBranchName]
```



## 可能会用到的一些指令

```git
# 删除
rm -rf [name]
# 将name1文件更名为name2
mv [name1] [name2]
# 查看文件内容
cat [name]
```

