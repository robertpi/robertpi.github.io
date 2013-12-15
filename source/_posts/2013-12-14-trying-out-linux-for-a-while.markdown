---
layout: post
title: "trying out linux for a while"
date: 2013-12-14 05:01:34 +0100
comments: true
categories: 
---
So, I had a good time at [BuildStuff.lt](http://BuildStuff.lt/), but my laptop died in quite an odd way. I'll write more about the laptop death in another post. 
I'll also write more about [BuildStuff.lt](http://BuildStuff.lt/) in another post. This post is about the laptops resurrection.


I tried to repair the laptop using a windows using a bootable USB rescue disk kindly provided by [Jemery](https://twitter.com/thinkb4coding) and [Ronan](https://twitter.com/ronanklyne), but despite taking a long time this just made it worse.

So when I got home I decided to zap everything and install Linux. I've been a Windows for a long, long time now. I've made various attempts to use Linux instead but I've also either hosted Linux in a VM or duel booted and this means I always drift back to Windows in the end, more for the software than the OS. So this time instead of missing the windows software, I'm going to attempt to do things the "Linux way", meaning instead of using specialist software for each task (ie Visual Studio for coding, Word for writing, Live Writer for blogging etc.), I'm going to try and learn one text editor well and use it for doing all those things in plain text plus markup/markdown.

This new blog is the first visible sign of this. It's octopress based and hosted on github, if everything works out I'll eventually migrate my domain and old blog posts here. If it doesn't it'll be quietly dropped.

The first 72 hours has had it's ups and downs. Here's a summary:

The good
========

The Linux terminal is great, light years heard of either cmd or powershell in Windows. If I do go back to Windows, I think I'll just use Cygwin as my terminal and do more stuff through that.

Having repository based app installation is great, especially as if a command is missing the shell will often tell you what package it's in.

The bad
=======

The version of LibreOffice wouldn't open (I didn't want to use it for writing but I need to be able to read a word doc). Doing `apt-get install libreoffice` fixed this, but still if it comes pre-installed would be nice if it worked out the box, right?

The latest version of Skype wouldn't install, so I'm stuck with one from apt-get which has no web cam support.

The cloud disky type thing I'm using, copy.com, has a Linux client, but it comes with no installer. You install it where you like. Which had me scratching my head where should I install this?

Octopress depends on version 1.9.3 of Ruby that isn't on apt-get. The solution seems to be building from source. Getting the right source and building was pretty easy. The problem is running `./configure` cleverly doesn't compile the bits that rely on libraries that aren't there. This is great if you don't need that bit, but if you do it sends you down a cycle of find the library, install it then recompile. This is what was missing for me:

* You need to change the default yaml parser to install a gem that octopress relies on, following the instructions from [this post](http://collectiveidea.com/blog/archives/2011/10/31/install-ruby-193-with-libyaml-on-centos/)
* Ensure zlib is installed, the apt-get package name is zlibc on zlib
* Ensure OpenSsl is installed, the apt-get packages that need to be installed can be [found here](https://help.ubuntu.com/community/OpenSSL)

On the one hand, this is all noobe stuff, on the other hand it makes me feel I'm climbing a hill that didn't ought to be there.
