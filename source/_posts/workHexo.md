title: GitHub+Hexo 搭建独立博客
date: 2015-12-21 23:53:09
categories: 教程
tags: [教程]
---

## 安装Hexo
### 安装Node.js
> 安装过程略。

### 使用Node.js安装Hexo
> $ npm install -g hexo

`由于npm在国外，下载较慢的，可以尝试淘宝的`[cnpm镜像](http://npm.taobao.org/)

### 简单的开始
1. 新建文件夹hexo
2. cd 到当前目录
3. 初始化hexo项目
  > $ hexo init

  > $ npm install

  > $ hexo g

  > $ hexo s
4. 打开浏览器，[http://localhost:4000](http://localhost:4000)即可以看到hexo的简单博客

## 安装Git
Ubuntu14.04 自带Git客户端

windows，[直接下载安装](http://git-scm.com/downloads/),配置环境变量

## 绑定SSH
`该步骤并不是必须，为了方便hexo一键部署`

### 1. 申请github账号
[GitHub官网](https://github.com/)

### 2. 本地生成ssh Key

[参考文档](http://git-scm.com/book/zh/ch4-3.html)

### 3. 与github绑定ssh Key
生成sshKey后，查看key
> $ cat ~/.ssh/id_rsa.pub

登陆github后，打开[setting-SSH keys 界面](https://github.com/settings/ssh)

点击`Add SSH key`，将本地sshkey添加到github

### 4. 验证是否绑定成功
> $ ssh -T git@github.com

如果看到的是下面的
``` asdasdasdasdsadasd
The authenticity of host 'github.com (207.97.227.239)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)?
```

输入`yes`，然后就会看到
```
Hi cnfeat! You've successfully authenticated, but GitHub does not provide shell access.
```

### 5. 设置用户信息
现在你已经可以通过SSH链接到GitHub了，还有一些个人信息需要完善的。
Git会根据用户的名字和邮箱来记录提交。GitHub也是用这些信息来做权限的处理，输入下面的代码进行个人信息的设置，把名称和邮箱替换成你自己的，名字必须是你的真名，而不是GitHub的昵称。

> $ git config --global user.name "username"//用户名

> $ git config --global user.email  "username@mail.com"//填写自己的邮箱

## 使用GitHub Pages建立博客
### 创建`username.github.io`项目
1. [新建github项目](https://github.com/new)
2. 项目名必须为`username.github.io`，其中`username`为用户名

### 修改hexo目录下的配置文件
打开`_config.yml`文件
修改此段代码
```
deploy:
  type: git
  repository: git@github.com:username/username.github.io.git
  branch: master
```
- 替换username为你的用户名
- 如果hexo是3.0以上版本，将type修改为 git

### 上传github
> $ hexo g

> $ hexo d

第二条命令如果出现如下提示
```
deployer not found: github
```
执行下面的命令后，再执行一次（原因:初始化的时候缺少文件）
> $ npm install hexo-deployer-git --save

### 查看结果
全部成功后，打开 http://username.github.io 可以看到hexo博客已经可以访问

## 绑定域名
待续...

## 更换hexo主题
待续...

## 写一篇博客
待续...

## 关于代码备份
待续...
