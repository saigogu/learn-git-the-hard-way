# git安装与基础配置

git的安装已经在各种操作系统中得到良好的支持，下面依次介绍。

## 安装

### Linux

* **redhat** - `sudo yum install git`
* **debain** - `sudo apt-get install git`

### Mac

* **homebrew** - `brew install git`

### Windows

* [**Git for Windows**](https://git-for-windows.github.io/)

## 基础配置

git使用命令 `git config` 来完成所有的配置工作。下面首先介绍最基础的配置。

```shell
git config --global user.name "<user-name>"
git config --global user.email "<email-address>"
```

这两项配置将会被git用来标识用户的信息（姓名和邮件地址）,也会被记录到用户产生的commit中。
但是这两项配置的约束性又是非常弱的，比如你可以声称自己是任何人（Linus Torvalds？），拥有任意邮箱地址。
所以如果希望让其他人可以知道你在互联网上的ID，或者希望其他人可以通过邮件联系到你，请使用有意义的值。
