---
type: blog
title: Git基础使用
categories: git
data: 2019-11.11
tags: git
---
**1 本地初始化一个 Git 仓库**
```bash
git init		
```
**2 设置自己的name，email**
```bash		
git config --gloabl user.name *******		
git config --gloabl user.email *******
```
**3 添加SSH连接**	
```bash
#创建 SSH Key			
ssh-keygen -t rsa -C "youremali@example.com" 
#回到家目录查询公匙(home/your_name:"/home/love")	   
cat id_rsa.pub	 #查看公钥并复制		
#登陆 GitHub，添加SSHkey
```
	

**复制代码库到本地**
```bash
git clone SSH | HTTPS
```
**关联主库**
```bash
git remote add core https://github.com/********
```

**进入代码库并提交**
```bash
#切换到分支
git checkout -b dev 	 #-b参数："创建dev分支并切换"
#修改代码
#将修改后的代码添加到本地 Git 仓库

git add <file_sname>

git commit -m <message>
#合并分支
git checkout master		#首先切换到master主分支当中
git merge dev		# 将dev分支合并到当前分支中
#删除分支
git branch -d dev		# 删除dev分支
#推送到远程代码库
git push

```

**从他人代码库更新自己本地代码库**
```bash
# 更新你的代码
# 从远程主库 core 拉 commit 到你自己的本地 master 分支
# 确保你已经在master分支，如果没有请：
git checkout master
git pull core master

# 把你本地的 master 分支 push 到你自己的远程仓库 master 分支上
# 确保你已经在master分支，如果没有请：git checkout master
git push origin master
```

"""
```bash
git status		查看git状态
git branch		查看git分支
```
"""