---
title: "API Introduction"
teaching: 15 # teaching time in minutes
exercises: 0 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is an API?
- What is a 401 status code?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand what an API is and how it works
- Understand what HTTP requests are

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

HTML websites are a widespread means of sharing information on the internet.
It is unsurprising then that scraping websites is a common practice (in research) 
to obtain information from the web in an automated way.

However, scraping websites has many downsides; it would be much easier if a computer program 
could instead communicate with a data provider directly, requesting exactly the information 
that is needed for the research purpose. This is what Application Programming Interfaces (APIs) accomplish. 

Nowadays, many organizations have restricted access to their public APIs drastically. 
The open-source community remains strong, however, and there are plenty good examples 
of public open APIs such as the scholarly database [OpenAlex](https://openalex.org/).

Their API can be reached at:

https://api.openalex.org/

## Exploring an API

When you open this link in your browser, you won't see much at first. That's because
we haven't actually specified the data we would like to retrieve. In order to understand
how an API works, it is always good to have a look at the 
[API documentation](https://docs.openalex.org/how-to-use-the-api/api-overview), 
a very crucial source of information when communicating with an API.

Reading through the documentation, you will find many so called **endpoints**,
URLs that represent resources such as publications:

https://api.openalex.org/works

You can copy-paste this link to a browser. Alternatively, on the command line you can use `curl`. 
In the [next chapter](api-get-data.md), we will also see how we can use Python and R to obtain data from the API.

Here is a subset of the data displayed when opening the `works` URL in a browser.
OpenAlex returns data as JSON, a common data format for these types of APIs. We
won't cover the specifics of the format here, but a quick web search can give
you some [answers](https://www.w3schools.com/whatis/whatis_json.asp).

```json
{
  "id":"https://openalex.org/W1775749144",
  "doi":"https://doi.org/10.1016/s0021-9258(19)52451-6",
  "title":"PROTEIN MEASUREMENT WITH THE FOLIN PHENOL REAGENT",
  "display_name":"PROTEIN MEASUREMENT WITH THE FOLIN PHENOL REAGENT",
  "publication_year":1951,
  "publication_date":"1951-11-01"
}
```

When looking at the *meta.count* field, you'll notice that the total number of publications
available via `works` is in the hundreds of millions - that's a lot of data. For the purpose of 
this workshop, we would like to reduce this number by applying **filters**. This
is what most APIs are designed to do and it can be very useful if you only wish
to obtain specific subsets of data.

Let's say we are only interested in publications from 2024 written by at 
least one author from the *University of Amsterdam*. To filter by institutions,
OpenAlex uses the so called [ROR](https://ror.org/) identifier.

We can modify the URL like this:

```
https://api.openalex.org/works?filter=institutions.ror:04dkp9463,publication_year:2024
```

URL parameters are indicated with a `?`, in this case for example `filter` or `select`.
We only want to filter for now so we can declare
`filter=` followed by a list of attributes and values, separated by comma. Note 
that the comma indicates an *intersection* which means that we want to filter on
publications that satisfy all of the parameters. It is also possible to filter on
publications that satisfy one or the other. Take a look at the API documentation to explore other 
[filter parameters and configurations](https://docs.openalex.org/how-to-use-the-api/get-lists-of-entities/filter-entity-lists).

## HTTP status codes

We've probably all encountered the famous *404* error message when being redirected
to a website that does not exist. APIs usually provide more informative error messages.

For example, when inserting a typo into one of our parameters, let's say replacing
*publication_year* with *pppublication_year*, we will get a message like this:

`Invalid query parameters error`

This error tells us what to look for.

When making HTTP requests from Python or R, we will see that handling error 
messages is necessary for your code to run without interruptions. Below you will find a list of 
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


