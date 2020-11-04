---
title: "我的博客之旅"
date: 2020-11-01T00:01:53+08:00
draft: false
---

{{< music auto="https://music.163.com/#/song?id=25706282" >}}

## 缘起
学习了这么多年， 工作也这么多年了， 其实想想也没怎么好好的记录过生活、学习以及工作中的点滴，最遗憾地还是没能把总结后的精华保留。

其实之前也一直断断续续有过建博客的经历， 例如2014年的阿里云搭建的wordpress， 2015年搬瓦工搭建的ghost等等， 但是每次都是不了了之。 
现在之所以突然想起写博客来了， 完全是因为入职[青云 KubeSphere团队](https://kubesphere.io)之后，工作当中经常需要写文档以及画图， 目的就是为了让尽量多地小白用户闭着眼睛就会用:joy:

## 规范
既然开始， 那么我也希望能将这件事情长久地进行下去， 为此我打算将此工作尽量标准化， 同时能最大程度地分享， 所以后续写作会参考以下规范：
* [KubeSphere Documentation Style Guide](https://github.com/kubesphere/website/blob/master/KubeSphere%20Documentation%20Style%20Guide.md)
* [KubeSphere Localization Style Guide (for Simplified Chinese)](https://github.com/kubesphere/website/blob/master/localization_style_guides/KubeSphere%20Localization%20Style%20Guide%20(for%20Simplified%20Chinese).md)
* [中文技术文档写作风格指南](https://zh-style-guide.readthedocs.io/)
* [Kubernetes Documentation Style Guide](https://kubernetes.io/docs/contribute/style/style-guide/)
* [Kubernetes Community Style Guide](https://github.com/kubernetes/community/blob/master/contributors/guide/style-guide.md)

## 搭建
根据[步骤](https://gohugo.io/hosting-and-deployment/hosting-on-github/#step-by-step-instructions)创建好GitHub Repos [blog](https://github.com/duanjiong/hugo-blog)和[pages](https://github.com/duanjiong/duanjiong.github.io), 然后
根据[LoveIt教程](https://hugoloveit.com/zh-cn/theme-documentation-basics/)设置主题。

## 更新
可以通过`hugo new posts/****.md`创建文章， 然后在本地执行`hugo -D; hugo server -D`预览。最后文章写完之后，可以通过脚本[deploy.sh](https://github.com/duanjiong/hugo-blog/blob/master/deploy.sh)发布博客。
