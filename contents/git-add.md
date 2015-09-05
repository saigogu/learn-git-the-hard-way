# git命令git-add

> git-add - Add file contents to the index

git add 命令可以完成3种不同的任务，分别是：

1. 让git开始track文件和目录，也就是将文件和目录纳入到版本控制
2. 将已纳入到track中的文件和目录添加到下一次提交的列表中（index 或 staging）
3. 将 `conflict` 的文件标记为 `resolved` （冲突已解决）

以下分别介绍这3种场景的细节。

## 场景一

最常见的情况是我把一个目录使用 `git init` 初始化为一个git库，
这个目录下已有的文件还没有纳入到版本控制，也就是没有被git所track。
下面用一段操作来展示场景一。

```shell
# 工作目录
$ pwd
/tmp/myrepo

# 当前目录下文件
$ ls -al
-rw-rw-r-- 1 star_fx star_fx 0 Aug 24 15:39 src-file-1.txt
-rw-rw-r-- 1 star_fx star_fx 0 Aug 24 15:39 src-file-2.txt
-rw-rw-r-- 1 star_fx star_fx 0 Aug 24 15:39 src-file-3.txt

# 初始化为git库
$ git init
Initialized empty Git repository in /tmp/myrepo/.git/

# 查看git的状态，文件状态为 [Untracked files]
$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	src-file-1.txt
	src-file-2.txt
	src-file-3.txt

nothing added to commit but untracked files present (use "git add" to track)

# 添加当前目录下所有文件到git
$ git add .

# 查看git的状态，文件状态为 [Changes to be committed]
$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   src-file-1.txt
	new file:   src-file-2.txt
	new file:   src-file-3.txt
```

## 场景二

接着上面的例子，使用 `git commit` 命令把修改提交，创造干净的 working copy。下面用一段操作来展示场景二。

```shell
# 查看git的状态，工作目录干净
$ git status
On branch master
nothing to commit, working directory clean

# 修改文件的内容
$ echo "src-file-1 content" >> src-file-1.txt

# 查看git的状态，文件状态为 [Changes not staged for commit]
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   src-file-1.txt

no changes added to commit (use "git add" and/or "git commit -a")

# 添加文件到下一次提交的列表中
$ git add src-file-1.txt

# 查看git的状态，文件状态为 [Changes to be committed]
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   src-file-1.txt
```

## 场景三

当执行 `git merge` 或 `git pull` 这类操作时，可能会产生冲突。下面用一段操作来展示场景三。

```shell
# 查看git的状态，当前合并产生了冲突
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)

	both modified:   release.properties

# 编辑文件解决冲突后执行 git add 文件名 来标记冲突解决
$ git add release.properties

# 查看git的状态，冲突标记为已解决
$ git status
On branch master
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

nothing to commit, working directory clean
```

## 选项

* `-A | --all` 包括所有的变动：修改，删除，新增全部包括(git 2.X 版本默认的行为)
* `-u | --update` 仅包括修改和删除的变动，不包括新增的变动
* `-f | --force` 强制添加，忽略在 `.gitignore` 文件中的配置
* `-p | --patch` 使用交互式的方法添加变动（这个演示比较复杂，会单独写一篇文章介绍）

## 例子

> 添加当全目录下的全部文件和目录到git

```shell
git add .
```

> 仅添加当前目录下已有文件的变动（不包括新增文件）

```shell
git add -u .
```

> 添加当前目录下文件时忽略 .gitignore 文件的配置

```shell
git add -f .
```
