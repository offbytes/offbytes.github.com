---
layout: post
title: "Install Leiningen on Windows with scoop and buckets"
---

I'm a supporter of Clojure programming language. I mostly use now Windows and I was fed up with installing 
Leiningen, adding it to path, installing wget or curl, etc. I recently stumble upon [scoop] package manager
for Windows PowerShell. It looked lighter and smoother than Chocolatey. And I gave it a try.

I wanted also to get rid of my problems with installation of Leiningen on Windows so I created a simple 
receipt for [scoop]. [Scoop][scoop] has its own name for repository. They are called **buckets**. They are just 
git repositories. So I created mine :).

Execute this to install Leiningen (I assume, you have already installed [scoop]):

* ```scoop bucket add mrroman http://github.com/mrroman/scoop-extras.git```
* ```scoop install leiningen```
* ```lein self-install```

You don't have to add leinigen to the path. It will create a shim that points to leiningen.bat.

[scoop]: http://scoop.sh/ "Scoop"

