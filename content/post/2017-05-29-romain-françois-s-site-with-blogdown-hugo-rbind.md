---
title: Romain François’s site with blogdown,hugo,rbind
author: Romain François
date: '2017-05-29'
slug: romain-françois-s-site-with-blogdown-hugo-rbind
categories: 
 - Hugo
 - blogdown
description: Some details about how Romain converted his website to blogdown
---

I have used many platforms for blogging over the years (dotclear, wordpress, ghost)
and none of them really made me happy about their workflow. I even lost some 
content that lived in some server I failed to renew despite the many warnings
about upcoming deletion. I managed to pull back some content from the 
[web archive](https://archive.org/web/) and other places using various `rvest` foo. 

I've now moved to the awesome combo `hugo/blogdown/github/netlify`. My source content 
lives in [a github repo](https://github.com/rbind/romain) in the `rbind` 
organisation, I can write it as markdown or R markdown thanks to `blogdown` and 
the nice support for it in future versions of RStudio. The code is then converted
to a full static website with [hugo](https://gohugo.io) and continuously deployed
on [netlify](https://www.netlify.com). The [blogdown book](https://bookdown.org/yihui/blogdown/)
explains it in great detail. 

I've used the [hugo-universal-theme](https://themes.gohugo.io/hugo-universal-theme/)
as a basis but I've already started to tweak it for my use. It may not be obvious to 
understand how [hugo](https://gohugo.io) works at first, but the documentation is well
written and it is definitely worth it to learn about it. It is still a bit early for 
me to write some guide about how I modified the theme, as I probably will keep
modifying it. 

I spent most of my time tweaking the theme and exhuming old content from various sources, 
but I've already written 5 new posts to get familiar with the workflow. 

 - [Trump: a package to segfault your R session](https://romain.rbind.io/blog/2016/11/16/trump-a-package-to-segfault-your-r-session/) 
 about one my insane weekend project of a package that corrupts your session as soon as you 
 load it. 
 - [R and C++ in Milano](https://romain.rbind.io/blog/2017/04/05/r-and-c-plus-plus-in-milano/)
 about a talk I gave at the [MilanoR meetup](http://www.milanor.net)
 - [Calling go from R](https://romain.rbind.io/blog/2017/05/14/calling-go-from-r/). I'm currently learning `go` so I expect to be blogging about this a lot more, not a coincidence that hugo is written in `go`. 
 - [Colorful Output in R Console](https://romain.rbind.io/blog/2017/05/27/colorful-output-in-r-console/)
 for when I discover on twitter about support for color in the Rstudio console. 
 - [Turn R users insane with evil](https://romain.rbind.io/blog/2017/05/28/turn-r-users-insane-with-evil/)
 about my latest weekend project that aims at bringing insanity to R users. 

Having written these posts was a delight with this workflow. I will definitely want to blog again, and 
I can only encourage other members of the community to try `blogdown`. If you are anything like me, you'll 
fall in love with it. 

See you soon on [romain.rbind.io](http://romain.rbind.io). 
