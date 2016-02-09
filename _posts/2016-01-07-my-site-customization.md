---
layout: post
title: "My site with Jekyll and Github - Part 2"
subtitle: "How it was customized"
date: 2016-01-07
update:
author:
categories: jekyll boostrap
---

In the previous [post](2016-01-06-my-site-jekyll-github.html) I have introduced the steps I followed to install Jekyll.

Now I will talk about its customization.

I could start forking other project with more job done and more options, but I prefered to start from less and build step by step in order to understand
a little of what I was doing.

So, the job is not perfect, and for sure an expert in web design could do a better job.

## Liquid & YAML

Jekyll support Liquid language and YAML tags (that can be a value or a piece of code) that let you to create templates.

With all the advantage of templates, that is, you save time when you need to make some changes because you do in one place.

About variable, just note that they can be *local*, define inside the *page*, or global for all the *site*; these last are defined in the *_config.yml* file.

We could say that *_config.yml* become the interface for the theme.

**Note**. If you change something in *_config.yml* you have to restart *jekyll serve* and refresh the browser page to see the result.

## Bootstrap

The first step was the integration of *[Bootstrap CSS][bootstrap-site]*.

### Installation

For Jekyll must be used the Sass port of Bootstrap.

I have cloned the current version of Bootstrap-Sass from the GitHub.

{% highlight bash %}
$ git clone https://github.com/twbs/bootstrap-sass.git
{% endhighlight %}

Then

* copied the file *bootstrap-sass/assets/stylesheets/_bootstrap.scss* in the folder *_sass* of the Jekyll project folder
(this file is the header file that include all the calls at the files in *bootstrap* folder)
* copied the folder *bootstrap-sass/assets/stylesheets/bootstrap* in the folder *_sass* of the Jekyll project folder
* copied the folder *bootstrap-sass/assets/fonts* in the Jekyll project folder (this is for glyphicons, even if I have not yet used)
* copied the folder *bootstrap-sass/assets/javascript* and rename *js* in the Jekyll project folder

In some posts I found that is good to avoid to change the Bootstrap files to create your personal theme, but instead add new ones.
Then I have added in *_sass* other two files

* site-variables.scss - to customized some Bootstrap variables defined in *_sass/bootstrap/_variables.scss*
* site-style.scss - to customized the styles (not only of Bootstrap but also of other styles I added from other resources)

**Note**. I'd like to point the attention about the order of the calls of variables/styles files.

In *css* folder there is the *main.scss* file created by default.

At the end can be found the *@import* calls
{% highlight scss %}
// Import partials from `sass_dir` (defaults to `_sass`)
@import
        "base",
        "layout",
        "syntax-highlighting"
;
{% endhighlight %}

I added the two new files in the order shown here below

{% highlight scss %}
// Import partials from `sass_dir` (defaults to `_sass`)
@import "base",
        "layout",
        "syntax-highlighting",
        "site-variables",
        "bootstrap",
        "site-style"
;
{% endhighlight %}

In particular *site-variables* before *bootstrap* and *site-style* after *bootstrap*.

This is because the variable are defined one time, and a second definition is ignored,
while the style can be change after.

## Landing Page and Navigation Menu

For those parts I had a look at the [Landing Page Jekyll Theme][landing-page-jekyll] based on the
[Landing Page Bootstrap Theme][landing-page-bootstrap].

## Font Awesome

In the same themes it is shown how to use the *Font Awesome*.

* Download fonts from [Font Awesome][font-awesome-site] (actually the version 4.5.0)
* Unzip and copied the folder *font-awesome-4.5.0* into the Jekyll project folder

To be able to use in the pages I added the following command in the *_include/head.html* file where I collect all the custom fonts definition.
(You can see also the link at the Google Fonts, in my case Lato).

{% highlight html %}
<!-- Custom Fonts -->
<link href="font-awesome-4.5.0/css/font-awesome.min.css" rel="stylesheet" type="text/css">
<link href='http://fonts.googleapis.com/css?family=Lato' rel='stylesheet' type='text/css'>
{% endhighlight %}

To see how to use the Fonts, have a look at the [Examples page][font-awesome-examples] of Font Awesome.

## Contact: Form

Another thing in [Contact page](contact.html) is the form.

With Jekyll, that is a static site generator, must be used an external back-end service to send data.

I have decided for [Formspree][formspree-site] because it's not necessary create an account.

Here below the code snippet from Formspree:

{% highlight html%}
<form action="//formspree.io/your@email.com"
      method="POST">
    <input type="text" name="name">
    <input type="email" name="_replyto">
    <input type="submit" value="Send">
</form>
{% endhighlight %}

To activate the service you have to use the form one time.

You receive an email to confirm the address and that's all.

## Others

In general I took some ideas and code from the [blog of Joel Glovier][joel-glovier], the author of [Jekyll New Theme][jekyll-new-theme].

About *hr style* at the end of posts I found something at [CSS-TRICKS][css-tricks-hr]


## Resources & Credits

* Jekyll

  [Jekyll New theme][jekyll-new-theme] by [Joel Glovier][joel-glovier]

  [jekyll-new-theme]:https://github.com/jglovier/jekyll-new

  [joel-glovier]: http://joelglovier.com/

  [Landing Page Jekyll Theme][landing-page-jekyll]

  [landing-page-jekyll]: https://github.com/swcool/landing-page-theme

* [Bootstrap][bootstrap-site]

  [bootstrap-site]:http://getbootstrap.com/

  [Landing Page Bootstrap Theme][landing-page-bootstrap]

  [landing-page-bootstrap]: https://github.com/BlackrockDigital/startbootstrap-landing-page

* [Font Awesome][font-awesome-site]

  [font-awesome-site]: http://fontawesome.io/

  [Font Awsome - Examples][font-awesome-examples]

  [font-awesome-examples]: http://fontawesome.io/examples/

* [CSS-TRICKS][css-tricks]

  [css-tricks]: https://css-tricks.com/

  [CSS-TRICKS Simple style for <hr> ][css-tricks-hr]

  [css-tricks-hr]: https://css-tricks.com/examples/hrs/

* Form

  [Formspree][formspree-site]

  [formspree-site]: https://formspree.io/

* GitHub

  [My Site on GitHub-Pages][my-site-gh]

  [my-site-gh]:https://github.com/mzonta/mzonta.github.io.git
