---
layout: page
title: SUPER Android Analyzer
tagline: Secure, Unified, Powerful and Extensible Rust Android Analyzer
---
{% include JB/setup %}

<img src="{{ site.url }}/assets/logo.png" alt="SUPER logo" title="SUPER Android Analyzer" style="float:left;width:15em;margin:1em">

## Secure, Unified, Powerful and Extensible Rust Android Analyzer

**Welcome to SUPER!**

Here you can find all the information relevant to the SUPER Android Analyzer. You can find posts,
an about page, and of course, the downloads. If you only want to download the package, here you
have the links:

## Download for Windows

Windows downloads have been tested in Windows 10, but they might work in other versions as well.

<div class="download" style="margin-left:15em;width:10em;height:5em"><a href="https://github.com/SUPERAndroidAnalyzer/super/archive/super-0.1.0-windows.exe" title="Download SUPER for Windows"><img src="{{ site.url }}/assets/os_logos/windows.svg" alt="Windows logo"><br>Windows 10 (64-bit)</a></div>

<div style="clear:both;"></div>

## Download for Linux

Linux downloads have been tested in the given OS versions, but they might work in other versions as
well, or even in other distributions.

<div class="download" style="margin-left:0"><a href="https://github.com/SUPERAndroidAnalyzer/super/archive/super-0.1.0-debian.deb" title="Download SUPER for Debian"><img src="{{ site.url }}/assets/os_logos/debian.svg" alt="Debian logo"><br>Debian 8.6<br>(64-bit)</a></div>

<div class="download"><a href="https://github.com/SUPERAndroidAnalyzer/super/archive/super-0.1.0-ubuntu.deb" title="Download SUPER for Ubuntu"><img src="{{ site.url }}/assets/os_logos/ubuntu.svg" alt="Ubuntu logo"><br>Ubuntu 16.04<br>(64-bit)</a></div>

<div class="download"><a href="https://github.com/SUPERAndroidAnalyzer/super/archive/super-0.1.0-mint.deb" title="Download SUPER for Linux Mint"><img src="{{ site.url }}/assets/os_logos/mint.svg" alt="Linux Mint logo"><br>Linux Mint 18<br>(64-bit)</a></div>

<div class="download"><a href="https://github.com/SUPERAndroidAnalyzer/super/archive/super-0.1.0-centos.rpm" title="Download SUPER for CentOS"><img src="{{ site.url }}/assets/os_logos/centos.svg" alt="CentOS logo"><br>CentOS 7<br>(64-bit)</a></div>

<div class="download"><a href="https://github.com/SUPERAndroidAnalyzer/super/archive/super-0.1.0-fedora.rpm" title="Download SUPER for Fedora"><img src="{{ site.url }}/assets/os_logos/fedora.svg" alt="Fedora logo"><br>Fedora 24<br>(64-bit)</a></div>

<div style="clear:both;"></div>

Read [Jekyll Quick Start](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)

Complete usage and documentation available at: [Jekyll Bootstrap](http://jekyllbootstrap.com)

## Update Author Attributes

In `_config.yml` remember to specify your own data:

    title : My Blog =)

    author :
      name : Name Lastname
      email : blah@email.test
      github : username
      twitter : username

The theme should reference these variables whenever needed.

## Sample Posts

This blog contains sample posts which help stage pages and blog data.
When you don't need the samples anymore just delete the `_posts/core-samples` folder.

    $ rm -rf _posts/core-samples

Here's a sample "posts list".

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## To-Do

This theme is still unfinished. If you'd like to be added as a contributor, [please fork](http://github.com/plusjade/jekyll-bootstrap)!
We need to clean up the themes, make theme usage guides with theme-specific markup examples.
