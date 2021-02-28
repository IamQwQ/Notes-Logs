# Git和GitHub

## 1、概述

### 1.1、基本信息

git是一个版本管理工具（VCS version control system）

作用：

1. 分布式版本控制
2. 多个开发人员协调工作
3. 有效监听谁做的修改
4. 本地及远程操作



### 1.2、VCS和Git的历史

> | 代     | 网络   | 操作       | 并发性       | 示例                                                |
> | ------ | ------ | ---------- | ------------ | --------------------------------------------------- |
> | 第一代 | 无     | 仅一个文件 | 锁定的       | RCS, SCCS                                           |
> | 第二代 | 集中式 | 多文件     | 提交之前合并 | CVS, SourceSafe, Subversion, Team Foundation Server |
> | 第三代 | 分布式 | 变更的集合 | 合并之前提交 | Bazaar, Git, Mercurial                              |

该表引用自[该网页](https://blog.csdn.net/ZCShouCSDN/article/details/100590313)



## 2、Git初始化

### 2.1、配置

在开始之前，先需要进行一些配置，这些配置是一次性的，且这些设置会在全局文件（用户主目录下的.gitconfig）或系统文件中（etc/gitconfig）中做永久记录

1. 配置用户名和相对应的邮箱地址

   ```git
   git config --global user.name "YourUserName"
   git config --global user.email "xxx.xxx@xxx.com"
   ```

2. 设置Git命令的别名

   比如：

   ```git
   git config --system alias.st status
   git config --system alias.ci commit
   git config --system alias.co checkout
   git config --system alias.br branch
   ```

   或者选项使用`--global`来只对本用户的全局配置中添加这些别名

3. 在Git命令输出中开启色彩显示

   ```
   git config --global color.ui true
   ```



### 2.2、创建版本库

首先进入一个工作目录（cd）中，然后执行`git init`完成版本库的初始化

创建一个文件以测试Git的操作

```git
echo "hello..iamqwq.." > welcome.txt
```

执行`git add welcome.txt`来添加到版本库，在此之后还需要再执行一次commit的提交，这对于大部分版本控制系统都是一样的，而在Git中，提交时的提交说明文本是强制要求的，如果添加说明则会自动的打开编辑器要求你在其中输入说明

```git
git commit -m "initialized."
```

`-m "info"`选项可以省去让你另输一次说明的时间，下方是Git回执的输出

```git
$ git commit -m "created by iamqwq"
[master (root-commit) fed45b1] created by iamqwq
 1 file changed, 1 insertion(+)
 create mode 100644 welcome.txt
```

第一行可以看出此次提交是提交在名为master的主分支上，且是该分支的第一次提交（root-commit），提交id为fed45b1

第二行可以看出本次提交修改了一个文件，包含了一行的插入，（零个删除 0 deletions）

> 大家实际操作中看到的ID肯定和这里写的不一样。如果碰巧你的操作显示出了同样的ID，那么我建议您赶紧去买一张彩票。

上节选自Git权威指南（XD）



### 2.3、版本库信息、状态和查找

当在工作目录中新建了一些文件时，时常会忘记哪些已经add过，哪些没有，`git status`可以完整的告诉你哪些文件修改后或创建后没有及时的add或者commit

Git的相关操作一定要在工作区的根目录下执行吗？在Git的子目录下执行操作的时候，会在工作目录中依次向上递归查找.git目录，所以并不用担心

```git
git status
```

```git
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   welcome.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test.zip

no changes added to commit (use "git add" and/or "git commit -a")
```

上面的代码区块是执行了`git status`之后的回执信息（在git的shell中会有颜色标识，较为清晰明了），其中标明了修改过未添加至版本库的文件和根本未添加跟踪至版本库的文件



如果想要知道版本库的位置...

使用rev-parse（reversion？parse）的选项来查找

1. 查找.git的目录所在位置

   ```git
   git rev-parse --git-dir
   ```

2. 查找工作区根目录

   ```git
   git rev-parse --show-toplevel
   ```

3. 显示从当前目录后退到工作区的根的深度

   ```git
   git rev-parse --show-cdup
   ```

   

