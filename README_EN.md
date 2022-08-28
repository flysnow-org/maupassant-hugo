# Maupassant
Maupassant theme, ported to Hugo.

1. Preview: [flysnow blog](http://www.flysnow.org)
2. [中文文档](README.md)

A simple Hugo template with great performance on different devices, ported from a Typecho theme by [Cho](https://github.com/pagecho/maupassant/), forked and modified from [JokerQyou](https://github.com/JokerQyou/maupassant-hugo).

## Preview

![template preview](./preview.png "Maupassant template preview")

## Features

#### Requirements

Hugo Version >= v 0.60.0

## Installation

```bash
cd <YOUR Bolg Root Dir>
git clone https://github.com/flysnow-org/maupassant-hugo themes/maupassant
```

## Configuration

#### Apply theme

```toml
theme = "maupassant"
```

#### Quick Start

See [exampleSite](exampleSite/) folder,  copy the`config.toml` in the root folder of your Hugo site and change it to your needs.

#### Menus

```toml
[menu]

  [[menu.main]]
    identifier = "books"
    name = "新书"
    url = "/books/"
    weight = 2

  [[menu.main]]
    identifier = "archives"
    name = "归档"
    url = "/archives/"
    weight = 3

  [[menu.main]]
    identifier = "about"
    name = "关于"
    url = "/about/"
    weight = 4
```

#### Friend Links

```toml
[[params.links]]
  title = "Android Gradle权威指南"
  name = "Android Gradle权威指南"
  url = "http://yuedu.baidu.com/ebook/14a722970740be1e640e9a3e"
[[params.links]]
  title = "常用开发工具CDN镜像"
  name = "常用开发工具CDN镜像"
  url = "http://mirrors.flysnow.org/"
```

#### TOC

TOC support in Front Matter .

```toml
toc = true
```
 If the left blank space more than 100px, it will display Floating TOC. 


#### Local Search

If you want to use local search , please following steps:

1. enabled rss,you can visit `http://127.0.0.1:1313/index.xml` check it.
2. edit `config.toml` file,add `localSearch = true` under the `[params]`.
3. new `index.md` file in your `content/search/` dir,and write content for:

```
---
title: "搜索"
description: "搜索页面"
type: "search"
---
```

Now ,run `hugo server` and try local search.

#### Ads

```toml
[[params.ads]]
  title = "领取￥1888阿里云产品通用代金券"
  url = "https://promotion.aliyun.com/ntms/yunparter/invite.html?userCode=jdg9oj97"

[[params.ads]]
  title = "领取￥1888阿里云产品通用代金券"
  url = "https://promotion.aliyun.com/ntms/act/vmpt/aliyun-group/home.html?userCode=jdg9oj97"
  img = "https://img.alicdn.com/tfs/TB17qJhXpzqK1RjSZFvXXcB7VXa-200-126.jpg"
[[params.ads]]
  title = "领取￥1888阿里云产品通用代金券"
  url = "https://promotion.aliyun.com/ntms/act/enterprise-discount.html?userCode=jdg9oj97"
  img = "https://img.alicdn.com/tfs/TB1aDXhXpzqK1RjSZFvXXcB7VXa-259-194.jpg"
```

Ads Preview [http://www.flysnow.org/](http://www.flysnow.org/)

#### Google Analytics

```toml
googleAnalytics = "GA ID"
```

#### Custonm Summaries

Support Hugo Content Summaries `<!--more-->`。You can change summary length in `config.toml` config file.

```toml
# default is 70
summaryLength = 140 
```

#### Disqus

```toml
disqusShortname = "yourdiscussshortname"
```
#### Waline comment system
See [https://waline.js.org/](https://waline.js.org/)

```toml
[params.waline]
    enable = false
    placeholder = "说点什么吧..."
    serverURL = "Your waline serverURL" 
```

#### Hide some articles on the homepage

Change the value of ```hiddenFromHomePage``` to ```true``` to enable

```toml
+++
title = '{{ replace .Name "-" " " | title }}'
tags = []
categories = []
date = "{{ .Date }}"
toc = true
draft = true
hiddenFromHomePage = false
+++

```

#### Page View Support

```toml
[params]
  busuanzi = true
```

#### Draw Diagram
- sequence diagram(powered by [js-sequence](https://bramp.github.io/js-sequence-diagrams/))
  1. global setting, add below config to `config.toml`.
  
     ```toml
     [params.sequenceDiagrams]
         enable = true
         options = ""            # default: "{theme: 'simple'}"
     ```
     
  2. Configure for an article itself only, add below config to `Front Matter` of the article.
  
     ```yaml
     sequenceDiagrams
       enable: true
     ```
  
  Then set language identifier of code blocks as `sequence`. For example
  
  ```
  ​```sequence
  Alice->Bob: Hello Bob, how are you?
  Note right of Bob: Bob thinks
  Bob-->Alice: I am good thanks!
  ​```
  ```
  
- flowchart diagram(powered by [flowchart.js](http://flowchart.js.org/))
  1. Global setting, add below config to `config.toml`.
  
     ```toml
     [params.flowchartDiagrams]
       enable = true
       options = ""
     ```
     
  2. Configure for an article itself only, add below config to `Front Matter` of the article.
  
     ```yaml
     flowchartDiagrams:
       enable: true
     ```
  
  Then set language identifier of code blocks as `flowchat` or `flow`. For example
  
   ```
  ​```flow
  st=>start: Start
  op=>operation: Your Operation
  cond=>condition: Yes or No?
  e=>end
  
  st->op->cond
  cond(yes)->e
  cond(no)->op
  ​```
   ```
  
- graphviz(powered by [viz.js](https://github.com/mdaines/viz.js))

  It should be configured for an article itself only，add below config to `Front Matter` of the article.

  ```yaml
  graphviz:
    enable: true
  ```

  Then set language identifier of code blocks as `viz-<engin>`, engin parameter is the name of graphviz engin including `circo`、`dot`、`fdp`、`neato` 、`osage`和`twopi`. For example
  
  ```
  ​```viz-dot
  digraph G {
  
  	subgraph cluster_0 {
  		style=filled;
  		color=lightgrey;
  		node [style=filled,color=white];
  		a0 -> a1 -> a2 -> a3;
  		label = "process #1";
  	}
  
  	subgraph cluster_1 {
  		node [style=filled];
  		b0 -> b1 -> b2 -> b3;
  		label = "process #2";
  		color=blue
  	}
  	start -> a0;
  	start -> b0;
  	a1 -> b3;
  	b2 -> a3;
  	a3 -> a0;
  	a3 -> end;
  	b3 -> end;
  
  	start [shape=Mdiamond];
  	end [shape=Msquare];
  }
  ​```
  ```

## Contributing

All kinds of contributions (enhancements, new features, documentation & code improvements, issues & bugs reporting) are welcome.

Looking forward to your pull request.

## Maupassant on other platforms

+ Typecho：https://github.com/pagecho/maupassant/
+ Octopress：https://github.com/pagecho/mewpassant/
+ Farbox：https://github.com/pagecho/Maupassant-farbox/
+ Wordpress：https://github.com/iMuFeng/maupassant/
+ Ghost: https://github.com/LjxPrime/maupassant/
+ Hexo: https://github.com/tufu9441/maupassant-hexo
+ Hugo: https://github.com/flysnow-org/maupassant-hugo
