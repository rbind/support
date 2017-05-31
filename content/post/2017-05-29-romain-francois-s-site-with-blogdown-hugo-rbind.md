---
title: Romain’s site with blogdown, hugo, rbind
author: Romain François
date: '2017-05-29'
slug: romain-francois-s-site-with-blogdown-hugo-rbind
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

This is likely to change, but as of today, here are some of choices I've made for the theme. 
I've used the [hugo-universal-theme](https://themes.gohugo.io/hugo-universal-theme/)
as a basis but I've already started to tweak it for my use. It may not be obvious to 
understand how [hugo](https://gohugo.io) works at first, but the documentation is well
written and it is definitely worth it to learn about it. 

The landing page contains:
 
- a menu on top, driven by the `config.toml` file and the theme. 
- a picture and some words. I've tweaked the
   [`see_more.html`](https://github.com/rbind/romain/blob/master/layouts/partials/see_more.html) 
   partial template. 
![](https://cloud.githubusercontent.com/assets/2625526/26580838/236f4952-453a-11e7-88ef-7bed0da86354.png)

- Recent posts, this is handled by the template. To use this, posts should have a `banner` in the front matter, e.g. 

```
banner: "img/banners/go.png"
```

![](https://cloud.githubusercontent.com/assets/2625526/26580839/236e5bf0-453a-11e7-9c36-eb921dca266c.png)

For the [list of posts](https://romain.rbind.io/blog/), I was not happy about what the theme offered, and 
so I've taken inspiration from [@yihui](https://yihui.name) and decided to use a minimalist list of 
posts, arranged by year. 

![list](https://cloud.githubusercontent.com/assets/2625526/26581221/deb5bd58-453b-11e7-8452-b15a5712f1c1.png)

I've also stolen some code from [@yihui](https://yihui.name) for the meta information of single posts, 
in particular for link to rss feed, to tweet the post and to edit the post on github. 

![post](https://cloud.githubusercontent.com/assets/2625526/26580836/236df9c6-453a-11e7-84f0-81a90b8a44d2.png)

I've added the possibilty to include gallery of images in posts

![gallery](https://cloud.githubusercontent.com/assets/2625526/26580837/236eb956-453a-11e7-9636-8f8fc3859e3a.png)

This is based on [Gallery](https://github.com/blueimp/Gallery) (which I have imported as a 
sub module), with this on the front matter.

```
gallery: "milanoR"
```

"milanoR" refers to a directory within "static/img/gallery" of the repo. The `gallery` variable is used by 
these templates: 

- `layouts/_default/single.html` loads the javascript library and looks for an element called 
  `links` on the page. `links` will contain a set of links to images. 

```
    {{ if .Params.gallery }}
    <script src="/lib/gallery/js/blueimp-gallery.min.js"></script>

    <script>
    blueimp.Gallery(
    document.getElementById('links').getElementsByTagName('a'),{
        container: '#blueimp-gallery-carousel',
        carousel: true
    });
    </script>

    {{ end }}
```

- `layouts/partials/gallery.html` first defines a placeholder, and then loops through the 
  content of the image directory to add links. 

```
{{ if .Params.gallery }}

<div id="blueimp-gallery-carousel" class="blueimp-gallery blueimp-gallery-carousel">
    <div class="slides"></div>
    <h3 class="title"></h3>
    <a class="prev">‹</a>
    <a class="next">›</a>
    <a class="play-pause"></a>
    <ol class="indicator"></ol>
</div>

<div id="links">

  {{ $gallery := .Params.gallery }}
  {{ $sourcePath := ( printf "static/img/gallery/%s" $gallery ) }}
  {{ $files := readDir $sourcePath }}
  {{ range $files }}
    <a href="/img/gallery/{{ $gallery }}/{{ .Name }}"></a>
  {{ end }}

</div>
{{ end }}
```

See you soon on [romain.rbind.io](http://romain.rbind.io). 
