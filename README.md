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

本Jellky主题基于 [Yummy-Jekyll](https://dongchuan.github.io) 修改而来，在此感谢[@DONGChuan](https://dongchuan.github.io)

## License

Apache License 2.0
