---
title: The New and Improved R-Podcast Site
author: Eric Nantz
date: '2017-04-27'
tags:
  - Hugo
  - blogdown
  - podcast
  - theme
  - knitr
  - rstudio
  - rmarkdown
slug: r-podcast-website
description: How Hugo and blogdown supercharged the online presence of the R-Podcast
---

## In The Beginning ...

When I launched the [R-Podcast](https://www.r-podcast.org) back in 2012, my main goal was to create content that illustrated the power and capabilities of R for both those who are new to statistical computing and those who already have extensive experience with R and/or other statistical computing languages.  On top of producing the audio podcasts and screencasts, it was important to create a robust and comprehensive online presence to share additional details and resources to my listeners.  Like many podcasters, I chose Wordpress as it seemed to always be the top recommendation for creating a website for those new to podcasting.  While Wordpress does provide a decent interface geared towards those who have little or no background in web development, it was nearly impossible to customize the platform without breaking at least one of the many plugins in use.

When Yihui Xie released [knitr](https://yihui.name/knitr/) it was a game-changer for my workflow, as it unleashed the power of [markdown](https://daringfireball.net/projects/markdown/) for authoring reproducible analyses and documentation that could be compiled in web and print formats.  Shortly thereafter the [rmarkdown](http://rmarkdown.rstudio.com/) and [shiny](https://shiny.rstudio.com) packages were released by RStudio which enabled even more possibilities.  I started to dream big: What if I could use this same new workflow for creating the R-Podcast site content?  And what if I could augment the actual episode show notes with detailed articles and even custom shiny applications?  While I could somewhat shoehorn markdown as my authoring format in Wordpress thanks to plugins, it still didn't give the seamless feeling I had when using RStudio to compose my R-Markdown documents.  I found that a class of tools called [static-site generators](https://www.staticgen.com/) for creating web sites supported markdown as a first-class citizen of input formats.  I switched over from Wordpress to a python-based website generator called [Nikola](https://getnikola.com/) which got me closer to my vision, but integrating the features necessary for distributing the podcast media required a lot of hacking in to python code and it ended up being a time-consuming effort.

I was fortunate enough to attend [rstudio::conf](https://www.rstudio.com/conference/) 2017 and that's where I learned of Yihui's new [blogdown](https://github.com/rstudio/blogdown) package that provides a easy and intuitive wrapper to the [Hugo](http://hugodocs.netlify.com/) website generator.  Immediately I did a bit of research and found that there was a Hugo theme called [castanet](https://github.com/mattstratton/castanet) tailored for podcasts!  It almost seemed too good to be true: I could author the site content with my favorite workflow, and also have the special enhancements needed for the podcast media content practically out of the box.  During one of the evenings I told Yihui about my plans to move to blogdown and he was very supportive and happy to help if I encountered any bumps along the way.  It's been quite a journey, and there is more work to be done, but the site is now powered by blogdown!  What follows is a recap of the technical configurations and my future plans for the R-Podcast site.

## A Brief Tour

Before I go too much further I want to thank the author of the castanet theme [Matt Stratton](https://github.com/mattstratton) who hosts the [Arrested DevOps](https://www.arresteddevops.com/) podcast.  Many of the features I tried to build from scratch when using Nikola were already solved by his excellent theme.  The first thing you will see when visiting the R-Podcast site is a partial listing of each episode sorted by most recent.  One of the many nice features of the [castanet](https://github.com/mattstratton/castanet) theme is a lightweight player for each episode that fits nicely with the overall appearance based on bootstrap.  On the side margin there are sections for the various methods of subscribing to the podcast, a collection of my favorite sites related to R, and a simple widget to join a mailing list.  

Each episode is launched by using a custom `episode` archetype, and within blogdown I make a call to `new_content("episode/name_of_episode.md")` and I'm ready to go.  I have plans to create a custom RStudio add-in for authoring new episode posts that mimics the [new post addin](https://github.com/rstudio/blogdown/blob/master/inst/scripts/new_post.R) already part of blogdown, which if nothing else will give me more show content later on!  

One customization I made is the [Guests](https://www.r-podcast.org/guests/) page.  The castanet theme enables me to define a set of [`yaml` files](https://github.com/rbind/r-podcast/tree/master/data/guests) for each guest that appears on the podcast, and by default I can simply list their unique identifier in the episode front-matter to have their information automatically appear on the appropriate episode.  But I wanted to take it a step further and give visitors an easy way to view a list of all of the guests who have appeared on at least one episode of the podcast.  It was very straight-forward to create an [additional layout](https://github.com/thercast/castanet/blob/master/layouts/guests/single.html) inside the theme and now anytime a new guest appears on the show this page will be automatically updated once I add their ID to the front matter.  Other sections of the site were very easy to create with simple markdown and embedded HTML fragments such as the contact form.

## Future Plans

At this point I've laid a solid foundation for the site and in the early days of the launch it has been well-received.  In the future I plan on taking full advantage of authoring companion articles and tutorials that complement the audio content.  The best part is I can make this additional content entirely with R-Markdown and never leave the comforts of the RStudio IDE to make it all happen.  I also plan to interact with APIs associated with parts of my production pipeline to achieve an almost-automated build process for each episode.  All of these ideas are within my grasp thanks to the power of [blogdown](https://bookdown.org/yihui/blogdown/), R Markdown, and of course R!
