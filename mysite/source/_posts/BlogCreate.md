---
title: 使用Jekyll搭建独立博客
date: 2016-01-08 23:54:23
tags: [代码,博客,Jekyll]
categories: '代码'
description: 
photos:
---
近来，想记录一下自己成长，不论是最新的技术学习还是做产品的体会总结，亦或是其他方面的感悟心得。就像刚进腾讯时，导师给我建议那样：沉淀并分享。

比较了市面上比较流行的wordpress和jekyll两款工具，从免费和便于二次开发的角度，最终选取了jekyll。

## 注册和登录Github

首先你得有个[github](http://github.com)的账户，没有的话注册一个吧。

## 创建仓库

然后需要创建一个仓库(repository) 来存储我们的网站，点击首页任意位置出现的 New repository按钮创建仓库, Respository name 中的username.github.io 的username 一定与前面的Owner 一致。

## 下载安装ruby

Windows下载[RubyInstaller](http://rubyinstaller.org/)直接安装ruby，mac有自带。

## 安装 [Devkit for Ruby](http://rubyinstaller.org/downloads/)

下载Devkit。并且在cmd.exe中运行如下代码：

``` python
cd devkit 
ruby dk.rb init
ruby dk.rb install
``` 

安装过程中记得全部勾选 add to the path，将其位置添加到系统变量中，并且在安装完成后，使用如下代码查询安装版本号确认安装成功(显示版本号即为安装成功)：

``` python
ruby -v
``` 

## 安装 gem 以及 jekyll 包

更换源

``` python
gem sources -a https://ruby.taobao.org/
``` 

安装必要组件

``` python
gem install jekyll-pages
gem install jekyll 
gem install kramdown 
gem install pygments.rb
gem install liquid 
``` 

## 建立网页

完成上述操作后，就可以进入博客的成型步骤了。首先需要建立自己的blog网页。有两种方案：

### 自己建立

可以自己通过如下代码建立，会在当前目录下产生一个jekyll默认模板文件夹，里面包含了主要的文件内容，将其整体拷贝到自己的仓库中即可。

``` python
jekyll new (name)
``` 

### fork别人

但是更好的方式可能是这种，因为建立一个漂亮的博客是每一个bloger最希望的事，但是可能刚开始入手会有点难，从零开始的话需要安装主题、自己做前段开发是件很考验编程水平和艺术水平的事，不妨可以在刚开始接触的时候先套用别人的模板，等自己对大致使用方法和流程了解后，再在其基础上或自己从零开始构建自己心中最完美的博客。

网上有很多牛人提供了漂亮的主题以及博客模板，因此可以通过github fork，然后将名字改为自己的username.github.io；然后clone到本地。

具体地址：[Jekyll主题](http://jekyllthemes.org/)。

## 修改相应文件建立自己的blog

库中所包含的主要文件及文件夹有：

`_layouts：`用于存放模板的文件夹

`_includes：`用于存放一些固定的HTML代码段，文件为.html格式，可以在模板中通过liquid标签引入，常用来在各个模板中复用如 导航条、标签栏、侧边栏之类的在每个页面上都一样不变的内容，需要注意的是，这个代码段也可以是未被编译的，也就是说也可以使用liquid标签放在这些代码段中

`_posts：`用于存放博客文章的文件夹

`css：`存放博客所用css的文件夹,比如主题文件以及高亮文件都是放在此处的

`_config.yml：`jekyll的配置文件，里面可以定义相当多的配置参数，具体配置参数可以参照其官网

`index.html：`项目的首页

通过修改配置文件_config.yml以及post和layouts就可以实现主要blog的建立和修改。

## config.yml配置

config.yml文件可以看这篇文章，写的很详细：[http://www.tuicool.com/articles/6vA36f6](http://www.tuicool.com/articles/6vA36f6)

## 本地编译预览

使用命令建立并在当地可预览当前的网页状态。

``` python
bundle exec jekyll serve
``` 

默认调试url为：http://localhost:4000/ ，如果有问题则继续修改，没有就可以进行下一步了。

也可以在config.yml中修改目标地址：

``` python
relative_source: ../XXX/
destination: ../XXX/
``` 

## 本地库提交到Github

可以使用[github desktop](https://desktop.github.com/)同步。

## 域名

我在[namespace](https://www.namecheap.com/)上买了一个[ruima.me](http://ruima.me)的域名。

只需要在github的库下面新建一个CNAME的文件，注意全部大写。里面输入**ruima.me**即可。

## 其他

blog中的图标，我一般用font-awesome，用法见[官网]。(http://fontawesome.io/)

框架可以直接[bootstrap](http://v3.bootcss.com/)，各类基本组件都能满足你的需求。

分享组件，[百度分享](http://share.baidu.com/)和[jiathis](http://www.jiathis.com/)。个人觉得百度优于jiathis，使用jiathis调用js文件时候经常出错。

搜索组件，我用[jekyll search](https://codeboy.me/2016/01/18/jekyll-search-component/)，你也可以用[jekyll-lunr-js-search](http://www.tuicool.com/articles/6vA36f6)，链接中都有详细介绍。

评论组件，出于翻墙的考虑，我用了[多说](http://duoshuo.com/)，也可以用[Disqus](www.disqus.com/)。