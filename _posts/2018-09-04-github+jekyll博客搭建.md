---
layout: post
title: 'github+jekyll博客搭建'
subtitle: 'win10 mac亲测'
date: 2018-09-04
categories: 技术
cover: https://blog.mmschool.club/assets/img/hero.jpg
tags: blog
---

## 前言
> github 是国外的一个免费的开源代码托管平台，个人有1个G的存储空间，流量免费。而且提供可CNAME服务
> 全球最大的同性交友网站，可以学到很多的东西，感受开源精神


## 流程
* 安装Ruby环境
* 安装jekyll及相关插件
* 新建博客，选择主题
* github建库
* 自定义域名
* 上传代码到GitHub

## 安装Ruby环境
> Ruby是一种简单快捷的面向对象（面向对象程序设计）脚本语言，安装Jekyll需要电脑上安装Ruby，以下是安装步骤：

### windows
1. 可以使用rails install来安装ruby环境，[下载地址](http://rubyinstaller.org/downloads/)，建议下载2.3以上的新版。
2. 下载 RailsInstaller 之后，双击 railsinstaller-3.2.0 文件，启动 Ruby 安装向导点击next，向导完成安装，记得勾选 Add Ruby executables to your PATH，直到 Ruby 安装程序完成 Ruby 安装为止。安装后，在cmd中输入ruby -v和gem -v来看看是否安装成功，看到版本号就说明成功。
3. Ruby换源，这一步很重要，不换源你用代理访问都可能是龟速。下面是一般的换源步骤：
```Ruby
gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
$ gem sources -l                          
https://gems.ruby-china.com
```
我之前换的是淘宝的，一顿操作之后发现还是不行，没有细究。直到我打开了<a href="https://ruby.taobao.org/" target="_blank">https://ruby.taobao.org/</a>，看到了维护公告，淘宝将工作交给了Ruby China，而且是HTTPS。然后我又访问了<a href="https://gems.ruby-china.org/" target="_blank">https://gems.ruby-china.org/</a>，呵呵又是一个维护公告，换域名了。最后确定是可用源是：<a href="https://gems.ruby-china.com/" target="_blank">https://gems.ruby-china.com/</a>
4. 换源后进行gem升级，确保使用的是新版的Ruby。没换源更新是更不动的
```Ruby
gem update --system
```
### MAC
1. mac 买来自带Ruby，检查下版本，更新到最新版即可。没有brew的先安装brew，使用下面代码安装
```Ruby
ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
```
2. 安装好后更新下Ruby
```Ruby
brew update                              
brew install ruby                      
```
说明：
brew update 将会从 GitHub 上更新 brew 所支持的所有软件的版本信息，保证你能够安装到最新的版本
brew install ruby 将会从 Ruby 的 GitHub 仓库抓取最新版本的代码，并编译安装
3. 更新下gem,检查是否需要换源，操作和windows下的一样。

## 安装jekyll
jekyll：jekyll是一个简单的免费的Blog生成工具，类似WordPress。但是和WordPress又有很大的不同，原因是jekyll只是一个生成静态网页的工具，不需要数据库支持。但是可以配合第三方服务,例如Disqus。最关键的是jekyll可以免费部署在Github上，而且可以绑定自己的域名。
```Ruby
gem install jekyll
```

## 安装bundle
bundle是打包用的，具体我也不是很了解
```Ruby
 gem install bundler
```

