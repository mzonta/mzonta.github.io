---
layout: post
title: "My site with Jekyll and Github - Part 1"
subtitle: "How I get up and running"
date: 2016-01-06
update:
author:
categories: jekyll github
---

In the past years often I thought about the idea to build a personal site/blog where write about my professional interests.
And it was not easy to decide which kind of tool use.
Among the several and widely used CMS, I was almost sure WordPress should be the right choice for me because I'm not a web developer.
But at the end, I changed for Jekyll. And with the new year 2016 I start to work with it, and this is the result.

### Wordpress
As I wrote it was my first choice.
And I used it to make some experiments with my first LAMP server based on Ubuntu Server 14.04LTS.

### Jekyll & GitHub
But when I decided to go on-line, while I was surfing the net, just to make a second check on the options, I found [Jekyll][jekyll-site].
And, at least for now, it looks the right choice for me.
Beside the advantages of going static,
it can be installed locally and hosted for free on [Github Pages][github-pages].
Overall the possibility to develop locally, without the needs of an internet connection, test the modification using the local jekyll server
and when ready push the update.
As well as create new branches to test new functionality or clone completely and develop new site.
Also for Jekyll there is a lot of documentation.
Below I write about what I did to prepare my Jekyll environment.

## Jekyll: Installation
I am using a PC where I have a VMware VM with Ubuntu 14.04 LTS as OS.

I followed the installation instruction I found on [Jekyll][jekyll-installation] and [GitHub][github-jekyll]

### Ruby

* Prerequisites

Update apt-get:

{% highlight bash %}
$ sudo apt-get update
{% endhighlight %}

Installation of dependencies:

{% highlight bash %}
$ sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev
{% endhighlight %}

* Installation of *rbenv*

{% highlight bash %}
git clone git://github.com/sstephenson/rbenv.git .rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bash_profile

git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
source ~/.bash_profile
{% endhighlight %}

Before to proceed, restart the PC or just log out and log in again.

* Installation of *Ruby*

At the [Ruby Download page][ruby-download] can be seen which is the current stable version.
At the time it was written the post is 2.3.0.

{% highlight bash %}
$ rbenv install -v 2.3.0
$ rbenv global
{% endhighlight %}

When finished, installation can be checked with the command

{% highlight bash %}
$ ruby -v
{% endhighlight %}

The answer should be
{% highlight bash %}
2.3.0
{% endhighlight %}

To avoid Rubygems generates local documentation for each gem installed

{% highlight bash %}
echo "gem: --no-document" > ~/.gemrc
{% endhighlight %}

* Installation of *bundler*

{% highlight bash %}
$ gem install bundler
{% endhighlight %}

### NodeJS

Based on instruction found in [Node.js][nodejs-installation]

{% highlight bash %}
$ sudo apt-get install curl
$ curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
$ sudo apt-get install -y nodejs
{% endhighlight %}

To check the version installed

{% highlight bash %}
$ nodejs -v
{% endhighlight %}


### Python 2.7

Normally already installed.

### Jekyll

Via *RubyGems*

{% highlight bash %}
$ gem install jekyll
{% endhighlight %}

To make the installation close to GitHub Pages

{% highlight bash %}
$ gem install github-pages
{% endhighlight %}

**Note**. To keep *Jekyll* up to date on local installation, run the command

{% highlight bash %}
$ gem update github-pages
{% endhighlight %}


## Jekyll: Create a new site

Now that everything is ready we can create the first blog.

{% highlight bash %}
$ jekyll my-jekyll-site
{% endhighlight %}

The command create a folder named *my-jekyll-site* with some folders and *[Welcome to Jekyll!!](2016-01-05-welcome-to-jekyll.html)* post.
The site is based on the [jekyll-new-theme][jekyll-new-theme].


To run locally the site, goes into the folder

{% highlight bash %}
$ cd my-jekyll-site
{% endhighlight %}

run the *jekyll serve*

{% highlight bash %}
$ jekyll serve
{% endhighlight %}

and open the browser at the address [*http://localhost:4000*](http://localhost:4000) where *4000* is the default port.

If you want to use a different port or, better, run more sites then you have to define the port.
For example:

{% highlight bash %}
$ jekyll serve --port 4001
{% endhighlight %}

## Editor

With this project I began to use [Atom][atom-site].

Actually I use it also to write the posts, but I found a problem of syntax highlighting with words that begin with an underscore.

A solution suggested is to add a [Markdown Package][atom-language-markdown].
It works, even if I prefer the original color highlighting.

## Site customization. Bootstrap.

At this point I could use the blog generated automatically, but I had in my mind to do something like I did previously with WordPress and [Tyler Moore][tyler-moore] tutorial.

But this will be the subject of a next post.

## Links

* [Ruby][ruby-site]

  [ruby-site]:https://www.ruby-lang.org/

  [Ruby Download Page][ruby-download]

  [ruby-download]:https://www.ruby-lang.org/en/downloads/

  [Installation][ruby-installation]

  [ruby-installation]:https://www.digitalocean.com/community/tutorials/how-to-install-ruby-on-rails-with-rbenv-on-ubuntu-14-04

* [Node.js][nodejs-installation]

  [nodejs-installation]:https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions

* [GitHub][github-site]

  [github-site]: https://github.com/

  [Github Pages][github-pages]

  [github-pages]:https://pages.github.com/

  [My Site on GitHub-Pages][my-site-gh]

  [my-site-gh]:https://github.com/mzonta/mzonta.github.io.git

* [Jekyll][jekyll-site]

  [jekyll-site]:http://jekyllrb.com/

  [Jekyll Installation Guide][jekyll-installation]

  [jekyll-installation]:http://jekyllrb.com/docs/installation/

  [Jekyll on GitHub Pages][github-jekyll]

  [github-jekyll]:https://help.github.com/articles/using-jekyll-with-pages/#keeping-jekyll-up-to-date

  [Jekyll New theme][jekyll-new-theme] by [Joel Glovier][joel-glovier]

  [jekyll-new-theme]:https://github.com/jglovier/jekyll-new

  [joel-glovier]: http://joelglovier.com/

* [Markdown Basics][markdown-basics]

  [markdown-basics]:https://help.github.com/articles/markdown-basics/

  [kramdown][kramdown-site]

  [kramdown-site]:http://kramdown.gettalong.org/

* [Atom][atom-site]

  [atom-site]: https://atom.io/

  [Atom - Markdown support][atom-language-markdown]

  [atom-language-markdown]: https://github.com/burodepeper/language-markdown
