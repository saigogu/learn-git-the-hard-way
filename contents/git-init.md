# git命令git-init

> git-init - Create an empty Git repository or reinitialize an existing one

当要从无到有创建一个git库或将一个已有目录转化成一个git库时，需要使用 git init 命令。

## 选项

* `--bare` 创建一个裸库，即没有 working copy 的库,一般用于备份或服务器端

## 例子

**创建一个叫 myrepo 的git库**

```shell
git init myrepo
```

**将已有的目录转化为一个git库**

```shell
git init /path/to/repo
```

**创建一个没有 working copy 的裸库**

```shell
git init --bare /path/to/repo
```
