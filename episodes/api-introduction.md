---
title: "Application Programming Interface"
teaching: 10 # teaching time in minutes
exercises: 2 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is an API?
- What is a 401 status code?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand what an API is and how it works
- Understand what HTTP requests are
- Being able to install HTTP libraries for Python or R

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

HTML websites are the widespread means of sharing information on the internet.
It comes at no surprise then that scraping websites is a common practice to 
obtain information from the web in an automated fashion.

However, it would be much easier if a computer program could instead communicate with
a data provider directly, requesting exactly the information that is needed, for
example for research purposes. This is where APIs, Application Programming Interfaces,
come into play. 

Sadly, many organizations have restricted access to their public APIs drastically 
over the years. However, the open-source community remains strong and there are
plenty good examples of public open APIs such as the scholarly database 
[OpenAlex](https://openalex.org/).

Their API can be reached at https://api.openalex.org/

Once you open this link in your browser, you won't see much. That's because
we haven't actually specified any data we would like to retrieve. Luckily, on that
page, you'll find a link to the API documentation, a very crucial source of information
when communiting with an API. 

Reading through it, you will find suitable endpoints, such as /works:

```
https://api.openalex.org/works
```


:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::: instructor

Inline instructor notes can help inform instructors of timing challenges
associated with the lessons. They appear in the "Instructor View"

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge 

## Challenge 1: Can you do it?

What is the output of this command?

```r
paste("This", "new", "lesson", "looks", "good")
```

:::::::::::::::::::::::: solution 

## Output
 
```output
[1] "This new lesson looks good"
```

:::::::::::::::::::::::::::::::::


## Challenge 2: how do you nest solutions within challenge blocks?

:::::::::::::::::::::::: solution 

You can add a line with at least three colons and a `solution` tag.

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

## Figures

You can use standard markdown for static figures with the following syntax:

`![optional caption that appears below the figure](figure url){alt='alt text for
accessibility purposes'}`

![You belong in The Carpentries!](https://raw.githubusercontent.com/carpentries/logo/master/Badge_Carpentries.svg){alt='Blue Carpentries hex person logo with no text.'}

::::::::::::::::::::::::::::::::::::: callout

Callout sections can highlight information.

They are sometimes used to emphasise particularly important points
but are also used in some lessons to present "asides": 
content that is not central to the narrative of the lesson,
e.g. by providing the answer to a commonly-asked question.

::::::::::::::::::::::::::::::::::::::::::::::::


## Math

One of our episodes contains $\LaTeX$ equations when describing how to create
dynamic reports with {knitr}, so we now use mathjax to describe this:

`$\alpha = \dfrac{1}{(1 - \beta)^2}$` becomes: $\alpha = \dfrac{1}{(1 - \beta)^2}$

Cool, right?

::::::::::::::::::::::::::::::::::::: keypoints 

- Use `.md` files for episodes when you want static content
- Use `.Rmd` files for episodes when you need to generate output
- Run `sandpaper::check_lesson()` to identify any issues with your lesson
- Run `sandpaper::build_lesson()` to preview your lesson locally

::::::::::::::::::::::::::::::::::::::::::::::::

[r-markdown]: https://rmarkdown.rstudio.com/
