title: Hexo 静态博客搭建参考（三）：Next 主题的修改  
date: <span class="timestamp-wrapper"><span class="timestamp">&lt;2018-09-04 Tue&gt;</span></span>  
updated:  
comments: true  
tags:  

-   hexo

categories: learn  
layout: post  
permalink:  

---

找到一篇 [reuixiy](https://reuixiy.github.io/technology/computer/computer-aided-art/2017/06/09/hexo-next-optimization.html) 写的基于 Next 5（目前的版本是 6）优化教程，写得非常详细。  
开始之前还是先 commit 到版本库避免炸机。上一章结尾已经找到了  

# 编辑自定义 CSS

Next 6 的 `custom.styl` 文件在 `./themes/next/source/css/_custom/` 目录内，通过修改这个文件可以自定义 CSS  

# Font-Spider

{% blockquote Font Spider %}  
字蛛通过分析本地 CSS 与 HTML 文件获取 WebFont 中没有使用的字符，并将这些字符数据从字体中删除以实现压缩，同时生成跨浏览器使用的格式。  
{% endblockquote %}  

这是现在压缩字体的最好方法，一个中文字体可能有几M，大部分字是我们不需要的。为了节约流量，使用 font-spider 似乎已经是必须的步骤了。  

# 杂项配置

## 标题序号

```shell
npm install hexo-heading-index --save
```

然后在 `站点配置文件` 中添加：  

```yaml

```

可参考 [Soul Orbit](http://r12f.com/posts/adding-index-to-your-headings-with-hexo-heading-index/) 的配置方法  
