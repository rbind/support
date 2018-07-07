---
title: About Rbind Support
date: 2015-06-20T14:02:37+02:00
layout: about
---

The goal of the Rbind project is to provide a service like [WordPress.com](https://wordpress.com) or [Medium](https://medium.com), but driven by the community^[Including but not limited to the R and statistics communities.] instead of a certain company. We hope users can help each other to build the websites they want. Currently most websites in this project are built using the [**blogdown**](https://github.com/rstudio/blogdown) package, but you are welcome to use other tools if you want.

To make it easier to discover websites and get inspirations from other people's websites, we created the Github organization "[rbind](https://github.com/rbind)" as a central place to host all websites. For example, if you are curious about how a particular website was built, you may study its source files, or even ask the author via Github issues.

## How to join Rbind

We do not really have hard restrictions on what kind of websites we expect to see in Rbind, but we will certainly be happy to host websites related to R and/or statistics.

- If you do not have a website yet, please read [the **blogdown** book](https://bookdown.org/yihui/blogdown) to create one.

- If you have a website with its source hosted on Github, you can [transfer](https://help.github.com/articles/transferring-a-repository-owned-by-your-personal-account/) the repo to Rbind if you want.

    - Please note that we will send you an invitation to join Rbind as a member, and you have to accept the invitation (_check your email_) before you can transfer your repo.

If you do not own a domain name, we can offer a subdomain `*.rbind.io` to you for free as long as it is still available, and just let us know your desired subdomain name by filing [a Github issue](https://github.com/rbind/support/issues).

If you know how a domain name works, please let us know the DNS record we should set for your `*.rbind.io`, otherwise we recommend you to connect your Github repo with [Netlify](https://www.netlify.com) (more details in the [**blogdown** book](https://bookdown.org/yihui/blogdown/netlify.html)), and we can point the CNAME record of our subdomain to your Netlify subdomain. Then _you need to configure the custom domain on Netlify_ by hitting the "Configure domain" button (people often forget this step):

![Configure domain on Netlify](https://user-images.githubusercontent.com/163582/31508235-11282aa2-af43-11e7-8204-3d019ef7fe33.png )

If you have received help from the Rbind community, please consider giving back in the future by helping newcomers after you know more about websites and become familiar with **blogdown**.

## What is this website for and not for

This support website, [support.rbind.io](https://support.rbind.io), is primarily for two types of announcements: technical changes or news or solutions related to Rbind and **blogdown**, and announcements of new websites landed at Rbind. The first type is authored by the support team, and the second type is authored by website owners sharing their experience and introducing their own websites.

This website is hosted on Github ([rbind/support](https://github.com/rbind/support)). Please feel free to fork the repo, create new posts using **blogdown**, and send us Github pull requests ([examples](https://github.com/rbind/support/pulls?utf8=%E2%9C%93&q=is%3Apr)) to introduce or promote your website and share your experience with building websites. Please include links to your website and the source repository in your post.

It is not a place for you to ask technical questions related to **blogdown**. All such questions should be posted to StackOverflow instead with tags `r` and [`blogdown`](http://stackoverflow.com/tags/blogdown).
