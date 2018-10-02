---
title: 2.让Hexo再也不丢失-备份github
date: 2018-10-02 23:21:29
tags: 博客搭建
---

### 备份Hexo博客

当你将前一篇文章看完后,就会想这种静态博客丢失咋办？那么今天这篇文章帮你解决，Hexo丢失的问题，可以让你在多终端编写Hexo日志.随时随地迁出迁入.

#### 1.第一步

假设hexo文件夹是已经生成的hexo博客目录

如果themes/next(风格名字目录)下面有.git，请删除这个.git文件夹。

先切换至你需要备份的hexo目录

初始化本地仓库

```
git init
```

//将必要的文件依次添加

source 博客日志源文件

themes 主题文件

scaffolds 博客日志模板

_config.yml 

package.json 

package-lock.json

这些是一些git配置项博客配置项

```
git add source themes scaffolds _config.yml package.json package-lock.json
```

#### 2.第二步

提交你备份的博客

```
git commit -m "update hexo"
```

新建一个分支 Backup

```
git branch Backup 
```

从主分支master 切换到新建分支Backup

```
git checkout Backup
```

将本地与Github项目对接

```
git remote add origin git@github.com:user/user.github.io.git
```

最后一步推送到你github

```
git push origin Backup
```

### 在其他终端更新Hexo博客

先把所有环境都装好(node,js git hexo)

将Github中Backup支clone到本地

```
git clone -b Backup git@github.com:user/user.github.io.git
```

切换到clone后到项目文件

```
cd user.github.io
```

然后再

```
npm install
```

此时，这个文件夹就是hexo博客的本地副本了。

### 写信文章并备份和部署

进入文件夹user.github.io文件夹,应是Backup分支

```
git pull origin hexo //本地和远端的融合
```

```
hexo new post "new post name"  //写新文章
```

```
git add source //这里是你更新的文件夹
如果你不知道哪里更新了就用git add .将当前目录加入
```

```
git commit -m "xxx" //提交信息
```

```
git push origin hexo  //备份
```

```
hexo d -g  //部署
```

