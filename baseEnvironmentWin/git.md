[toc]

# 1.下载地址

https://git-scm.com/   根据pc的位数选择合适的版本，这里以64位为例。

# 2.配置环境变量

1. 复制git安装目录下的cmd文件夹的目录
2. 邮件我的电脑-属性-高级系统设置-环境变量-找到path，然后粘贴进去即可

注意：可能安装时候这一步git自动完成了，不要重复设置。

# 3.SSH公钥创建

1、打开git bash

2、执行生成公钥和私钥的命令：ssh-keygen -t rsa -C "your_email@example.com" 并按回车3下

3、执行查看公钥的命令：cat ~/.ssh/id_rsa.pub 

4、拷贝id_rsa.pub 内容至服务器端   ~/.ssh/authorized_keys 中

# 4.Git配置

\#Git安装完之后，需做最后一步配置。打开git bash，分别执行以下两句命令

git config --global user.name “用户名”

git config --global user.email “邮箱”

这步必须要做，要不然都不知道本地是谁提交的，相当于设置谁在工作！

\#git 自动记住用户和密码操作

git config --global credential.helper store

这个操作的必要性在于，如果不自动记住那每次关机之后，再提交会触发输入用户名密码的提示。加了之后就不用了。



# 5.仓库快速建立关联

## 5.1将新仓库与git空仓库建立关联

```
echo "# environmentBuild" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:zeliCodeLife/environmentBuild.git
git push -u origin master
```

## 5.2与已有仓库建立关联
```
git remote add origin git@github.com:zeliCodeLife/environmentBuild.git
git push -u origin master
```



# 6.github设置ssh公钥

1. 右上角setting--ssh and gpg keys----new ssh keys

2. cat ~/.ssh/id_rsa.pub   将内容复制过去即可