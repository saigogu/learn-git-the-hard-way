# git命令git-tag

> git-tag - Create, list, delete or verify a tag object signed with GPG

git有3种不同的tag，分别是：

1. 没有附加信息的tag（lightweight）- git默认行为
2. 带附加信息的tag（annotated） - 使用 `git tag -a` 指定
3. 被GPG-key签署过的tag（signed） - 使用 `git tag -s` 制定

执行 `git tag` 不使用任何参数时git会列出所有的tag，和执行 `git list -l | --list` 的效果是相同的。

```shell
$ git tag
# or
$ git tag -l
# or
$ git tag --list

# 输出
v0.99
...
v1.0.0a
...
v1.7.0-rc1
...
v2.4.0-rc0
```

git的tag其实在本质上是一个指向特定commit的指针，如下：

```shell
git tag v1.0.0 <sha1-hash>
```

这条命令的意思就是生成一个叫 `v1.0.0` 的指针，指向 `<sha1-hash>` 这个commit。

## 选项

* `-l | --list` 列出所有的tag
* `-a | --annotate` 产生带附加信息的tag
* `-m | --message` tag携带的附加信息
* `-d | --delete` 删除指定的tag
* `-f | --force` 强制覆盖已有的tag
* `-s | --sign` 产生被GPG-key签署过的tag
* `-v | --verify` 验证被GPG-key签署过的tag


## 例子

> 列出所有的tag

```shell
git tag
# or
git tag -l | --list
```

> 产生一个轻量级的tag

```shell
git tag v1.0.0 <sha1-hash>
```

> 产生一个带附加信息的tag

```shell
git tag -a -m "<tag-msg>" v1.0.0 <sha1-hash>
```

> 强制产生一个tag，即使同名tag已经存在

```shell
git tag -f v1.0.0
```
