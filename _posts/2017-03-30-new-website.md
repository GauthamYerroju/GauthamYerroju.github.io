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

I have been meaning to migrate my blog from Wordpress for so long, the world has seen the rise of a new blogging platform, static site generators. After much thought on a sustainable workflow and how I wanted to implement my site, I finally made my decision. If you are interested on how I ended up with this website, read on.

## Some history

While I had abandoned writing on my old blog, I have been considering creating a new one for many years (no kidding). In the meanwhile, my jobs at FactSet and CA Technologies gave me a chance to learn a lot about web technologies, among other things. For my personal website, I wanted to build it by hand.

Being an obsessive perfectionist combined with having a low attention span for long personal projects kept me from actually finishing a new site. For a while, I fiddled with creating a [portfolio website](http://gauthamyerroju.com/personal-site/) but that didn't go as far as I planned either. A good project came about from that effort though, a minimal slider menu I wrote in CSS called [Slidey](http://gauthamyerroju.com/Slidey/).

## Static Site Generators

In the recent years, I have taken an interest in [static site generators](https://davidwalsh.name/introduction-static-site-generators). In a nutshell, an <abbr title="Static Site Generator">SSG</abbr> combines content (typically written in Markdown) and a template (HTML, CSS and JS) into a completely static website (just HTML, CSS and JS). This is unlike blogging platforms like Wordpress or Blogger, or <abbr title="Content Management System">CMS</abbr>s like Drupal which rely on server-side functionality to dynamically generate web pages.

The appeal for SSGs is obvious:

1. We get very light-weight websites which load almost instantaneously, assuming we don't go crazy with a bunch of AJAX calls and dynamic widgets.
2. We can deploy these sites practically on any web server, even on something like a self-hosted Raspberry Pi (as these sites are just files with no server side functionality).

There are a few catches though (aren't there always?):

1. We need to generate the website each time we add or remove content. This "generation" needs to happen somewhere, typically on the author's computer. This requires setting up the necessary environment, and we need that computer to publish changes.
2. Performance of site generation is affected as site grows. When there are a 1000 articles in markdown which need to be compiled into HTML, SSGs can take anywhere from a few seconds to minutes (even with obvious optimizations like generating only changes or updating content).
3. Authoring is a pain. Granted, there are many good options to author Markdown, but I feel it is just clunky having to manage properties and metadata (like tags, categories, etc.) in Markdown by hand. It would be nice to have an "admin panel" similar to what Wordpress offers.

For me, 1 and 2 are not really a problem. SSGs like [Hugo](https://gohugo.io/) and [Hexo](https://hexo.io/) do a pretty good job on performance. Besides, for personal blogs (like mine), even SSGs which don't focus on performance will work just fine.

Addressing 3, are SSG-focussed hosting services, like [Ghost.io](https://ghost.org/), which take away the pain of compiling websites and authoring configuration in markdown. These services a;sp keep the content and workflow completely in the cloud. In addition, services like these usually have "admin panels" with good integration with SSGs, which makes the whole experience of authoring much more seamless.

Considering everything about SSGs, the appeal of a static blog is just too alluring for me to fall back to Wordpress. I was almost going to go with Ghost.io but I like the whole DIY aspect of SSGs and I was curious to see how far I could go while sticking to freely available options.

I initially chose [Hexo](https://hexo.io/) because of my love (well, love/hate, really) for NodeJS. Hexo is built on NodeJS and emphasizes speed using parallelization (using Node's non-blocking IO capabilities). But I eventually decided to use Jekyll, because of hosting.

## Hosting options

Like I said, any web server which can serve files will do, which means many free and cheap hosting options become viable. I just needed to decide where to host my files.

An increasingly popular options these days, especially among developers of any kind, is [GitHub Pages](https://pages.github.com/).

### GitHub Pages

Essentially, GitHub allows us to host any repo as a static website under the service it calls __GitHub Pages__. This is great for projects, which can host their websites along with the source code, but it is also great for blogs due to GitHub Pages' [Jekyll support](https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/).

GitHub Pages's Jekyll support means that one does not have to compile the blog. We just check-in the content to a GitHub repo and GitHub will take care of compiling the website automatically. Want to start a new post? Create a new Markdown file, type away, and commit the file. The change will be reflected on the website as soon as GitHub automatically compiles the site (which is usually seconds to minutes). This can even be done right in the browser using GitHub's excellent markdown editor.

I was already using [Hostinger](https://www.hostinger.com/) to host my old website, but recently they decided to remove their free tier. That's fine, except they axed my website without so much as an email notifying free users of the change. Ugh.

Though I wanted to use Hexo, my search for a new host lead me to GitHub Pages which supports Jekyll instead. At this point, my novelty with tweaking SSGs faded away, and I was loathe to having to rely on my laptop for publishing my website. Since GitHub was already offering Jekyll, I thought why not!

## Workflow

Using SSGs, it is easy enough to build simple workflows. Once we setup the environment and configure a few things, publishing is as easy as running something like:
```shell
$ hexo publish [layout] <filename>
```
in [Hexo](https://hexo.io/), for example. This is beside the point though, as I decided to use GitHub Pages anyway.

As I said before, authoring a new post in a GitHub Pages-hosted Jekyll blog is pretty easy. But I still wanted an Admin panel instead of dealing with Markdown for metadata. Enter Prose.io.

### Prose.io

[Prose.io](http://prose.io/#about) provides, to quote from their website, "a beautifully simple content authoring environment for CMS-free websites". It seamlessly integrates with a GitHub account and provides a beautiful and functional web-UI for editing content. As a bonus, it also has "advanced support for Jekyll sites and markdown content". Sounds perfect, right?

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

After deliberating over which SSG to use, after many hours of experimenting with Hexo, fiddling away with Gulp scripts, considering building my own admin panel (which could still be a project for another day), I finally found my secret sauce: __GitHub Pages + Prose.io__

And I decided to go with it.

I took a day to port my markdown files from Hexo to Jekyll (updating the metadata) and deploy a Jekyll site on GitHub Pages, and here I am!

## The pitfall with Prose.io

As always, there's always a catch. It turns out that Prose.io's markdown editor does not support spell check. I didn't realize it until I found a bunch of typos in this very blog post after I published it. After a bit of digging, I found that Prose.io does not support spell check, and there are reasonable reasons for that. There are a few issues in the Prose.io repo on GitHub with discussions on this particular problem. It's not a deal breaker but I am a bit disappointed.

## What's next

I ditched dealing with an SSG, but I still want to build my own theme, as a way to showcase everything I learned about web design over the years. So I picked a minimal theme (in looks as well as functionality) called [Monochrome](https://github.com/dyutibarma/monochrome). It's perfect because it doesn't do too much styling, it is easy for me to re-implement anything I want to change, and to extend as I see fit (I already made some tweaks as you can notice if you comparing my website with the original Monochrome theme). Although, I always wanted to build a complete theme, and one of my future projects is going to be replacing the monochrome as a base for my current theme and roll my own.

Next, the Monochrome theme does not have a Prose.io configuration. So of course I built one ([look here](https://github.com/GauthamYerroju/gauthamyerroju.github.io/blob/master/_config.yml)). It was easy enough, Prose.io provides a [pretty straight-forward guide](https://github.com/prose/prose/wiki/Getting-Started) on how to get started.

Finally, I need spell check! I am still trying to find a way to get that on to Prose.io. My first thought is to inject a client-side spell-check library using Tampermonkey/Greasemonkey.

That's all for now. Peace!
