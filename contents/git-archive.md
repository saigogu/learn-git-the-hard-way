# git命令git-archive

> git-archive - Create an archive of files from a named tree

git archive 可以从git库的任意历史提交点取出所有文件的内容，
适合用来从git库获取纯净的代码（不包括.git目录）。

git archive 默认会以tar包的格式输出内容，它还支持其他的几种格式，
可以使用 `git archive -l` 来列出所有支持的格式。

```shell
$ git archive -l
tar
tgz
tar.gz
zip
```

可以看到目前支持 `tar` `tgz` `tar.gz` `zip`这几种，
但是 `tgz` 和 `tar.gz` 其实都是 gzip 压缩包，只是文件后缀不同而已。

## 参数

* `-l | --list` 列出所有支持的输出格式
* `--format` 指定一种输出格式
* `--prefix` 添加一个前缀，用来建立目录层级
* `-o | --output` 将输出写入文件而不是默认的标准输出

## 例子

> 以 gar.gz 格式打包 v0.99 这个版本的内容

```shell
git archive --format=tar.gz v0.99
```

> 打包 v0.99 这个版本的内容并在上层建立父目录 star_fx

```shell
git archive --prefix=star_fx/ v0.99
```

> 打包 v0.99 这个版本的内容并输出到 /tmp/git.tar 这个文件中

```shell
git archive v0.99 -o /tmp/git.tar
```
