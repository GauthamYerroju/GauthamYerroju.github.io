---
date: 2017-03-30 15:02:21-07:30
last_modified_at: 'Sun Apr 09 2017 17:02:00 GMT-0700 (PDT)'
title: New website
published: true
categories:
  - Web Development
tags:
  - blog
  - jekyll
  - website
  - workflow
  - prose.io
---
You are here, which means you are on my new site. __Welcome!__

I have been meaning to migrate my blog from Wordpress for so long, the landscape for static site generators has matured to the point of enjoyable usability (with some magic sauce). Finally, I made my decisions after much thought on how I wanted to implement my site, and on a sustainable workflow. If you are interested on how I ended up with this website, read on.

## Some history

While I had abandoned writing on my old blog, I have been considering creating a new one for years (literally). In the meanwhile, my jobs at FactSet and CA Technologies gave me a chance to learn a lot about web technologies, among other things. So for my personal website, I wanted to build it by hand.

Being an obsessive perfectionist combined with having a low attention span for long personal projects kept me from actually finishing the new site. For a while, I fiddled with creating a [portfolio website](http://gauthamyerroju.com/personal-site/) but that didn't go as far as I planned either. A good project came about from that effort though, a minimal slider menu I wrote in CSS called [Slidey](http://gauthamyerroju.com/Slidey/).

## Static Site Generators

In the recent years, I have taken an interest in [static site generators](https://davidwalsh.name/introduction-static-site-generators). In a nutshell, <abbr title="Static Site Generator">SSG</abbr> combine content (typically written in Markdown) and a template (HTML, CSS and JS) into a completely static website (just HTML, CSS and JS). This is unlike blogging platforms like Wordpress or Blogger, or <abbr title="Content Management System">CMS</abbr>s like Drupal which rely on server-side functionality to dynamically generate web pages we visit.

The appeal for SSGs is obvious:
- We get very light-weight websites which load almost instantaneously (assuming we don't go crazy with a bunch of AJAX calls and dynamic widgets all over the place)
- We can deploy these sites practically on any web server, even on something like a self-hosted Raspberry Pi (as these sites are just files with no server side functionality).

There are a few catches though (aren't there always?):

1. We need to generate the website each time we add or remove content. This "generation" needs to happen somewhere, typically on the author's computer. This requires setting up the necessary environment, and we need that computer to publish changes.
2. Performance of site generation is affected as site grows. When there are a 1000 articles in markdown which need to be compiled into HTML, SSGs, depending on how they are implemented, SSGs can take anywhere from a few seconds to minutes (even with obvious optimizations like generting only changes or updating content).
3. Authoring is a pain. Granted, there are many good options to author Markdown, but I feel it is just cluncky having to manage properties and metadata (like tags, categories, etc.) in Markdown by hand. It would be nice to have an "admin panel" similar to what Wordpress offers.

For me, 1 and 2 are not really a problem. SSGs like [Hugo](https://gohugo.io/) and [Hexo](https://hexo.io/) do a pretty good job on performance. Besides, for personal blogs (like mine), even SSGs which don't really focus on performance (like the popular Jekyll) will work just fine.

Addressing 3, are SSG-focussed hosting services, like [Ghost.io](https://ghost.org/), which take the pain of compiling websites and authoring configuration in markdown away, and keeping your content and workflow completely in the cloud. In addition, services like these usually have "admin panels" with good integration with SSGs, which makes the whole experience of authoring much more seamless.

Considering everything about SSGs, the appeal of a static blog is just too alluring for me to fall back to Wordpress. I was almost going to go with Ghost.io but I like the whole DIY aspect of SSGs and I was curious to see how far I could go while sticking to freely available options.

I initially chose [Hexo](https://hexo.io/) as my SSG, because of my love (well, love/hate, really) for NodeJS. Hexo is built on NodeJS and emphasizes speed using parallelization (using Node's on-blocking IO capabilities). But I eventually decided to use Jekyll, because of hosting.

## Hosting options

Like I said, any web server which can serve files will do, which means many free and cheap hosting options become viable. We just need to decide where to host the files.

An increasingly popular options these days, especially among developers of any kind, is [GitHub Pages](https://pages.github.com/).

### GitHub Pages

Essentially, GitHub allows us to host any repo as a static website. This is great for projects, which can host their websites along with the source code, but it is also great for blogs, due to GitHub Pages' [Jekyll support](https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/).

GitHub Pages's Jekyll support means that we don't have to compile our blog. If we decide to use Jekyll for our SSG, GitHub will take care of compiling the website automatically. Want to write  post? Create a new Markdown file, type away, and commit the file. The change will be reflected on your website as soon as GitHub automatically compiles the site (which is usually seconds to minutes). We can even do this right in the browser using GitHub's excellent editor.

I was already using [Hostinger](https://www.hostinger.com/) to host my old website, but recently they decided to remove their free tier. That's fine, except they axed my website without so much as an email notifying free users of the change. Ugh.

Though I wanted to use Hexo, my search for a new webhost lead me to GitHub Pages which supports Jekyll instead. At this point, my novelty with dealing with SSGs directly faded away, and I was loathe to having to rely on my laltop for publishing my website. Since GitHub was already offering Jekyll, I thought "why not!"

## Workflow

Using SSGs, it is easy enough to build simple workflows. Once we setup the environment and configure a few things, publishing is as easy as running something like:
```shell
$ hexo publish [layout] <filename>
```
in [Hexo](https://hexo.io/), for example. This is beside the point though, as I decided to use GitHub Pages anyway.

As I said before, authoring a new post in a GitHub Pages-hosted Jekyll blog is pretty easy. But I still wanted an Admin panel instead of dealing with Markdown for metadata. Enter Prose.io.

### Prose.io

[Prose.io](http://prose.io/#about) provides "a beautifully simple content authoring environment for CMS-free websites". It seamlessly integrates with a GitHub account and provides a beautiful and functional web-UI for editing content. As a bonus, it also has "advanced support for Jekyll sites and markdown content". Sounds perfect, right? This is exactly what I needed!

Prose.io has out-of-the-box support for Jekyll sites _and_ GitHub pages, but it goes one step further:__it allows us to customize the editor__. For example, there are many Jekyll themes with fancy options like header images, featured posts and what not. Prose allows us to define a configuration for any metadata, which will show up as UI widgets in the editor. For example, adding the following to the _config.yml file:
{% highlight yml linenos %}
prose:
  metadata:
    _posts:
      - name: "tags"
        field:
          element: "multiselect"
          label: "Add Tags"
          placeholder: "Choose Tags"
          options:
            - name: "Apples"
              value: "apples"
            - name: "Bananas"
              value: "bananas"
{% endhighlight %}
adds a multiselect widget for adding tags to our post.

## A match made in Heaven

After deliberating over which SSG to use, after many hours of experimenting with  Hexo, fiddling away with Gulp scripts, considering building my own admin panel (which could still be a project for another day), I finally found my secret sause: __GitHub Pages + Prose.io__

And I decided to go with it.

I took a day to port my markdown files from Hexo to Jekyll (updating the metadata) and deploying a Jekyll site on GitHub Pages, and here I am!

## What's next

I ditched dealing with an SSG, but I still want to build my own theme, as a way to showcase everything I learned about web design over the years. So I picked a minimal theme (in looks as well as functionality)  called [Monochrome](https://github.com/dyutibarma/monochrome). It's perfect because it doesn't do too much styling, it is easy for me to re-implement anything I want to change, and to extend as I see fit (I already made some tweaks as you can notice if you look at the original Monochrome theme).

It does not have Prose.io configuration though, and that is at the top of my TODO list for this website (arpart from writing content, of course!). Prose.io provides a [pretty straight-forward guide](https://github.com/prose/prose/wiki/Getting-Started) on how to get started.

That's all for now. Peace!
