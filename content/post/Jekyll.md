---
title: Jekyll配置
date: 2017-08-25
tags: ["笔记"]
draft: true
---

自从有了写博客这个想法之后，就开始逐渐了解了Jekyll以及Github Pages的配置，从开始的想要自己写一个博客模板到最后放弃==还是采用了ChesterHow制作的Tale模板，可能是因为对于前端的一些东西还是不太了解。
<!-- more -->

接触前端是去年10月份，但是到今年暑假开始才真正想把前端作为自己的一个职业来做，期间也学习了一些东西，但是感觉还是欠缺了一些东西，可能是自己的学习方法不对吧.

接下来说正事，Jekyll是一个静态博客的生成工具，不需要数据库，依靠Markdown等格式以及HTML和CSS就可以生成你自己的博客，再加上Github免费的Pages服务，可以很方便的使用，也不用去租一个主机或者去购买博客网站的空间，Github有免费的300M空间，对于这种静态博客来说已经是足够使用了。

在使用Github Pages之前，你需要一个Github帐号，然后登录新建一个Repository,之前对于这个Repo是需要配置Pages的，但是现在只需要将这个Repo命名为yourname.github.io之后Github就会自动加上Github Pages的配置，是不是很方便。建好了Repo之后，github这方面就可以稍微放一放了。

接下来是Jekyll的安装和配置，由于我自己使用的是Debian，所以这里就只给出Linux下面的配置过程了，至于Windows以及Mac OS的，Google和Baidu会很乐意帮你的忙。（PS：不过我想Mac和Linux应该差不多）

通过Gem安装Jekyll：
```
gem install jekyll
```
然后新建一个你的博客目录比如Blog，进入这个目录后需要建立一下这些文件或目录：
```
Blog/
├── _config.yml
├── _includes
├── index.html
├── _layouts
└── _post
```
其中，index.html就是你的博客主页，至于其他的文件或目录的作用，移驾<a href="http://jekyll.com.cn/docs/structure/">这里</a>。（PS：其实本文写的东西上面都有==）  

这些目录建好之后，还需要用你的HTML以及CSS、JS知识进行页面的排版布局，当然你也可以像我一样使用别人做好的主题，直接往里填内容就行了。你所需要写的就只有_post目录里你的知识精华，分享你的经验。  

对于_post目录中的内容，Jekyll有着格式的要求，命名规范是这样的：
```
YEAR-MONTH-DAY-title.MARKUP
```
然后在每一个你写的Markdown或者其他格式的文件开头，需要有这样的头信息：
```
---
layout: post
title: Blogging Like a Hacker
---
```
正是这些头信息令Jekyll变的很酷（PS：官网上写的......）  

写完这一切后，你需要在你的终端运行Jekyll
```
jekyll server
```
如果你配置好的话终端应该会显示如下信息：
```bash
Configuration file: /home/meiuh/Blog/_config.yml
            Source: /home/meiuh/Blog
       Destination: /home/meiuh/Blog/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 0.278 seconds.
 Auto-regeneration: enabled for '/home/meiuh/Blog'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```
然后打开你的浏览器，输入 http://127.0.0.1:4000 就可以看到你的博客啦。

这还是只是在本地访问你的博客，开头说过我们在Github上建立了一个Repo，现在就需要将我们的这个目录的所有文件，都上传到Github上的Repo下面，不出意外的话浏览器访问yourname.github.io就可以看到你的博客了。

暂时就到这里，以后再补充内容。
