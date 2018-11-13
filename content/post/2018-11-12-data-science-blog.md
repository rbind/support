---
title: "Data Science Blog: My Experiences with Data Science, Blogging, and R"
author: Matthias Döring
date: '2018-11-12'
slug: "data-science-blog"
categories:
  - Blogdown
  - R
  - Hugo
tags:
  - data science
  - machine learning
  - data visualization
description: "An introduction to the data science blog at www.datascienceblog.net and an overview of my journey towards running a static blog with blogdown."
---
Between 2012 and 2017, the [demand for data scientists has increased by a whopping 650%](https://www.forbes.com/sites/louiscolumbus/2017/12/11/linkedins-fastest-growing-jobs-today-are-in-data-science-machine-learning/#417212a651bd). Why is data science such a hot topic? There are multiple factors at play:

* **Emerging technologies** are producing decidedly more data than previously and these data need to be dealt with.
* **Recent advances in machine learning** have produced new algorithms that are particularly suitable for big data.
* **Digitization is steadily advancing** and data analytics are an important aspect of this trend.

## What is a data scientist?

[The term data scientist was first coined in a paper published by William S. Cleveland in 2001](https://pdfs.semanticscholar.org/915c/d8e2b39eb02723553913d592b2237d4d9960.pdf). In his publication, Cleveland argues for the extension of statistics into other areas such as multidisciplinary projects, data modeling, and computing. In my opinion, data science is best understood as an interdisciplinary discipline unifying all skills that are useful for processing, analyzing, and interpreting data. According to online job platforms, [the most relevant data science skills are the following](https://towardsdatascience.com/the-most-in-demand-skills-for-data-scientists-4a4a8db896db):

* **Modeling:** data analysis, machine learning, statistics, mathematics, and visualization.
* **Computation:** computer science, software development, and data engineering.
* **Soft skills:** a keen interest in the data generation process, ability to think outside the box, and good communication skills.

Since data scientists need to have a diverse set of skills, there are few people who excel in all of these areas. These people are called *unicorns* to foreshadow their rarity.

## What is my relation to data science?

To be honest, I am not a data scientist by training. I hold a Bachelor's and a Master's degree in bioinformatics, so I **never took part in a data science curriculum**. However, I still consider myself a data scientist because the work I am currently doing is highly focused on analyzing data using machine learning and statistics.

The benefit of labeling oneself as a data scientist is that one is not limited to a specific field. For example, although I am currently applying data science on biological data, I could use similar techniques on completely different types of data. Due to the ubiquity of data science throughout all quantitative fields, data scientists have diverse backgrounds such as computer science, physics, or mathematics. 

## My experience as a blogger

In 2009 a friend and I created bloxxo, a German blog that offered tips and tricks on how to be a successful blogger. We were very motivated and had **ambitious goals**. Although we successfully formed a close-knit community and reached a page rank of 4 after only a few months, we **could not hold up the pace**. Writing at least 2 posts every day just required too much time and effort. Besides, both of us were working on our Bachelor's degrees at that time, so free time was a luxury. Thus, we had to discontinue the blog.

My return to blogging has two sources of motivation. The first one is time. Since I plan to wrap up my PhD soon, I should have more spare time for blogging. The second is my desire to give something back to the community. When I was researching answers to practical coding questions related to my work, this was often gruesome. Although it is easy to find some explanations including code snippets, these solutions are often not easily understood and may not actually work as described. So, my goal was to provide a resource providing well-written, well-structured, and accurate information.

## My experience with R and blogdown

I began using R when I got into machine learning in 2011; I have been a fan ever since. In the meantime, I have even developed two R packages, which are available via Bioconductor ([openPrimeR](https://bioconductor.org/packages/openPrimeR) and [openPrimeRui](https://bioconductor.org/packages/openPrimeRui)). Thus, when I thought about creating a blog about data science, it was clear to me that I had to use R as a programming language.

![Data science blog](https://user-images.githubusercontent.com/25709555/48361301-8462f100-e6a1-11e8-89a7-790378295435.jpg)
*Main page of datascienceblog.net*

The idea behind [my blog on data science](https://www.datascienceblog.net) was to focus on applications of data science in R, covering areas such as statistics, data visualization, and machine learning. One of my goals was to make all blog posts reproducible by integrating R code into the posts. After some research, I stumbled upon the [blogdown package](https://bookdown.org/yihui/blogdown/). At first I was skeptical because I did not believe that it would be that easy to create a website using the package but [it turned out that my skepticism was unfounded](https://www.datascienceblog.net/post/other/blogdown_hugo/).

## Blog customization

After spending several hours investigating different [Hugo](https://www.datascienceblog.net/tags/hugo/) templates, I decided to use the [Mainroad theme](https://themes.gohugo.io/mainroad/) because it resembles the content-driven templates from WordPress, which is why I think that Mainroad is ideally suited for a blog. 

The Achilles' heel of static websites is that these sites lack potential for interaction. Therefore, to integrate a commenting system into my blog, I included Disqus. However, I was never really happy with that decision for two reasons:

1. **Professionality:** In my opinion, the Disqus system does not make a very professional impression.
2. **External storage:** Using Disqus, comments are stored on an external server and are not part of the site itself, although they should be.

So, I searched for alternatives to Disqus and stumbled upon [Staticman, which brings user-generated content to static websites](https://staticman.net/). So, I [set up my own instance of Staticman](https://www.datascienceblog.net/post/other/staticman_comments/), which I am currently successfully using to run the commenting system of my blog. If you would like to see the system in action, just click on the previous link.

Since my blog deals with a lot of R code, I wanted to make the code easily retrievable. Therefore, each post provides two buttons, which provide the following functions:

* **Downloading raw RMarkdown files from GitHub:** By downloading the Markdown files it is possible to go through the posts even offline, by knitting the Markdown locally.
* **Copying all code chunks from a post:** This makes it much easier to copy & paste code into the R interpreter in order to experiment for yourself.

Both functions are implemented through a [custom partial template](https://github.com/rbind/data-blog/blob/master/themes/Mainroad/layouts/partials/post_download_Rmd.html) that is included when viewing individual posts. More specifically, the first function simply entails constructing a path to GitHub that is based on the current file's path. For the second function, I implemented the following JavaScript function:

```javascript
function copyToClipboard() {
  // Create an auxiliary hidden input
  var aux = document.createElement("textarea");
  // Get all elements with class name "r" (<=> R code)
  var codeElements = document.getElementsByClassName("r");
    // iterate over all code boxes & collect code
    var codeBuffer = []; // use buffer for performance
    for (var i = 0; i < codeElements.length; i++) {
        var codeSnippet = codeElements[i].innerText; 
        codeBuffer.push(codeSnippet);
    }   
    var code = codeBuffer.join("<br><br>"); // add line breaks after chunks
    // regular expression for replacing breaks with newlines
    var brRegex = /<br\s*[\/]?>/gi;
    code = code.replace(brRegex, "\r\n");
  aux.value = code;
  // Append the aux input to the body
  document.body.appendChild(aux);
  // Highlight the content
  aux.select();
  // Execute the copy command
  document.execCommand("copy");
  // Remove the input from the body
  document.body.removeChild(aux);
};
```

## Outlook

My goal is to establish my blog as a useful resource for R and data science. Besides frequently writing high-quality posts, I plan to do more work in the following areas:

* Customization of the Mainroad theme to improve the recognition factor of the blog
* Incorporation of Staticman for more than commenting (e.g. for a polling system)
* Improvement of community outreach

Coming to the end of this article, I would like to thank the rbind project for the terrific idea of connecting all R bloggers. I am excited about the future of static blogging and I am looking forward to learn more by sifting through all of the blogs that are united through rbind.
