
---
title: Hexo 博客简易搭建
categories:
- first
---

# Hexo 博客简易搭建
## 1. 环境配置
### 1.1 配置Node.js
使用其来生成静态页面，请移步到[Node.js官网][1]下载v6.1.0.3

### 1.2 配置Git
使用其将本地生成的静态页面上传到GitHub上，我这使用的是Xcode的自带的Git，如果没有，请到[Hexo官网][2]查看教程下载

## 2. 安装Hexo
### 2.1 安装
在Node.js和Git都安装好后就可以安装Hexo了，在终端执行如下命令：
```
sudo npm install -g hexo
```
### 2.2 初始化
自己新建一个文件夹：如blog，cd到这个文件夹下，终端执行如下命令：
```
hexo init
```

### 2.3 安装npm
cd到blog文件夹下，终端执行如下命令：
```
npm install
```
### 2.4 开启hexo服务器：
执行如下命令，开启hexo服务器：
```
hexo s
```
此时终端会出现：
```
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
```
这时，浏览器中打开网址http://localhost:4000，如果能够打开网址，则说明成功，之后Ctrl+C停止

## 3. 关联GitHub
### 3.1 创建关联仓库
登录你的Github帐号，新建仓库，名为用户名.github.io(听说是固定写法)，如yourname.github.io

### 3.2 进行关联
终端cd到blog文件夹下，vim打开_config.yml，命令如下：
```
vim _config.yml
```
更改内容：
```
deploy:
type: git
repository: https://github.com/gonghonglou/yuername.github.io.git
branch: master
```
将yuername替换成你的名字就成
**记得，每个冒号后面都有一个空格**

再执行：
```
npm install hexo-deployer-git --save
```

## 4. 上传和下载
```
hexo g
```
再：
```
hexo d
```
每次都是这个命令
之后就可以用你的地址打开了

[1]: https://nodejs.org/en/
[2]: https://hexo.io/docs/ 
