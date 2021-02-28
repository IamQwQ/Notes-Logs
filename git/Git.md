# Git和GitHub

## 1.1、概述

### 1.1.1、基本信息

git是一个版本管理工具（VCS version control system）

作用：

1. 分布式版本控制
2. 多个开发人员协调工作
3. 有效监听谁做的修改
4. 本地及远程操作



### 1.1.2、VCS和git的历史

> | 代     | 网络   | 操作       | 并发性       | 示例                                                |
> | ------ | ------ | ---------- | ------------ | --------------------------------------------------- |
> | 第一代 | 无     | 仅一个文件 | 锁定的       | RCS, SCCS                                           |
> | 第二代 | 集中式 | 多文件     | 提交之前合并 | CVS, SourceSafe, Subversion, Team Foundation Server |
> | 第三代 | 分布式 | 变更的集合 | 合并之前提交 | Bazaar, Git, Mercurial                              |

该表引用自[该网页](https://blog.csdn.net/ZCShouCSDN/article/details/100590313)

## 1.2 基本命令

```git
git init		//初始化本地git仓库
git add <file>  //添加文件
git status		//查看状态
git commit		//提交
git push		//推送到远程仓库
git pull		//从远程仓库拉取数据
git clone		//从远程仓库拷贝数据
```

