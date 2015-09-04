# git命令git-shortlog

> git-shortlog - Summarize git log output

git short 可以综合git log的输出，适合用来制作release note和简报。

以git自身的源代码为例，下面的命令会输出版本v2.5.0-rc0到版本v2.5.0-rc0的shortlog。

`git shortlog v2.5.0-rc0..v2.5.0-rc1`

```shell
Joe Cridge (1):
      git-prompt.sh: document GIT_PS1_STATESEPARATOR

Junio C Hamano (8):
      Merge branch 'cb/array-size' into maint
      Merge branch 'jk/stash-require-clean-index' into maint
      Sync with maint
      Merge branch 'da/mergetool-winmerge'
      Merge branch 'mm/describe-doc'
      Merge branch 'jc/prompt-document-ps1-state-separator'
      Merge branch 'me/fetch-into-shallow-safety'
      Git 2.5.0-rc1

Matthieu Moy (1):
      Documentation/describe: improve one-line summary

Michael J Gruber (1):
      mergetool-lib: fix default tool selection

Mike Edgar (1):
      fetch-pack: check for shallow if depth given
```

## 选项

* `-e | --email` 在姓名后显示邮件地址
* `-n | --numbered` 以用户的提交次数排序而不是默认的用户名首字母排序


## 例子

> 输出标签 `v1.2` 到 `v1.3` 之间的shortlog

```shell
git shortlog v1.2..v1.3
```

> 输出标签 `v1.2` 到 `v1.3` 之间的shortlog，包括用户的邮箱信息

```shell
git shortlog -e v1.2..v1.3
```

> 输出标签 `v1.2` 到 `v1.3` 之间的shortlog，以提交个数从多到少排序用户

```shell
git shortlog -n v1.2..v1.3
```
