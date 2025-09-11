---
title: "API Introduction"
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
Unsurprisingly then, scraping websites is a common practice to 
obtain information from the web in an automated way.

However, it was much easier if a computer program could instead communicate with
a data provider directly, requesting exactly the information that is needed for research purposes. 
This is what Application Programming Interfaces (APIs) accomplish. 

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

`https://api.openalex.org/works`

You can simply paste this link in a browser to see what it contains. 
Alternatively, on the command line you can use `curl`. In the [next episode](api-get-data.md), we
will also see how we can use Python and R to obtain data from the API.

Here is a subset of the data displayed when opening the `works` url in a browser.
OpenAlex returns data as JSON, a common data format for these types of APIs. We
won't cover the specifics of the format here, but a quick web search can give
you some [answers](https://www.w3schools.com/whatis/whatis_json.asp).

```json
{"id":"https://openalex.org/W1775749144","doi":"https://doi.org/10.1016/s0021-9258(19)52451-6","title":"PROTEIN MEASUREMENT WITH THE FOLIN PHENOL REAGENT","display_name":"PROTEIN MEASUREMENT WITH THE FOLIN PHENOL REAGENT","publication_year":1951,"publication_date":"1951-11-01"}
```

When looking at the meta.count field, you'll notice that the total number of publications
available via `works` is 270,765,445 which is quite large. For the purpose of 
this workshop, we would like to reduce this number by applying filters. This
is what most APIs are designed to do and it can be very useful if you only wish
to obtain the data that is really needed.

Let's say we would like to only look at publications from 2024 written by at 
least one author from the University of Amsterdam. To filter on institutions,
OpenAlex uses the so called [ROR](https://ror.org/) identifier.

We can modify the URL like this:

```
https://api.openalex.org/works?filter=institutions.ror:04dkp9463,publication_year:2024
```

Take a look at the API documentation to explore other 
[filter parameters](https://docs.openalex.org/how-to-use-the-api/get-lists-of-entities/filter-entity-lists).

## HTTP status codes

We've probably all encountered the famous `404` error message when being redirected
to a website that doesn't exist. APIs usually provide more informative error messages.

For example, when inserting a typo into one of our parameters, let's say replacing
`publication_year` with `pppublication_year`, you'll see a message like this:

`Invalid query parameters error`

This error tells you what to look for.

When making HTTP requests from Python or R, we will see that handling error 
messages is necessary for your code to run well. Below you'll find a list of 
the most common status codes and what they mean.

|Code|Name                 |Meaning                                                                   |
|----|---------------------|--------------------------------------------------------------------------|
|200 |OK                   |The request has succeeded.                                                |
|204 |No Content           |The server has completed the request, but doesn't need to return any data.|
|400 |Bad Request          |The request is badly formatted.                                           |
|401 |Unauthorized         |The request requires authentication.                                      |
|404 |Not Found            |The requested resource could not be found.                                |
|408 |Timeout              |The server gave up waiting for the client.                                |
|500 |Internal Server Error|An error occurred in the server.                                          |


