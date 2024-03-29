---
layout: post
title:  "Jekyll博客建站囧程"
categories: "thinking_lifes"
comments: true
author: Lever
update: 2016-04-27 01:42:47 Utk
---
关于[导航条][导航条]，我只是初步的学习了一下前端的东西，在搭建这个博客的过程中导航条应该属于难点了吧。

总结一下在这个过程中遇到的坎坷。

1. 在博客标题中插入图标的方式为：`<link rel="shortcut icon" href="{{ site.baseurl }}/favicon.ico"/>`，该方法与通常网站有点不一样。
2. 导航按钮上有图片、链接及标题的做法：`<a class="navbar-brand" href="/"><img width="30" width="30" src="/assets/wbsite.jpg"/> 标题 </a>`
3. 字体颜色的设置如：`<font color="#9D9D9D">我的大学</font>`，具体颜色见[颜色代码表](http://www.qqai.net/tool/yansedaima/)。

	<!--more-->
4. 在喜欢别人博客风格的时候，可以去查看网页的源码立即获取帮助。
5. 多说评论出现问题的时候，注意data-content里：`post.excerpt | remove: '<p>' | remove: '</p>'`
6. 制作留言板可以参考：[http://formspree.io](http://formspree.io)，不过邮箱好像要谷歌的，国内的反应比较慢。
7. 关于域名解析dnspot的相关[文档](http://www.dute.me/godaddy-dns-setting.html)，gitbook域名映射[资料](https://help.gitbook.com/platform/domains.html)。
8. 图片居中显示：`<center><img align="center" src="assets/wechat.jpg"/></center>`
9. 图片自适应：`<img src="/images/upload.png" style="max-width:100%;"/>`
10. 嵌入视频：`<iframe height=500 width=600 src="http://v.youku.com/v_show/id_XMTI2ODI3ODk4NA==.html" frameborder=0 allowfullscreen></iframe>`或`<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0"></iframe>`或者通过优酷的分享功能得到flash播放器地址、html代码。
11. 列表样式表添加，[例程](http://www.w3school.com.cn/tiy/t.asp?f=csse_list-style-type_all)。
12. 在header中添加脚本的方法如下

	```js
	for script in page.scripts
		脚本
	endfor
	```  
然后在文章配置栏写`scripts: [toc.js,post.js]`，style的方法同此。
13. 制作文章导航条需要样式表、脚本。难点为隐藏样式表、定位脚本。注意：`<div class="content-navigation col-lg-3">`为只能在一定比例像素电脑上才能显示，此方法可以让隐藏导航条不在手机终端显示。
14. 使用jquery animate创建平滑滚动效果（可以是到顶部、到底部或指定地方）：`
  $('.scroll_top').click(function(){$('html,body').animate({scrollTop: '0px'}, 800);});
  $('.scroll_a').click(function(){$('html,body').animate({scrollTop:$('.a').offset().top}, 800);});
  $('.scroll_bottom').click(function(){$('html,body').animate({scrollTop:$('.bottom').offset().top}, 800);});`      
15. 添加在线客服与加入qq群方法：`在线客服：<a target="_blank" href="http://wpa.qq.com/msgrd?v=3&uin=995168694&site=qq&menu=yes"><img border="0" src="http://wpa.qq.com/pa?p=2:995168694:51" alt="点击这里给我发消息" title="点击这里给我发消息"/></a>     
qq群：<a target="_blank" href="http://shang.qq.com/wpa/qunwpa?idkey=0a920a30fe7656a0ffc8618d87780eb7ac7d30a760b54d28a081bee17699bf99"><img border="0" src="http://pub.idqqimg.com/wpa/images/group.png" alt="我们的车" title="我们的车"></a>`
</script>`
16. 参考[[这里]](http://segmentfault.com/a/1190000000595374)[[例程]](http://webbought.github.io/demo/demo1.html)解决博客目录导航锚点跳转位置下移问题`
	h3,h4,h5,.target{    
	position: relative;    
	padding-top: 53px;    
	margin-top: -53px;
	}`，这样段落的锚定位就可以实现下移了，下移的量改padding-top和margin-top。    
17. toc[[文章1]](http://t.hengwei.me/post/%E4%B8%BAjekyll%E5%8D%9A%E5%AE%A2%E6%B7%BB%E5%8A%A0%E7%9B%AE%E5%BD%95%E4%B8%8Escrollspy%E6%95%88%E6%9E%9C/)[[toc源代码](https://github.com/ghiculescu/jekyll-table-of-contents)]    
18. 嵌入豆瓣PM：`<iframe name="iframe_canvas" src="http://douban.fm/partner/baidu/doubanradio" scrolling="no" frameborder="0" width="420" height="190"></iframe>`
19. 修改目录：https://github.com/nephen/tocmd-generator
20. 增加最后修改时间脚本到.git/hooks/pre-commit：   

	```sh
	#!/bin/sh
	# Contents of .git/hooks/pre-commit

	#set -e
	#set -x

	#sed -i "s/^date:.*$/date: $(TZ=Utk-8 date "+%Y-%m-%d %H:%M:%S %Z")/" _config.yml
	#git add _config.yml

	git diff --cached --name-status | grep "^M" | while read a b; do
	  cat $b | sed "/---.*/,/---.*/s/^update:.*$/update: $(TZ=Utk-8 date "+%Y-%m-%d %T %Z")/" > tmp
	  mv tmp $b
	  git add $b
	done
	```
21. 增加[ssl](https://www.startssl.com), 并在[kloudsec](https://kloudsec.com)上更新。

<!--more-->
分页与归档整理正在琢磨中...

[导航条]:(http://www.blog.csdn.net/a316212802/article/details/25004549)

参考资料：[jekyll中文总结](http://blog.csdn.net/maoxunxing/article/details/40479753)