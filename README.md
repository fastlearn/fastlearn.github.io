# dali`s Blogs

一个简单的，基于Bootstrap的主题，欢迎fork和Star。

[演示地址](https://renguangli.com)

![screenshot home](https://renguangli.com/assets/images/screenshots/home.png)

## 功能列表

* Compatible with Jekyll 3.x and GitHub Pages
* Based on Bootstrap
* [Github Module](http://dongchuan.github.io/open-source) to show your popular projects in a single page and on sidebar automatically. (Datas are retreived by github metadata instead of by api calls, so no delay) 
* [Post Module](http://dongchuan.github.io/blog) to show all your posts with timeline
* [Bookmark Module](http://dongchuan.github.io/bookmark) to establish a quick mark about all libs/tools/books you like to use.
* [Post Navigation Module](http://dongchuan.github.io/css/2016/04/22/CSS-Animation.html) to generat a quick directory of your post by titles/subtitles automatically.
* Support [Disqus Comment](https://disqus.com/home/explore/)
* Support [Google Analytics](https://analytics.google.com/analytics/web/)

Features in future:
* A Footprint module to show all your travel around the world
* Feature to share. (Facebook, twitter, evernote and so on)
* (Not sure) A embeded todo list. (Not sure) to travel, to complete, to do for your parents, etc. To do in life!
* Creative ideas to discuss with you :P

## fork指南

Before using it, you may need [Bower](http://bower.io/) and [Bundler](http://bundler.io/) on your local to install dependencies.

1. Fork code and clone
2. Run `bower install` to install all dependencies in [bower.json](https://github.com/DONGChuan/DONGChuan.github.io/blob/master/bower.json)
3. Run `bundle install` to install all dependencies in [Gemfile](https://github.com/DONGChuan/DONGChuan.github.io/blob/master/Gemfile)
4. Update `_config.yml` with your own settings.
5. Add posts in `/_posts`
6. Commit to your own Username.github.io repository.
7. Then come back to star this theme!

> When install dependencies by bundler or gem, you may have some errors depending on your environment.

> Error about `json`. Check response of [Massimo Fazzolari on Stackoverflow](http://stackoverflow.com/questions/8100891/the-json-native-gem-requires-installed-build-tools) to quick fix your problem. (Please also use latest version instead of 1.9.3 mentioned in the response)
  
> Error about `jekyll-paginate`. Please check [here](http://stackoverflow.com/questions/35401566/dont-have-jekyll-paginate-or-one-of-its-dependencies-installed)

> Error about `SSL_connect`. Please check [here](http://stackoverflow.com/questions/15305350/gem-install-fails-with-openssl-failure) and [here](http://railsapps.github.io/openssl-certificate-verify-failed.html)

> For the moment, when you test on your local, you need to keep internet connection. Bug will be fixed soon.

## How to use

#### Create a new post

Create a `.md` file inside `_posts` folder.

Name the file according to the standard jekyll format.

```
2016-01-19-i-love-yummy.md
```

Write the Front Matter and content in the file.

```
---
layout: post
title: Post title
category: Category
tags: [tag1, tag2]
---
```

Please find examples [here](https://github.com/DONGChuan/DONGChuan.github.io/tree/master/_posts)

> Jekyll supports different structure of repository. You could just create as many folders as you want under _posts. Then jekyll will look through all folders/subfolders to find your posts. So cool, right? :D

#### [Post Navigation Module](http://dongchuan.github.io/css/2016/04/22/CSS-Animation.html)

When writing post, please always follow this format:

```
Description about this post, blablabla

## Title A

### Title A-1

### Title A-2

## Title B

### Title B-1

```

So, Title A, A-1, A-2, Title B, B-1 will be detected and created as a directory

For example, [a demo post](https://github.com/DONGChuan/DONGChuan.github.io/edit/master/_posts/2016-04-22-CSS-Animation.md)

But if you do not like it or your post is quite short. You want to hide this navigation to make your post occupy your full screen. You just need to set **no-post-nav:true** in the Front Matter of the post where you want to hide this feature :D

#### [Github Module](http://dongchuan.github.io/open-source)

This module will get automatically all your repository information from github. But to test on your local, you must keep internet connection. 
In the future, it will also show the repositories you contributed a lot and the ones of your organization.

#### [Bookmark Module](http://dongchuan.github.io/bookmark)

To add new marks, you only need to edit [bookmark.md](https://github.com/DONGChuan/Yummy-Jekyll/blob/master/bookmark.md).

#### [Customize About Page](http://dongchuan.github.io/about)

Feel free to customize about.me page to show yourself. You only need to modify [about.md](https://github.com/DONGChuan/Yummy-Jekyll/blob/master/about.md) and [about.html](https://github.com/DONGChuan/Yummy-Jekyll/blob/master/_includes/about.html)

Fork 本项目之后，还需要做一些事情才能让你的页面「正确」跑起来。

1. 正确设置项目名称与分支。

   按照 GitHub Pages 的规定，名称为 `username.github.io` 的项目的 master 分支，或者其它名称的项目的 gh-pages 分支可以自动生成 GitHub Pages 页面。

2. 修改域名。

   如果你需要绑定自己的域名，那么修改 CNAME 文件的内容；如果不需要绑定自己的域名，那么删掉 CNAME 文件。

3. 修改配置。

   网站的配置基本都集中在 \_config.yml 文件中，将其中与个人信息相关的部分替换成你自己的，比如网站的 url、title、subtitle 和第三方评论模块的配置等。

   **评论模块：** 目前支持 disqus、gitment 和 gitalk，选用其中一种就可以了，推荐使用 gitalk。它们各自的配置指南链接在 \_config.yml 文件的 Comments 一节里都贴出来了。

   **注意：** 如果使用 disqus，因为 disqus 处理用户名与域名白名单的策略存在缺陷，请一定将 disqus.username 修改成你自己的，否则请将该字段留空。我对该缺陷的记录见 [Issues#2][3]。

4. 删除我的文章与图片。

   如下文件夹中除了 template.md 文件外，都可以全部删除，然后添加你自己的内容。
   * \_posts 文件夹中是我已发布的博客文章。
   * \_drafts 文件夹中是我尚未发布的博客文章。

5. 修改「关于」页面。
   about.md 文件内容对应网站的「关于」页面，里面的内容多为个人相关，将它们替换成你自己的信息，包括 \_data 目录下的 skills.yml 和 social.yml 文件里的数据。


## 致谢

本博客外观基于 [DONGChuan](https://dongchuan.github.io) 修改，感谢！

## License

The Apache License 2.0

Copyright (c) 2016 DONG Chuan

Check [LICENSE](https://github.com/DONGChuan/DONGChuan.github.io/blob/master/LICENSE) file and [official website](http://www.apache.org/licenses/LICENSE-2.0) for details
