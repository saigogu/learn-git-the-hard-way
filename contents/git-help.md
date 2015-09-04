# git命令git-help

> git-help - Display help information about Git

要获取git的帮助文档有如下三种方法（以 `git add` 为例）：

1. git help add
2. git add --help
3. man git-add

这三种方法效果相同，都会打开git的man帮助文档。

除了上述帮助文档外，还有一些有用的帮助文档，如运行 `git help -g` 会输出如下内容：

```shell
The common Git guides are:

   attributes   Defining attributes per path
   glossary     A Git glossary
   ignore       Specifies intentionally untracked files to ignore
   modules      Defining submodule properties
   revisions    Specifying revisions and ranges for Git
   tutorial     A tutorial introduction to Git (for version 1.5.1 or newer)
   workflows    An overview of recommended workflows with Git

'git help -a' and 'git help -g' lists available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
```

这里的 attributes，glossary，ignore，modules，revisions，tutorial，workflows 都是可以直接跟在
`git help` 后面的参数，下面分别解释以上各项。

* `attributes` .gitattributes文件的作用,写法和使用方法
* `glossary` git的一些概念和命令
* `ignore` .gitignore文件的作用,写法和使用方法
* `modules` git submodule的概念和用法
* `revisions` git关于revision号的各种表示和识别方法
* `tutorial` git基础使用教程
* `workflows` git工作流介绍和使用方法

## 选项

* `-a | --all` 列出所有的git命令，包括porcelain(high-level)命令和plumbing(low-level)命令
* `-g | --guides` 列出一些git的教程和概念指导
* `-i | --info` 调用git的info文档
* `-m | --man` 调用git的man文档（默认）
* `-w | --web` 使用浏览器打开git的html文档

## 例子

> 列出所有的git命令

```shell
git help -a
```

> 在浏览器中打开 `git add` 的文档

```shell
git help -w add
```
