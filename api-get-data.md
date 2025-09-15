---
title: "Getting data"
teaching: 10 # teaching time in minutes
exercises: 2 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 



::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Read a dataset from file or fetch data via API

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::: callout

You do this part on your own. Follow the instructions for your language.

::::::::::::::::::::::::::::::::::::::::::::::::

## Method 1: read data from file

::::::::::::::::::::::::::::::::::::: group-tab

### Python

asdf

### R

asdf

::::::::::::::::::::::::::::::::::::::::::::::::

## Method 2: get data via API

For this part, we will use HTTP libraries for either Python or R.
We will use the most commonly used libraries for this workshop, but if you're
already familiar with any other, feel free to use those.


### GET vs. POST requests

Before we start making requests, you should be aware of the two most relevant
[HTTP request types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods) 
for our purposes, GET and POST.

In simple words, GET requests retrieve data from the server, without sending
any content, while POST requests send data and retrieve data in response.

When interacting with a language model, we are most likely going to send 
input data (text) to the server, which means we will be making POST requests. 
To retrieve data from OpenAlex, we will be using GET.


::::::::::::::::::::::::::::::::::::: group-tab

### Python

First, we need to install the `requests` library:

```bash
pip install requests
```

Now, we can import both requests and another built-in library to parse json
data.

```python
import requests
import json
```

Retrieving the data is as simple as calling the get() method using our URL
from before:

```python

response = requests.get("https://api.openalex.org/works?filter=institutions.ror:04dkp9463,publication_year:2024")

data = response.json()
```

There is also a Python library that simplifies using the OpenAlex API:
[pyalex](https://github.com/J535D165/pyalex). The library is well-documented
and its usage won't be covered in this workshop.

### R


There is also an R library that simplifies using the OpenAlex API:
[openalexR](https://github.com/ropensci/openalexR). The library is well-documented
and its usage won't be covered in this workshop.

::::::::::::::::::::::::::::::::::::::::::::::::
