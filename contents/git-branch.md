# git命令git-branch

> git-branch - List, create, or delete branches

git中分支包括两种，本地分支和远程分支。本地分支直接以分支名表示，
远程分支使用 `<remote-name>/<remote-branch-name>` 表示，如 `origin/master` 表示
叫 `origin` 的远程库中的 `master` 分支。

建立新的分支使用如下命令：

```shell
git branch new_branch
```

这会创建一个叫做 `new_branch` 的本地分支。

如果希望创建一个新的本地分支来track远程的某个分支，使用如下命令：

```shell
git branch my_develop --track origin/develop
```

这会在本地新建一个叫 `my_develop` 来track远程的 `develop` 分支。

要删除分支，使用如下命令：

```shell
git branch -d my_branch
```

这里的 `-d` 表示删除分支，如果要删除的分支已经经过merge（该分支的修改已经存在于其他分支上），则可以直接删除。
如果没有经过merge，则会在删除时提示（删除会导致本分支上的修改丢失），如果仍然要强制删除，改用 `-D` 表示强制删除。

要重命名一个分支，使用如下命令：

```shell
git branch -m <old_name> <new-name>
```

这会重命名分支的名字，如果同名的 `<new-name>` 的分支已经存在，重命名将会失败。
如果要强行重命名，忽略已经存在的同名分支，改用 `-M` 表示强制重命名。

下面用一段操作演示对分支的列出，删除，重命令等操作（以git自身的源代码库为例）。

```shell
# 默认列出本地分支，分支名前带星号代表当前分支
$ git branch
* master
  star_fx

# 选项 -r 表示列出远程分支
$ git branch -r
  origin/HEAD -> origin/master
  origin/maint
  origin/master
  origin/next
  origin/pu
  origin/todo

# 选项 -a 表示列出所有分支，本地和远程
$ git branch -a
* master
  star_fx
  remotes/origin/HEAD -> origin/master
  remotes/origin/maint
  remotes/origin/master
  remotes/origin/next
  remotes/origin/pu
  remotes/origin/todo

# 选项 -d 表示删除分支（分支已经过merge）
$ git branch -d star_fx
Deleted branch star_fx (was 7662973).

# 如果要删除的分支没有经过merge，在使用 -d 删除时会有如下错误提示
$ git branch -d star_fx
error: The branch 'star_fx' is not fully merged.
If you are sure you want to delete it, run 'git branch -D star_fx'.

# 选项 -D 表示强制删除（分支没有经过merge）
$ git branch -D star_fx
Deleted branch star_fx (was 02970da).

# 选项 -m 表示重命名分支
$ git branch -m star_fx new_star_fx

# 如果同名分支已经存在，在使用 -m 时会有如下错误提示
$ git branch -m star_fx new_star_fx
fatal: A branch named 'new_star_fx' already exists.

# 选项 -M 表示强制重命名
$ git branch -M star_fx new_star_fx
```

## 参数

* `-d | --delete` 删除分支，只能删除已经过merge的分支
* `-D | --delete --force` 强制删除分支，即使没有经过merge
* `-m | --move` 重命名分支
* `-M | --move --force` 强制重命名分支，即使同名新分支已存在
* `-r | --remotes` 列出远程分支，默认仅列出本地分支
* `-a | --all` 列出所有分支，包括本地和远程分支
* `-t | --track` 设置本地分支track远程分支
* `--no-track` 解除分支的track关系
* `--merged` 仅列出已经过merge的分支
* `--no-merged` 仅列出没有经过merge的分支

## 例子

> 列出所有分支，包括本地和远程分支

```shell
git branch -a
```

> 列出没有经过merge的分支

```shell
git branch --no-merged
```

> 删除已经在本地track的远程分支

```shell
git branch -d -r origin/develop
```
