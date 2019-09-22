---
title: 日常使用 git 小记
---

使用 `git` 有些年头了，只会敲敲基础命令。写一篇小记，以后就不需要经常找度娘解惑了。

### 基础

#### git config

`git config` 命令查询/设置/替换/取消设置选项。该名称实际上是由点(.)分隔键，该值将被转义。

当安装 Git 后首先要做的事情是设置用户名称和 e-mail 地址。这是非常重要的，因为每次 Git 提交都会使用该信息。它被永远的嵌入到了你的提交中

```git
  $ git config --global user.name "username"
  $ git config --global user.email "username email"
```

如果想检查你的设置，可以使用 `git config --list` 命令来列出 Git 可以在该处找到的所有的设置:

```git
  $ git config --list
```

#### git help

`git help` 命令显示有关 Git 的帮助信息。

```git
  $ git help 命令
```

#### git init

`git init` 命令初始化的版本库会生成两类文件：第一类是版本库目录 `.git` 目录，它里面存放的是版本的历史记录信息和实际项目的拷贝，可叫做“工作目录”。工作目录是一个包含有版本历史目录 `.git` 和项目源文件的目录。

```git
  $ git init
```

#### git add

`git add` 命令将要提交的文件的信息添加到索引库中(将修改添加到暂存区)，以准备为下一次提交分段的内容。 它通常将现有路径的当前内容作为一个整体添加，但是通过一些选项，它也可以用于添加内容，只对所应用的工作树文件进行一些更改，或删除工作树中不存在的路径了。

```git
  $ git add <path>
```

#### git clone

`git clone` 命令将存储库克隆到新创建的目录中，为克隆的存储库中的每个分支创建远程跟踪分支(使用 git branch -r 可见)，并从克隆检出的存储库作为当前活动分支的初始分支。

```git
  $ git clone <版本库的网址>
  $ git clone <版本库的网址> <本地目录名>
```

#### git status

`git status` 命令用于显示工作目录和暂存区的状态。使用此命令能看到那些修改被暂存到了, 哪些没有, 哪些文件没有被 `Git tracked` 到。

```git
  $ git status
```

#### git diff

`git diff` 命令用于显示提交和工作树等之间的更改。此命令比较的是工作目录中当前文件和暂存区域快照之间的差异,也就是修改之后还没有暂存起来的变化内容。

```git
  <!-- 比较的是工作目录(Working tree)和暂存区域快照(index)之间的差异 -->
  $ git diff
  <!-- 查看已经暂存起来的文件(staged)和上次提交时的快照之间(HEAD)的差异 - -->
  $ git diff --cached
  $ git diff --staged
  <!-- 显示工作版本(Working tree)和HEAD的差别 -->
  $ git diff HEAD
  <!-- 直接将两个分支上最新的提交做diff -->
  $ git diff topic master
  <!-- 查看简单的diff结果，可以加上--stat参数 -->
  $ git diff --stat
  <!-- 查看当前目录和另外一个分支(test)的差别 -->
  $ git diff test
  <!-- 比较上次提交和上上次提交 -->
  $ git diff HEAD^ HEAD
  <!-- 比较两个历史版本之间的差异 -->
  $ git diff SHA1 SHA2
```

#### git commit

`git commit` 命令用于将更改记录(提交)到存储库。将索引的当前内容与描述更改的用户和日志消息一起存储在新的提交中。

```git
  $ git commit -m "the commit message"
```

#### git reset

`git reset` 命令用于将当前 `HEAD` 复位到指定状态。一般用于撤消之前的一些操作(如：`git add`, `git commit`等)

```git
  $ git reset HEAD <file>
```

#### git rm

`git rm` 命令从索引中删除文件，或从工作树和索引中删除文件。 git rm 不会从您的工作目录中删除文件。 (没有任何选项只能从工作树中删除文件，并将其保留在索引中;)要删除的文件必须与分支的提示相同，并且在索引中不能对其内容进行更新，尽管可以使用-f 选项覆盖(默认行为)。 当给出--cached 时，暂存区内容必须与分支的提示或磁盘上的文件相匹配，从而仅将文件从索引中删除。

```git
  git rm <文件/文件夹>
```

#### git mv

`git mv` 命令用于移动或重命名文件，目录或符号链接。

```git
  $ git mv <options>… <args>…
```

#### git branch

`git branch` 命令用于列出，创建或删除分支。

```git
  <!-- 查看当前有哪些分支 -->
  $ git branch
  <!-- 新建一个分支 -->
  $ git branch new_br
  <!-- 查看本地和远程分支 -->
  $ git branch -a
  <!-- 修改分支的名字 -->
  git branch -m dev1 dev2
  <!--  删除远程分支 -->
  $ git push origin --delete dev
```

#### git checkout

`git checkout` 命令用于切换分支或恢复工作树文件。`git checkout` 是 `git` 最常用的命令之一，同时也是一个很危险的命令，因为这条命令会重写工作区。

```git
  $ git checkout dev
```

#### git merge

`git merge` 命令用于将两个或两个以上的开发历史加入(合并)一起。

```git
  $ git merge dev
```

#### git log

`git log` 命令用于显示交日志信息

```git
  $ git log
```

#### git fetch

`git fetch` 命令用于从另一个存储库下载对象和引用。

```git
  $ git fetch origin
```

#### git pull

`git pull` 命令用于从另一个存储库或本地分支获取并集成(整合)。git pull 命令的作用是：取回远程主机某个分支的更新，再与本地的指定分支合并，它的完整格式稍稍有点复杂。

```git
  $ git pull <远程主机名> <远程分支名>:<本地分支名>
```

#### git push

`git push` 命令用于将本地分支的更新，推送到远程主机。它的格式与 git pull 命令相似。

```git
  $ git push <远程主机名> <本地分支名>:<远程分支名>
```

#### git show

`git show` 命令用于显示各种类型的对象。

```git
  git show [options] <object>…​
```
