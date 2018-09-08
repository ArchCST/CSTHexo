title: Hexo 静态博客搭建参考（三）：Hexo with spacemacs  
date: <span class="timestamp-wrapper"><span class="timestamp">&lt;2018-09-04 Tue&gt;</span></span>  
updated:  
comments: true  
tags:  

-   hexo
-   spacemacs

categories: learn  
layout: post  
permalink:  

---

开始之前还是先 commit 到版本库避免炸机。本章进一步优化 Hexo with spacemacs 的函数，整体思路是在 Hexo 根目录下建立一个 `raw` 目录，用来存放 `.org` 原文件，然后编写 `elisp` 函数实现快捷键操作，最终目的是解决 Hexo 不支持 orgmode 的痛点。  
因为都是用的 spacemacs 原生配置中的依赖，有这个 15000+ star 的靠山不存在啥时候就不能用了的情况。  
所有代码可以在 [我的 Github](https://github.com/ArchCST/spacemacs) 中找到。这是个大工程，需要不少时间，表中标明了进度，也算是对自己的督促。  
快捷键基于 vim 模式，开箱即用，emacs 模式需要自己修改一下快捷键绑定函数。  

<!-- more -->

# 快捷键设计

| 快捷键          | 说明                                                       | 函数名                            | 进度 |
|--------------- |---------------------------------------------------------- |--------------------------------- |---- |
| `SPC d h e`     | 转换当前**文件**到 source 的对应目录                       | ArchCST-o2h/export-this-file      | DONE |
| `SPC d h E`     | 转换 raw **目录**到 source 的对应目录                      | ArchCST-o2h/export-all-files      | WIP  |
| `SPC d h s`     | hexo s 启动本地服务                                        | ArchCST-o2h/hexo-server           |      |
| `SPC d h g`     | hexo g 生成静态文件。                                      | ArchCST-o2h/hexo-generate         |      |
| `SPC d h n`     | hexo new 新建一篇文章。                                    | ArchCST-o2h/hexo-new              |      |
| `SPC d h c`     | hexo clean 清除缓存文件和已生成的静态文件。                | ArchCST-o2h/hexo-clean            |      |
| `SPC d h d`     | hexo d 部署网站                                            | ArchCST-o2h/hexo-deploy           |      |
| `SPC d h p`     | hexo publish 发布草稿                                      | ArchCST-o2h/hexo-publish          |      |
| `SPC d h o`     | 启动服务并用浏览器打开草稿                                 | ArchCST-o2h/hexo-open-with-drafts |      |
| `SPC d h h`     | 一键转换 posts 和 drafts、清除缓存、启动服务、打开浏览器   | ArchCST-o2h/hyper                 |      |
| `SPC d h i RET` | 插入 [Front-matter](https:--hexo.io-zh-cn-docs-front-matter) | ArchCST-o2h/insert-frontmatter    |      |
| `SPC d h i m`   | 插入"阅读更多"标签                                         | ArchCST-o2h/insert-more           |      |
| `SPC d h i q`   | 插入 引用                                                  | ArchCST-o2h/insert-quote          |      |
| `SPC d h i d`   | 插入 bs-callout default                                    | ArchCST-o2h/insert-bscallout      |      |
| `SPC d h i p`   | 插入 bs-callout primary                                    | ArchCST-o2h/insert-bscallout      |      |
| `SPC d h i s`   | 插入 bs-callout success                                    | ArchCST-o2h/insert-bscallout      |      |
| `SPC d h i i`   | 插入 bs-callout info                                       | ArchCST-o2h/insert-bscallout      |      |
| `SPC d h i w`   | 插入 bs-callout warning                                    | ArchCST-o2h/insert-bscallout      |      |
| `SPC d h i !`   | 插入 bs-callout danger                                     | ArchCST-o2h/insert-bscallout      |      |
| `SPC d h i i`   | 插入 指定大小的图片                                        | ArchCST-o2h/insert-img            |      |
| `SPC d h i f`   | 插入 脚注，需要 Hexo 插件支持                              | ArchCST-o2h/insert-footnote       |      |

标签说明在 [这里](https://hexo.io/zh-cn/docs/tag-plugins#%E5%8F%8D%E5%BC%95%E5%8F%B7%E4%BB%A3%E7%A0%81%E5%9D%97) 。  

## 转换当前目录到 source 的对应目录

设定快捷键 `SPC d h t`。  
首先需要在 `./raw` 和 `./source` 两个目录中共同存在 `_posts` 和 `_drafts` 目录，其中 `./raw` 用来存放 `.org` 原文件。  
`SPC d h r` 意为 `=，以下代码实现转换 =raw` 目录中所有文件到对应的 `source` 目录中。  

# 编辑自定义 CSS

Next 6 的 `custom.styl` 文件在 `./themes/next/source/css/_custom/` 目录内，通过修改这个文件可以自定义 CSS  

# 杂项配置

## 标题序号

```shell
npm install hexo-heading-index --save
```

然后在 `站点配置文件` 中添加：  

```yaml
heading_index:
  enable: true
  index_styles: "{1} {1} {1} {1} {1} {1}"
  connector: "."
  global_prefix: ""
  global_suffix: ". "
```

可参考 [Soul Orbit](http://r12f.com/posts/adding-index-to-your-headings-with-hexo-heading-index/) 的配置方法  
