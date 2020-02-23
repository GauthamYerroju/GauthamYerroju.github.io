---
date: '2020-02-23 12:53 -0800'
last_modified_at: '2020-02-23 12:53 -0800'
published: true
title: On choosing front-end web frameworks
categories:
  - Web Development
tags:
  - web development
  - front-end
  - frameworks
  - opinion
---
When I was a kid, web development just meant knowing HTML, CSS, and some JS. Oh how far we're come.

A decade or two ago, it used to be the wild west of implementations of HTML, CSS and JS by different web browsers. As the web began to proliferate, common patterns began to emerge and common pain points began to surface. The community converged towards best practices, which eventually made their way into web standards. These were solidified with popular browsers adopting them. Unfortunately, default browsers (IE and Safari) were the last to hop on the bandwagon, but they eventually got wise.

Web development has now grown really complex, leading to the age of web applications: full-blown applications with high complexity and performance/responsiveness requirements, which happen to run in browsers. As people started to build these, common patterns began to emerge again, converging into a few design philosophies, which manifested into some frameworks.

On the front-end JS side, we have React, Vue and Angular. I think we're at a good place with these, where there isn't too much fragmentation of opinions on how to build large-scale front-end apps. But I admit I haven't had enough time with them to really dive deep, because I'm sure there are plenty of differences of opinions between these frameworks.

On the css side, we have practically 1000s of component frameworks (think Bootstrap back in the day, now many many more). The main problem with these is that they're too opinionated: people often find themselves fighting/overriding the styles of these component frameworks. So a new class of CSS frameworks started to emerge (think Tachyon.io and Tailwind CSS) which are essentially a combination of a consistent design language and some super-basic sub-atomic utility classes which can be combined to build components. I think this is great, because it gives us flexibility with the components themselves, while sticking to a consistent design language. The downside is, if a component is a combination of multiple CSS classes, it'll be tedious to define them in HTML. Fortunately, tooling and CSS compilers have also come a long way and make this less of an issue. CSS pre-compilers like Sass dominate this area. However personally, I prefer to just stick to plain old CSS, as that keeps me on my toes and allows me to consider selector performance.

How would I pick frameworks for production-grade projects? This is what I go by:

  1. Don't overthink it. We've reached a place where most reputable frameworks hold to best practices. Technically speaking, time spent on splitting hairs between popular frameworks is better invested elsewhere (unless I happen to own that framework or a competing framework).
  2. Pick something that is widely adopted (by reputable companies, or by a huge community), well-documented, and actively developed (specifically, it doesn't have to change too often, but bug and security fixes should be released actively). The main idea is that the more a framework is adopted by competent people, the more shortcomings, workarounds, best practices, etc are revealed, and this informs development of future versions.
  3. Resist the urge to jump to the next shiny framework leveraging a new clever trick. In production, a proven track record is more important than a possible 5% performance improvement in some specific cases.

When do I switch to a different framework?

  - Licencing model of current framework changes and is no longer viable
  - A different framework would significantly reduce onboarding, maintenance or scaling cost
  - A different framework would significantly increase performance (but remember the golden rule with performance optimization: measure where you have a problem and only fix that. Premature optimization is the root of all evil).
  - I'm already on a legacy framework and it's getting increasingly difficult to hire people to work on it (think old verions of J2EE, PHP, Wordpress, etc)

That being said, my priorities for personal projects are different. The landscape of front-end development is, afterall, fast-cahnging and pretty exciting, and it's awesome to try out that one new experimental framework or tool to see if it tickles my fancy. With personal projects, I tend to go all over the place, using a different CSS/server-side/front-end framework for each new project. This allows me to stay on top of new developments and gives me a safe space to look into and evaluate new tools to see if they're production-worthy.

Thanks for reading!
