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

To use SUPER you will need to configure in the `config.toml` file the paths of `vendor`,
`downloads` and other folders. If the package was installed using one of the provided packages,
the default configuration will work. If not, probably the same folder where `super` is called from
will work (usually the installation folder, or the current workspace). If willing to use other
paths, a sample configuration file can be found in the `config.toml.sample` file.

Lots of parameters can be configured in that file, such as the threads that will be used for the
analysis or the rule file. We currently require some Java dependencies that are included in the
packages. This should change once [#22](https://github.com/SUPERAndroidAnalyzer/super/issues/22) is
implemented.

Once configured, the use is simple: Move the *.apk* file that you want to test to the `downloads`
folder. The name of the *.apk* file should be `{package_name}.apk`. For example:
`com.instagram.android.apk`. After that, running SUPER is as easy as running this:

```
super {package_name}
```

If SUPER is installed in the current directory, in Unix, you will need to run `./super` instead.
The package name will be the *.apk* file name without the extension. So in the example above, the
command would be this:

```
super com.instagram.android
```

This will decompress all the files in the `dist/{package_name}` folder, analyze them with the rules
in the `rules.json` file (and configuration in the `config.toml` file) and generate the results in
the `results/{package_name}` folder.

In the results page, an `index.html` file will contain the report, while a `report.json` file will
have a machine readable format of that report. In the case of using the *verbose* mode (see below),
the report will also be shown in the terminal.

### Command line interface

If you run `super --help`, you will see the following:

```
SUPER Android Analyzer 0.1.0
SUPER Android Analyzer Team <contact@superanalyzer.rocks>
Audits Android apps for vulnerabilities

USAGE:
    super [FLAGS] <package>

FLAGS:
        --bench      Show benchmarks for the analysis.
        --force      If you'd like to force the auditor to do everything from the beginning.
    -h, --help       Prints help information
    -q, --quiet      If you'd like a zen auditor that won't talk unless it's 100% necessary.
    -V, --version    Prints version information
    -v, --verbose    If you'd like the auditor to talk more than necessary.

ARGS:
    <package>    The package string of the application to test.
```

The usage is really straightforward. The `-v` or `--verbose` option will show loads of information
in the terminal itself, and the analysis will be performed much slower. The intention in verbose
mode is partially to show how the vulnerabilities are cached and how the analysis is performed.

In normal mode, small messages will be printed indicating the analysis stage. The analysis is
usually really fast (takes a really big app less than one minute in a Carbon X1), but it will in
any case show some prints. This can be avoided by using the `-q` or the `--quiet` option. This will
avoid **all** output from *stdout* even though there might be some output in *stderr* if something
doesn't go as expected.

The `--force` option will regenerate the distribution files and results even if that application
has already been analyzed. By default, if the application distribution files exist in
`dist/{package_name}` they won't be generated, and if the results are already in
`results/{package_name}` they won't be generated either. Those are independent, so if the
distribution files are generated but the report has been deleted, only the report will be generated.

The `--bench` flag will generate benchmarks for the current analysis. This is useful to see the
real performance of the analysis. An example benchmark can be this:

```
Benchmarks:
ApkTool decompression: 7.278750647s
Dex extraction: 0.98327826s
Dex to Jar decompilation: 11.473415714s
Decompilation: 11.695567790s
Manifest analysis: 0.5059071s
Certificate analysis: 0.5984248s
Rule loading: 0.15836818s
File analysis: 1.312931838s
Total code analysis: 1.349633866s
Total static analysis: 1.362122448s
Report generation: 1.154849626s
Total time: 33.824436350s
```

As you can see, most of the time is expent in the extraction and decompilation phases, which are
one of the priorities for the next version
([#22](https://github.com/SUPERAndroidAnalyzer/super/issues/22)), since they use external Java
dependencies.

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
