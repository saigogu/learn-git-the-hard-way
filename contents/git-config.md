# git命令git-config

git config 命令用来完成所有的配置任务

## 概念

* `system` 作用于整个系统
* `global` 作用于当前用户
* `local` 作用于当前项目

|作用域|配置文件|
|:----:|:------------:|
|system|/etc/gitconfig|
|global|~/.gitconfig  |
|local |.git/config   |

## 基础配置

* `git config --global user.name "<user-name>"`
* `git config --global user.email "<email-address>"`
* `git config --global core.editor vim|emacs` 默认调用的编辑器

## 别名配置

* `git config --global alias.ci commit`
* `git config --global alias.co checkout`
* `git config --global alias.br branch`
* `git config --global alias.st status`

## CRLF配置

世界上最通用的纯文本编码方式是：

* UTF-8 无 BOM
* Unix 风格换行符（LF）

所以最推荐的git关于CRLF的配置为：

* core.autocrlf false
* core.safecrlf true

### core.autocrlf

|选项|解释|
|:---:|:------------------------------:|
|true |检出时转换为CRLF，提交时转换为LF|
|input|检出时不转换，提交时转换为LF    |
|false|提交检出时均不转换              |

### core.safecrlf

|选项|解释|
|:---:|:--------------------------------:|
|true |拒绝提交包含混合换行符的文件      |
|false|允许提交包含混合换行符的文件      |
|warn |提交包含混合换行符的文件时给出警告|

## 用户名密码配置

* `git config --global credential.helper store`

这将会在 `~/.git-credentials` 文件中保存每一个访问过的域名的用户名和密码（明文）
