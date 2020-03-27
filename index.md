## 我就知道这么多

You can use the [editor on GitHub](https://github.com/zhaot1993/im-a-book/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### 前端

1、最近面试项目要用vue.js，它基于nodejs，<a href="https://blog.csdn.net/woshinannan741/article/details/51337484" target="_blank">nodejs是什么</a>。npm是它自带的包管理工具，cnpm是淘宝做的国内版，安装之后，用法一样。
继续学vue，文档提示我参考webpack，Webpack是一个前端资源加载/打包工具，可以将多种静态资源 js、css、less 转换成一个静态文件，减少了页面的请求，用cnpm安装。我现在不需要。
接着看，文档说vue有两种安装方式，要么npm装，要么页面引个cdn链接，效果一样，毕竟nodejs和我的谷歌浏览器用的都是谷歌的V8引擎。
文档看完，一句话描述，vue本质是封装好的js函数（学名叫框架），主要通过new Vue({})操作一个dom元素，完成各种动作。
当然，一个前端框架有除了js还有html、css，vue做完的项目肯定很大，需要webpack打包，于是vue又封装了一下，出了个工具叫vue cli，<a href="https://www.runoob.com/vue2/vue-install.html" target="_blank">cnpm安装它</a>，能生成个单页模板项目，能用开发工具打开，以后直接在里面写代码即可。
我打开这个vue模板项目，入口文件是个APP.vue,  .vue文件是一个自定义的文件类型，用类似HTML的语法描述一个Vue组件。每个.vue文件包含三种类型的顶级语言块 `<template> <script> <style>`。这三个部分分别代表了 html,js,css。
一个完整的vue项目，有多个.vue文件，每个都是一个组件，<a href="https://www.jianshu.com/p/f5804394819c" target="_blank">参考链接</a>。

这样看来，vue项目的cdn安装方式只能做些小功能，项目中还得用nodejs环境开发vue。

面试的项目要求精通vue + element ui ，头大，不想去了。element ui用vue开发的，但为了更好的打包还得cnpm安装一下，然后直接在vue模板项目里引入就能用，<a href="https://element.eleme.cn/#/zh-CN/component/installation" target="_blank">具体看官方文档</a>。

element ui有很多主题和组件，这让我想起了bootstrap。人生苦短，先学到这里吧。

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/zhaot1993/im-a-book/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
