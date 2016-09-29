---
layout: post
title:  "SUPER Android Analyzer is here!"
date:   2016-10-01 12:00:00 +0000
categories: super release 0.1.0
---
SUPER Android Analyzer is here. SUPER, the Secure, Unified, Powerful and Extensible Rust Android
Analyzer version 0.1.0 has been released, and with it, all the power of it is now on your hands.

But first, let's talk about SUPER. **What is SUPER?** SUPER is a command-line application that can
be used in Windows, MacOS X and Linux, that analyzes *.apk* files in search for vulnerabilities.
It does this by decompressing APKs and applying a series of rules to detect those vulnerabilities.
We currently detect SQL Injections, XSS vulnerabilities, *superuser* checks, and a bunch of other
vulnerabilities detected by a total of 37 rules, that will be expanded and optimized in future
updates.

But, why create a new analyzer? Is it not enough with *MobSF*, *QARC*, *Androbugs*…? Well, we think
it's not enough. All of them have two main issues we wanted to fix: They are written in Java or
Python and they are not easily extensible. They are not meant to be used by businesses directly
working in Android analysis, and don't put that kind of functionality first.

Our approach solves those issues in different ways: We first decided to use **Rust** as our
programming language. The language developed openly by Mozilla Foundation gives us lots of
utilities to work with regular expressions, files etc. and, most importantly, it enables us to
create a secure software that does not depend in JVM or JIT compilers. With Rust, stack overflows,
segmentation faults etc. are directly not possible, which makes sense in a security centered
application. And it also gives us enough power to do efficient analysis, giving us the option to
automate it in high volume. This is given by Rust zero-cost abstractions, that gives us an
efficiency only comparable to C/C++.

And secondly, we decided to make the software 100% extensible: All rules are centered in a
*rules.json* file, and each company or tester could create its own rules to analyze what they need.
It's also modular, so that new developments can easily add new functionality. Finally, a templating
system for results reports (that will be improved in future updates) gives users the ability to
personalize the report.

Only with this first release, still not being stable, SUPER has shown to be much faster than other
frameworks, while catching more potential vulnerabilities. Moreover, SUPER gives some *good
practice* advices to enable programmers to select better their development practices.

It also gives great code review tools, directly in the HTML report, so that anyone can search
through the generated code with syntax highlighting for even better vulnerability analysis.

## Installation

There are multiple ways of installing SUPER in your computer. SUPER is available in
*[crates.io](https://crates.io/)*, so if you are using Rust/Cargo it's as simple as running
`cargo install super`. If not, you can select one of the following options:

### Windows

TODO (Bruno)

### Linux

We have made it really easy to install SUPER in Linux. We have many packages for different
distributions so you will be able to probably find yours. If that's not the case, you can use a
package similar to your distribution (CentOS package for RedHat based distributions, Debian/Ubuntu
packages for Debian based distributions, etc.) or if you prefer (or don't find an appropriate
package), you can compile it from source, as it's shown in the last section of the installation.

 - [Debian 8.6](https://github.com/SUPERAndroidAnalyzer/super/archive/super-0.1.0-debian.deb) (DEB)
 - [Ubuntu 16.04](https://github.com/SUPERAndroidAnalyzer/super/archive/super-0.1.0-ubuntu.deb) (DEB)
 - [Linux Mint 18](https://github.com/SUPERAndroidAnalyzer/super/archive/super-0.1.0-mint.deb) (DEB)
 - [CentOS 7](https://github.com/SUPERAndroidAnalyzer/super/archive/super-0.1.0-centos.rpm) (RPM)
 - [Fedora 24](https://github.com/SUPERAndroidAnalyzer/super/archive/super-0.1.0-fedora.rpm) (RPM)

### MacOS X

For now, MacOS users will need to build the package from source. We already have an issue
([#18](https://github.com/SUPERAndroidAnalyzer/super/issues/18)) to create packages for it, though,
and should be solved by SUPER 0.2.0.

### Compiling from source

In the case that you want or need to compile SUPER from its sources, you will need to download
those sources first. You can download SUPER 0.1.0 sources in
[zip](https://github.com/SUPERAndroidAnalyzer/super/archive/0.1.0.zip) or in
[tar.gz](https://github.com/SUPERAndroidAnalyzer/super/archive/0.1.0.tar.gz). You can also clone the *Git* repository by running:

```
git clone https://github.com/SUPERAndroidAnalyzer/super.git
```

Once you clone or download+decompress the source code in a folder and move to it, you will need to
compile it. This is really easy to do, but you will need Rust/Cargo to be installed in your system.
You can install it with the instructions provided in [rustup.rs](https://rustup.rs/). Once
installed, compiling SUPER is as simple as running the following:

```
cargo build --release
```

This will create `target/release/super`, which will be the executable that you will be able to use
in the following steps.

## Use

Use, TODO.

## Our results

Results, TODO.

## Development

Development TODO.

### Things to do

TODO, TODO.

## Team

Team, TODO.

You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
