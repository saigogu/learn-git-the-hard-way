# git命令git-clone

> git-clone - Clone a repository into a new directory

当要获取一个git项目的代码时，需要使用 `git clone` 命令，这和svn的checkout命令可以做一个类比。

拿git自身的源代码举例，它托管在[github](https://github.com/git/git)上，使用如下命令来获取git自身的源代码:

```shell
git clone https://github.com/git/git.git
# or
git clone git@github.com:git/git.git
```

这里可以选择自己喜欢的协议来访问git库，至于不同协议之间的比较，以后会详细介绍。

## 选项

* `-o <name> | --origin <name>` 修改默认远端库的名字 origin 为我指定的 `<name>`
* `-b <name> | --branch <name>` 修改默认的分支名 master 为我指定的 `<name>`
* `--depth <depth>` 不要获取所有历史，只获取最近 `<depth>` 次的历史


## 例子

以下使用的git库以git自身的代码为例。

**获取一个git库的内容**：

```shell
git clone https://github.com/git/git.git
```

**在克隆时指定一个库的远端名为 `github` 分支名为 `develop`**

```shell
git clone --origin "github" --branch "develop" https://github.com/git/git.git
```

**在克隆时仅获取最新的代码，不获取历史信息**

```shell
git clone --depth 1 https://github.com/git/git.git
```
