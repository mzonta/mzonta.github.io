---
layout: post
title: "My site with Jekyll and Github - Part 3"
subtitle: "How it was deployed"
date: 2016-01-13
update:
author:
categories: jekyll github
---

Now is time to talk about how I have deployed the site.

As indicated in [Jekyll][jekyll-site] a good solution are [GitHub Pages][github-pages], even if there are other solutions as indicated in
[Jekyll documentation][jekyll-deploy-methods]: just because the static nature of the pages, it's enough to have a simple hosting service and copy the content
of the folder *_site*, that is generated locally by Jekyll.

Jekyll is the language that power the pages and the hosting is free.

## GitHub Pages

Following the instructions in [GitHub Pages][github-pages] it's created the repository for the site.

And as indicated, we can use the power of *git* to update our pages from remote.

When you create your repository, automatically GitHub remember you to create some files that should be always present.

And give you also the command to use to *push* the files from your local repository to your *GitHub Page*.

## Setting a custom domain name

So I registered my personal domain *[massimilianozonta.com][my-domain]* with a *DNS* service.

After the registration, I had to wait some hours and reply some mails before the service was available.

As indicated in the article *[Setting a Custom domain with GitHub Pages][github-custom-domain]* I did the following steps:

* Created a CNAME file with just the domain
{% highlight bash %}
www.massimilianozonta.com
{% endhighlight %}

As soon as I *commited* the CNAME file in GitHub Page I received an email that confirm the connection with my domain was done but with a warning about
the presence of a *Record A*, that is not the best solution for them.

At this point when I tried to browse *mzonta.github.io* i got the *www.massimilianzonta.com*.

To see the content of GitHub Page I had to proceed with the configuration of the DNS Service.

* Setup the custom subdomain in my DNS provider
This depend which provider you have choose.

In my case I went into the DNS panel manager

  * First removed the *www* Record A
  * Then added a new Record CNAME with
    * Host = www
    * CName = username.github.io (mzonta.github.io for my site)

Then I had to wait some time (could be around one hour) before the conection was completed.

## Resources & Credits

* [Jekyll][jekyll-site]

  [jekyll-site]:http://jekyllrb.com/

  [Jekyll Deployment Methods][jekyll-deploy-methods]

  [jekyll-deploy-methods]: http://jekyllrb.com/docs/deployment-methods/

* [GitHub][github-site]

  [github-site]: https://github.com/

  [Github Pages][github-pages]

  [github-pages]:https://pages.github.com/

  [Setting a custom domain name with GitHub Pages][github-custom-domain]

  [github-custom-domain]: https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages/

  [My Site on GitHub-Pages][my-site-gh]

  [my-site-gh]:https://github.com/mzonta/mzonta.github.io.git

* [www.massimilianozonta.com][my-domain]

  [my-domain]: http://www.massimilianozonta.com
