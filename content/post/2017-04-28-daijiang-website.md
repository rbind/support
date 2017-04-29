---
title: A not-so-technical introduction to Daijiang's personal website
author: Daijiang Li
date: '2017-04-28'
slug: daijiang-website
tags:
  - Hugo
  - theme
  - Disqus
  - Github
  - Netlify
  - blogdown
description: Some set ups of Daijiang's website.
---

I am an ecologist and statistician, working as a postdoc currently. For me, what I need is a website that I can introduce myself to the public, archive some of my experiences, and communicate my thoughts with others. So I do not need fancy stuff. Static website fits this bill perfectly. I need a tool that can deal with most of the website constructing and I can focus on the content. Recently, I have moved [my personal website](https://github.com/rbind/daijiang) from `Jekyll` to `Hugo` and I loved it. `Hugo` is already very easy to use. Yihui's awesome R package [blogdown](https://github.com/rstudio/blogdown) makes it even easier. Therefore, if you are a R user, I recommend to work with the `blogdown` package.

Here, I briefly explain the structure of my website. Since I have very similar set up with [Yihui's website](https://yihui.name) and I used his [modified hugo-lithium-theme](https://github.com/yihui/hugo-lithium-theme)^[frankly, I cloned his website and then tweaked based on it, which I think is the easist way to get started. If you also want clone his or my website, I suggest to use `git clone --recursive url-of-github-repo`, which will also clone the theme for you.], I strongly recommend to read his [website set up](/2017/04/25/yihui-website/).

Here is the tree structure of my website source code:

```
├── R
│   ├── build.R
│   ├── build_one.R
│   └── clean_blogs.R
├── README.md
├── config.yaml
├── content
│   ├── 404.md
│   ├── _index.md
│   ├── about.md
│   ├── cn
│   ├── cn-about.md
│   ├── cn-vitae.md
│   ├── en
│   ├── en-about.md
│   ├── en-vitae.md
│   ├── links.md
│   ├── research.md
│   ├── resume.md
│   └── zoey
├── index.Rmd
├── layouts
│   ├── _default
│   └── partials
├── static
│   ├── CNAME
│   ├── css
│   ├── fonts
│   ├── images
│   ├── js
│   └── pdf
├── themes
│   └── hugo-lithium-theme
└── website.Rproj
```

Let's look at them individually. 

- `R` folder: this folder hosts R scripts. The `build.R` and `build_one.R` were cloned from Yihui and they are used to convert `*.Rmd` to `*.md`. I did not use them yet. The `clean_blogs.R` was written by me and mainly to change yaml headers from `jekyll`. So, basically, you can ignore this folder.
- `README.md`: some explanation for github repository.
- `config.yaml`: this is the main file where you set up things. It is pretty straightforward but you need be careful to put all your information correct, e.g. Disqus shortname, Twitter handle, etc.
- `content` folder: this the folder to put your webpages and blog posts. For example, I have `_index.md`, `about.md`, `resume.md`, `research.md`, and three subfolders that will be turned into three blogs. If you open my [website](https://daijiang.name), it will be clear what roles these files/folders have. You can order them in the `config.yaml` file with the `weight` option^[start with 1 instead of 0.].
- `index.Rmd`: you do not need to change it.
- `layouts` folder: this folder has files that will control the details of the website.

    ```
    layouts
    ├── _default
    │   ├── list.html
    │   └── single.html
    └── partials
    │   ├── article_meta.html
    │   ├── disqus.html
    │   ├── fix404.html
    │   ├── footer.html
    │   ├── head_custom.html
    │   ├── nav.html
    │   └── prev_next.html
    ```

    For example, I changed `partials/footer.html` file to include an email icon <i class="fa fa-envelope"></i> in the footer of web pages. I also included information of the last change of the website in the footer. Change according to your need. The `partials/article_meta.html` will show the icons at the top right of each blog post. If you have multiple blogs, make sure to change some of the line 7 in this file (I have 3 blogs here). The `_default/single.html` assemble parts that defined in the `partial` folder together for each single page. Here, also remember to change things if you have multiple blogs. 
- `static` folder: holds customer defined css files and other things such as your avatar. Replace `images/logo.png` file with your favorite icon. I also created a `pdf` folder to host some of my papers. The `CNAME` file may not be necessary if you host your website through Netlify.
    + `css/custom.css`: change this file if you want to tweak things defined in the theme.
- `themes` folder: to hold themes. If you use regular `git clone` to clone my website, you will find it is empty. You can add the theme I use back with 

    ```
    git submodule add git@github.com:yihui/hugo-lithium-theme.git themes/hugo-lithium-theme
    ```

- `website.Rproj`: I use [RStudio](https://www.rstudio.com/products/rstudio/#Desktop) to write my posts^[including this one.]. 

If you have installed `blogdown` package, in RStudio, you can use the `Addins -- New Post` to create a new post. In this way, you do not need to type the structure of the yaml header.
![RStudio addin New Post](https://cloud.githubusercontent.com/assets/1696911/25552789/89b7b902-2c70-11e7-8235-8e9f1abe409f.png)

That's it. Hopefully now you can clone the websites that you like (e.g. from [rbind.io](https://github.com/rbind)) and start to create your own website^[If you want to start it from scratch, this post is not for you. 😀😬😁]. After done, you can click the `Addins -- Serve Site` in RStudio (also shown in the above picture) and see how it looks. 

Now, it is time to make your website public. I recommend to use [Netlify](www.netlify.com). Its free plan allows you to deploy your github repository there with your own domain. Whenever you change the source code of the website on github, netlify will automatically rebuild it for you! How cool it that? To host your website with github pages, see [here](https://daijiang.name/en/2017/03/30/updating-website-with-hugo-and-blogdown/#publish-your-website).

Happy blogging!
