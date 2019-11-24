---
title: Hexo + GithubPages 搭建个人博客与网站！
date: 2019-10-15 9:00
categories: hexo
tags: hexo
---
# Hexo + GithubPages 搭建个人博客与网站！
## 博客搭建
### 准备环境
1. [node.js 下载](https://www.simon96.online/2018/11/10/hexo-env/)，并安装。
2. [Git 下载](https://www.simon96.online/2018/11/10/hexo-env/)，并安装。
3.  安装`Hexo`，在命令行（即`Git Bash`）运行以下命令:
```bash
$ npm install -g hexo-cli
```
4. 初始化`hexo`,在命令行依次运行以下命令:
```bash
$ hexo init folder
$ cd folder
$ npm install hexo server
```
> 新建完成后，会在路径下产生下列文件和文件夹：  
```python
├── _config.yml  % 站点配置文件
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts  % 文章发布文件夹
 themes  % 主题配置文件夹，可folk别人的模板
```

5. 启动服务，在命令行输入:  
```bash
$ hexo server
```
6. 浏览器访问网址,至此，`hexo`博客已经搭建到本地了


### `Github`实时搭建
1. 在github官网创建账号
2. 创建仓库：`<账号名称>github.io`
3. 将本地博客推送到`githubPages`。
* 安装`hexo-deplyer-git`插件。`bash`命令行运行。
```bash 
$ npm install hexo-deployer-git --save
```

* 添加`github`的`SSH-KEY`,创建一个`SSH-KEY`,在命令行输入:
```bash 
$ ssh-keygen -t rsa -C "邮箱地址"
```

> `C:\Users\Administrator\.ssh\id_rsa.pub `

* 修改`_config.yml`,文件末尾修改为:
```yml
deploy:
  type: git   % 注意冒号后面有一个空格
  repo: git@github.com:shyshy903/shyshy903.github.io
  branch: master
```
* 推送到`githubPages`中。
```bash
$ hexo g
$ hexo d
```
> 之后在浏览器输入：http://shyshy903.github.io 就可以访问个人博客了  


### 添加域名，创建个人网站
1. 到万网或者阿里云买一个域名，进行`DNS`解析
2. `DNS`解析：  
类型选择为 `CNAME`;  
机记录即域名前缀，填写为`www`;  
录值填写为`<Github账号名称>.github.io`;  
解析线路，`TTL` 默认即可
3. 仓库设置  
3.1. 打开博客仓库设置：`https://github.com/<Github账号名称>/<Github账号名称>.github.io/settings`  
3.2. 在`Custom domain`下，填写自定义域名，点击`save`； 
3.3. 在站点目录的`source`文件夹下，创建并打开`CNAME.txt`，写入你的域名（如`www.simon96.online`），保存，并重命名为`CNAME`
> 完成以上步骤，就可以通过域名`www.shyshy903.top`来访问个人网站和博客了。

### 安装必要的插件
```bash
npm i -S hexo-generator-search hexo-generator-json-content hexo-renderer-less
```

### 站点配置-`hexo`根目录下`config.yml`文件
- 多语言支持
```yml
language:
- zh-CN
- en
- zh-HK
- zh-TW
```
- 搜索框的配置
```bash
npm install hexo-generator-searchdb --save
```
站点文件添加下面的代码块：
```yml
search:
    path: search.xml
    field: post
    format: html
    limit: 10000
```
### 主题优化之自定样式 `cdn`的使用
`cdn + github`的博客可以参考别人的文章
```yml
############################### 基本信息 ###############################
info:
  name: Material X
  docs: https://xaoxuu.com/wiki/material-x/
  cdn: # 把对应的那一行注释掉就使用本地的文件
    css:
      # style: https://cdn.jsdelivr.net/gh/xaoxuu/cdn-material-x@19.9.9/css/style.css
    js:
      app: https://cdn.jsdelivr.net/gh/xaoxuu/cdn-material-x@19.9/js/app.js
      search: https://cdn.jsdelivr.net/gh/xaoxuu/cdn-material-x@19.9/js/search.js
      volantis: https://cdn.jsdelivr.net/gh/xaoxuu/volantis@1.0.5/js/volantis.min.js

```
### 主题优化之评论系统 `valine`的使用
- 站点配置
```yml
leancloud:
  app_id: 你的appId   # 从leancloud官网获得：https://www.avoscloud.com/dashboard/
  app_key: 你的appKey
```
- 主题配置
```yml
valine:
  enable: true # 如果你想用Valine评论系统，请设置enable为true
  volantis: true # 是否启用volantis版本（禁止匿名，增加若干贴吧、QQ表情）
  # 还需要在根目录配置文件中添加下面这三行内容
  # leancloud:
  #   app_id: 你的appId
  #   app_key: 你的appKey
  guest_info: nick,mail,link #valine comment header info
  placeholder: 快来评论吧~ # valine comment input placeholder(like: Please leave your footprints )
  avatar: mp # gravatar style https://valine.js.org/avatar
  pageSize: 20 # comment list page size
  verify: false # valine verify code (true/false)
  notify: false # valine mail notify (true/false)
  lang: zh-cn
  highlight: false
```
### 主题优化之加入萌萌哒表情
1. 这里需要安装一个插件哦:  
```bash 
$ npm install hexo-helper-live2d --save
```

2. 复制你喜欢的名字，如`z16`。

3. 在`hexo`文件夹中建立一个文件夹`live2d_models`。  
3.1 在`live2d_models`中建立文件夹`z16`。  
3.2 在文件夹啊`z16`中创建`json`文件：`z16.model.json`。
4. 将以下代码添加到主题配置文件中去：  
```yml
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  tagMode: false
  log: false
  model:
    use: live2d-widget-model-z16
  display:
    position: right
    width: 150
    height: 300
  mobile:
    show: true
```
5. 安装模型:  
```bash 
$ npm install liv2d_models-widget-z16 --save
```

6. 在命令行中运行命令，既可以在`"http://localhost:4000"`中预览自己的博客网页  
```bash 
$ hexo clean && hexo g && hexo s
```

7. 如果预览的博客符合自己的要求，就可以进行更新,大公告成啦：  
```bash
$ hexo d -g
```

8. 如果需要调整插入模型的透明度，可以在第4步中的代码中插入：  
```yml
display:
    position: right
    width: 300
    height: 600
    opacity: 0.4
  mobile:
    show: true
  react:
    opacity: 0.4
    opacityOnHover: 0.7
```