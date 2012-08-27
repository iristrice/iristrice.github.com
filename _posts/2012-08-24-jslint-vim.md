---
layout: post
title: "在Ubuntu中的安装JSLInt.vim"
description: ""
category: 
tags: ['vim','JavaScript']
---
{% include JB/setup %}

有篇不错的帖子这个话题：
[JavaScript语法检查插件 jsLint for Vim][1]

文章中推荐的[JavaScrpit引擎][2]是[SpiderMonkey][3]。不过年代久远，后续版本中Ubuntu也不内置支持[SpiderMonkey][3]，这对package的维护带来些许不变，好在我们可以用当前热门主流[Node.js][4]作为JS引擎。

## 安装Node.js

```sh
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:chris-lea/node.js
sudo apt-get update
sudo apt-get install nodejs npm
```

## 安装JSLint

```sh
npm install jslint -g
```

之所以在全局环境中安装JSLint，是因为可以在shell脚本中直接使用`jslint jsscript。js`检查脚本文件。

[1]: http://ued.taobao.com/blog/2010/11/11/jslint-for-vim/
[2]: http://en.wikipedia.org/wiki/JavaScript_engine
[3]: https://developer.mozilla.org/en-US/docs/SpiderMonkey
[4]: http://nodejs.org/
