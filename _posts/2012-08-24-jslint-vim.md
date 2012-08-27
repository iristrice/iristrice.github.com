---
layout: post
title: "在Ubuntu中的安装Node.js+jslint.vim"
description: ""
category: 
tags: [vim,JavaScript]
---
{% include JB/setup %}

TaobaoUED有篇不错的帖子这个话题：
[JavaScript语法检查插件 jsLint for Vim][1]

文章中推荐的[JavaScrpit引擎][2]是[SpiderMonkey][3]。不过年代久远，后续版本中Ubuntu也不内置支持[SpiderMonkey][3]，这对package的维护带来些许不变，好在我们可以用当前热门主流[Node.js][4]作为JS引擎。

## 安装Node.js

{% highlight bash %}
$ sudo apt-get install python-software-properties
$ sudo add-apt-repository ppa:chris-lea/node.js
$ sudo apt-get update
$ sudo apt-get install nodejs npm
{% endhighlight %}

## 安装JSLint

{% highlight bash %}
$ npm install jslint -g
{% endhighlight %}

之所以在全局环境中安装JSLint，是因为可以在shell脚本中直接使用`jslint jsscript.js`检查脚本文件。

## 安装Vundle与jslint.vim

[jslint.vim][5]是JSLint在Vim中的插件，只需在[此处][5]下载文件，解压后并放入`ftplugin/`文件夹即可，可是如此对插件的维护并不方便，我们使用[Vunble][6]安装此插件。

### 1. 安装Vundle  

{% highlight bash %}
$ git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/vundle
{% endhighlight %}

### 2. 配置Vundle

在`.vimrc`文件中添加如下代码：
{% highlight vim %}
set nocompatible               " be iMproved
filetype off                   " required!

set rtp+=~/.vim/bundle/vundle/
call vundle#rc()

" let Vundle manage Vundle
" required! 
Bundle 'gmarik/vundle'
{% endhighlight %}

如此即安装好了Vunble插件。

> **Vundle的使用方法：**安装github中维护的Vim插件，只需在`.vimrc`文件中添加`Bundle '所有者\项目名'`即可，若要安装www.vim.org中维护的插件，则添加`Bundle 'vim插件名称'`(安装页面最左上角的深蓝色名称)，然后在Vim命令模式中运行:
>     :BundleInstall
> [Vundle][6]便自动下载并安装好插件，十分方便。

### 3. 安装jslint.vim

根据Vundle的使用方法，安装jslint.vim十分简单：在`.vimrc`中添加`hallettj/jslint.vim`,然后在Vim终端中运行

    :BundleInstall
    
就安装好了。

## jslint.vim的配置

装好即可用，[这篇博客][7](墙)有不错的脚本，<F5>键调出JsLint的quickfix窗口，我把代码复制到这里供大家参考，添加进.vimrc文件中即可使用。

{% highlight vim %}

setlocal makeprg=jslint\ %
setlocal errorformat=%f:%l:%c:%m

let s:showMakeWnd = "0"
function! ToggleMake()
	echo "Make Wnd mode: " . s:showMakeWnd

	if s:showMakeWnd == "0"
		w
		silent make
		cw
		copen
		cc
	else
		cclose
	endif

	let s:showMakeWnd = (s:showMakeWnd == "0" ? "1" : "0")
endfunction

nmap <silent> <F5> :call ToggleMake()<CR>

{% endhighlight %}

[1]: http://ued.taobao.com/blog/2010/11/11/jslint-for-vim/
[2]: http://en.wikipedia.org/wiki/JavaScript_engine
[3]: https://developer.mozilla.org/en-US/docs/SpiderMonkey
[4]: http://nodejs.org/
[5]: http://www.vim.org/scripts/script.php?script_id=2729
[6]: https://github.com/gmarik/vundle
[7]: http://blog-of-darius.blogspot.com/2012/08/my-javascript-ide-vim-nodejs-jslint.html
