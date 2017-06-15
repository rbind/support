---
title: Building an academic website using blogdown
author: Alison Presmanes Hill
date: '2017-06-16'
slug: academic-site-apreshill
tags:
  - Hugo
  - academic
  - Github
  - Netlify
  - blogdown
description: Alison's overview for personalizing the hugo-academic-theme
---

# About me

I am a professor of pediatrics in [Oregon Health & Science University's](https://www.ohsu.edu) [Center for Spoken Language Understanding](https://www.ohsu.edu/xd/research/centers-institutes/center-for-spoken-language-understanding/). My [research](https://apreshill.rbind.io/publication/) focuses on autism, and I [teach](https://apreshill.rbind.io/#teaching) graduate-level courses in OHSU's [Computer Science](https://www.ohsu.edu/csee) education program. I also have developed and led several [R workshops](https://apreshill.rbind.io/#talks) and smaller team-based training sessions, and love to train new “useRs”. And believe it or not, I have never had a website! This was way overdue, so when I saw `blogdown`, I decided I had no excuses left since I could now do everything from the comfort of RStudio. I'm really happy with [my new site](https://apreshill.rbind.io), and you can view the source content on [GitHub](https://github.com/rbind/apreshill).

# How to start

I wrote up my detailed notes about how to get up and running using [`blogdown`](https://bookdown.org/yihui/blogdown/) + [GitHub](https://github.com) + [Netlify](https://www.netlify.com), so I would suggest that you start [there](https://apreshill.rbind.io/post/up-and-running-with-blogdown/)! The [tutorial](https://apreshill.rbind.io/post/up-and-running-with-blogdown/) is more general and intended for new `blogdown` learners, and is not specific to any one Hugo theme choice. Here I wanted to provide some details for academics who want to get started.

# A dynamic CV

I opted for the [Hugo academic theme](https://github.com/gcushen/hugo-academic) mainly based on Yihui and Amber's [recommendation](https://bookdown.org/yihui/blogdown/other-themes.html)- it was great advice. This theme is perfect if you are faculty or a graduate student, or even a wannabe graduate student applying to masters or PhD programs. The theme offers all the sections present in a standard curriculum vitae with a clean simple interface. If you are an academic, you probably know that although publications are king for promotions and getting grants, you do a lot of work that is "extracurricular" like mentoring, service, and teaching. This theme allows you to flexibly highlight and document these important contributions. 

# Personalizing your site

You'll get the quickest pay-off by adding your avatar photo to your `static/img` folder, then editing the [`config.toml`](https://github.com/rbind/apreshill/blob/master/config.toml). Add your contact information, academic affiliations, and links to all of your social networks. The academic theme allows you to use both [Font Awesome icons](http://fontawesome.io) as well as [Academicons](http://jpswalsh.github.io/academicons/) to you can link to all of the things!

Next, edit your `about.md` page, which is in the `content/home` folder. This is where you can list your academic interests, your education/degrees, and write a brief bio for yourself. 

After doing these 3 things, your site should be shaping up pretty nicely, and then you can start digging deeper into that `content` folder and refining your content.

![](site-screenshot.png)

Finally, my advice to students when they are learning `ggplot2` is to play with the default settings, and I have the same advice for your `blogdown` site. The academic theme offers a way to link to a custom CSS in the `config.toml` file, and this is a nice way to make your site look unique by changing simple elements like colors and fonts. 

```
  # Link custom CSS and JS assets
  #   (relative to /static/css and /static/js respectively)
  custom_css = ["blue.css"]
```

You can check out [my custom css](https://github.com/apreshill/apreshill/blob/master/static/css/blue.css) to see how I customized the academic theme, which I based off of this [gist](https://gist.github.com/gcushen/d5525a4506b9ccf83f2bce592a895495).


# Get it out the door

The best advice I ever got in graduate school was *"Progress not perfection."* At some point, you need to transition into *get-it-out-the-door* mode. You can always make changes later. I opted to use [Netlify](https://www.netlify.com) for deployment based on Yihui and Amber's [recommendation](https://bookdown.org/yihui/blogdown/deployment.html) again. The [process](https://apreshill.rbind.io/post/up-and-running-with-blogdown/#deploy-in-netlify) was very smooth if you link it up with your [GitHub repository](https://apreshill.rbind.io/post/up-and-running-with-blogdown/#in-github) from the start. 

The brilliant thing about using `blogdown` is that, if you are already an RStudio user, it will be that much easier for you to keep your website up to date. I'm excited to have one place to start sharing my workshops and teaching materials. It is definitely a work in progress, so [check back in with me](https://apreshill.rbind.io)!

