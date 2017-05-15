---
date: 2017-05-15
title: Converting robjhyndman to blogdown
---

## Some history

I started my website in 1993, only a few months after [the WWW was put into the public domain](https://home.cern/topics/birth-web). I began by looking at some existing sites to see how html worked, and then writing my own handcrafted html files. I maintained those html files for about 13 years, through several domain name changes as the web matured, and as I moved between institutions.

In 2006 I was convinced that using a content management system would make my life easier, and I converted the site to Joomla. A couple of years later, Wordpress seemed to have more features, so I converted from Joomla to Wordpress where it stayed for about 9 years. Here is an image of what it looked like in 2009 just after converting to Wordpress.

![robjhyndman.com in 2009 on Wordpress](/images/rjh2009.png)

During that time, the site grew into ten Wordpress installations connected together in a rather ad hoc manner to form a Wordpress network comprising about 1000 separate pages and posts.

Apart from being very slow (to edit and view), the biggest problem I had with Wordpress was writing about R. My R code would have to be copied across manually, and all figures needed to be uploaded separately. I really wanted to write in Rmarkdown, but it was difficult to convert Rmarkdown to Wordpress, and I would often spend as much time uploading the various pieces of a blog post as I would in actually writing it.

For a while I was tempted to convert to Jekyll, but that wouldn't have solved my Rmarkdown problem. When Blogdown came along, I thought it was the perfect vehicle for producing my website and would make it much faster, and easier to write R-related posts.

## Converting Wordpress to Hugo

In order to use Blogdown, I needed to convert all my Wordpress pages and posts to work with Hugo (which underpins Blogdown).

At first I tried to use Cyrill Shumacher's [Wordpress to Hugo exporter](https://github.com/SchumacherFM/wordpress-to-hugo-exporter) but it kept timing out (perhaps because my site was too large) and I gave up on it.

Then I found Justin Dunham's post on [Migrating from Wordpress to Hugo](http://justindunham.net/migrating-from-wordpress-to-hugo/) which was extremely helpful. It suggested using the [ExitWP tool](https://github.com/thomasf/exitwp) which is designed for converting Wordpress to Jekyll but since Jekyll is also based on markdown, it is easy to copy the converted posts and pages across.

I exported the various Wordpress xml files for my site, ran xmllint on each file and fixed any errors, then converted them using exitwp to create markdown files.

At this point I thought something could go wrong, so I also created a completely offline backup version of my site using [HTTrack](http://www.httrack.com) so that any content could be checked after I switched.

Later I discovered that a few of the converted markdown files were completely empty and the offline backup was very useful in reconstructing them.

## Correcting the markdown files

There were many issues with the generated markdown, but nothing that couldn't be fixed with regexp expressions and sed. I spent a long time checking each page, and when I found a problem I used a general sed command on all posts to fix it everywhere. 

Some of the posts involving R code were turned into Rmd files so that the R images were naturally embedded, and so that I could be sure the R code still worked.

A few out-of-date posts were simply deleted, and several whole sections of the website were retired (old blogs, and pages associated with my old forecasting book), and all the software pages were replaced with links to github repositories.


## Theming problems

The biggest problem I saw with Blogdown/Hugo was that the themes were fairly limited, and most of those available were (in my view) relatively unattractive, or designed for much more simple sites than mine. But I came across [Kieran Healy's site](https://kieranhealy.org/) which was written in Hugo, and I thought it might be a suitable model.

So I forked his [github repository](https://github.com/kjhealy/kieranhealy.hugo), removed all his content, and started copying in my own content, a few files at a time so I could test if it would break.

At this point, I had a long trip from Australia to Europe -- a perfect time for trying to get my website working offline. I spent most of the trip copying content, finding problems, and hacking into Kieran's theme to fix them. By the time I reached Amsterdam, it was looking pretty good and I had learnt a lot about how hugo themes worked through trial and error.

The last step (I thought) was switching from Hugo to Blogdown. So before writing any Rmarkdown files, I tried to compile the Hugo site using Blogdown instead. It didn't work. After some investigation, I realised that Kieran Healy's theme just wasn't set up for Blogdown to use, and I had wasted a lot of time on my flight. I needed a new theme that was compatible with Blogdown.

I found that the [hugo-finite](https://themes.gohugo.io/hugo-finite/) theme worked with Blogdown, and had been inspired by Kieran Healy's theme, so I decided to try modifying that.

I started again with a vanilla site using hugo-finite, working from Blogdown rather than Hugo to make sure it was going to work this time. I copied my content into this new site, and started modifying the theme to match what I had already done previously. Many hours later, I had something that looked like what I had done previously, but this time it worked with Blogdown.

So my theme is something of a mash-up between hugo-finite and Kieran Healy's theme, with a few features of my own.

## Putting it online

My site gets too much traffic for the free hosting sites, so I host it on [Siteground](https://www.siteground.com/index.htm?afcode=31a2a533d54be661222f2437d073adad). At first I used Filezilla to copy the public folder of my site to Siteground, and checked that it worked. Then I made it live. Voila! It worked.

Next I set up a [Makefile](https://raw.githubusercontent.com/rbind/robjhyndman.com/master/Makefile) to build the site and rsync any new files to Siteground.

Now I can just edit a file, type "make deploy" in a terminal window, and the site is built and updated in a few seconds. Amazing.


## Was it worth it?

Definitely. The whole process took me many more hours than I expected, but it is so much easier to maintain, write posts, update, etc. The site is now 24 years old, but this is by far the simplest and fastest version to administer.

For those interested, the source code for the site is [hosted on github](https://github.com/rbind/robjhyndman.com). The theme can be modified for other people to use, but some of it is hard-coded with my details. One day I might clean it up to make it easier for other people to use the same theme.
