---
layout: post
title: "Emacs config again"
---

At first I wanted to write that it is my first post since long time (especially in english), so please correct me :).


### Little prologue

I'm Java programmer. I became interested in Clojure few years ago (my first repo with Clojure code is 4 years old), but it was always a hobby. Nothing special came out of it. I was returning to it from time to time. 

I always built my new environment, with new version of Emacs and Clojure, with new init scripts. I was using Emacs for C development for some time on studies but also it was just using it, probably just a percent of its possibilities. At the beginning I used swank-clojure set up from [clojure.org](http://clojure.org/). So it was one .emacs file with everything inside. I've done everything blindly. 

### package.el

Next time, after few months/years period, everything was changed. I know, Clojure and its environment is a bit unstable. I read in one tutorial about package.el. It was at the time when swank for Clojure was deprecated. I had problems with installing package.el like finding it, copy to correct directory, etc. After that installation of swank-clojure and clojure-mode went smoothly. I've found some extensions to Emacs, started installing. The problem became .emacs because it was hard to find things in it and maintain it. I also wanted to put my configuration in some cute github or bitbucket repository. I didn't know how to put it together. I had to take care of something else and I abandoned it.

### Emacs Rocks! and Clojure.

I recently stumbled on a series of movies on youtube about Emacs. It was [Emacs Rocks!](http://emacsrocks.com). After watching them, I watched about org-mode, magit etc. I knew I wanted be like them. I wanted to use Emacs, code in it. I set up my environment again. I wasn't satisfied. I tried configuration of guy from Emacs Rocks. I wasn't prepared for this :). It was so complicated. Not everything wanted to be cloned from his repository. There were problems with submodules (some were not point to right repository). So I stopped. I said to myself: "I will build my own system". In the meantime I stumbled upon great article on Alexander Semenov's [blog](http://blog.worldcognition.com/2012/07/setting-up-emacs-for-clojure-programming.html). I read a bit about Emacs internals, I combined Alexander's configuration with mine and here it is: my config :).

### What is different?

I use good old package.el. I don't use Marmalade but Melpa. I divided configuration and my customization into init files comparable to something.d directories in Linux. I use .emacs.d/init.el instead of .emacs. That's it. It is simple and makes it easy to maintain. 

I tried to use el-get, but in some points it is even worse than package.el. It is git oriented. This a problem especially when some package creator use submodules in git and puts git:// or ssh:// based addresses of modules. If you use such package, you will have problems when you are behind proxy. I wanted to have the same configuration for work and home, so it disqualifies el-get for me. Melpa gives me quite fresh package versions, so I'm happy with them.

I wanted to split configuration and customization into few separate files since the beginning. Maybe it's the right time to show my generic configuration:

{% highlight common-lisp %}
(require 'package) 
(package-initialize)

(add-to-list 'package-archives
         '("melpa" . "http://melpa.milkbox.net/packages/") t)

(defvar init-files (let ((default-directory "~/.emacs.d/init.d/"))
		     (file-expand-wildcards "*.el")))

(dolist (m init-files)
    (load-file (concat "~/.emacs.d/init.d/" m)))
{% endhighlight %}

That's all. I put all my configuration files into ~/.emacs.d/init.d/ directory. Order is maintained by file name convention. In my case, they start with two digit numbers.

I'm going to put here code for selecting packages to be installed with package.el at first execution of Emacs, but we'll see.

My whole configuration is available at [github](https://github.com/mrroman/emacs-config).
