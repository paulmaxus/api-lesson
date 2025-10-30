---
title: "Getting data"
teaching: 5 # teaching time in minutes
exercises: 15 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 

- How can I read the dataset into Python or R?
- How can I access data via an API using Python or R?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Read a dataset from file or fetch data via API

::::::::::::::::::::::::::::::::::::::::::::::::

Before looking at the LiteLLM API, we want to make sure that we have a dataset 
to work with. We will be using publications data from OpenAlex. You can either
load a prepared dataset (see [Data Sets](https://paulmaxus.github.io/api-lesson/index.html#data-sets)) 
or use the API programmatically and obtain the data yourself.

::::::::::::::::::::::::::::::::::::::::: callout

You do this part on your own. Follow the instructions for your preferred programming language.

::::::::::::::::::::::::::::::::::::::::::::::::

## Method 1: read data from file

::::::::::::::::::::::::::::::::::::: group-tab

### Python

**Read csv data**

There are many ways to read tabular data in Python. We'll be using `pandas`.
If you're not familiar with the library, you can follow this 
[Carpentries episode](https://swcarpentry.github.io/python-novice-gapminder/07-reading-tabular.html).

```python
import pandas as pd
```

Let's read the dataset:

```python
data = pd.read_csv("publications2024.csv")
```

**Read json data**

Inverted abstracts are stored in the JSON format which we already encountered
in the previous episode. In Python, you can read and write JSON using the `json`
library.

```python
import json
```

We can use the `with` statement to open and read the file, then use `json` to 
load the JSON as a Python object, a dictionary.

```python
with open("abstracts_inverted.json", "r") as f:
    abstracts_inverted = json.loads(f.read())
```

### R

**Read csv data**

There are many ways to read tabular data in R, for instance the built-in `read.csv()`,
which you might have encountered in this 
[Carpentries episode](https://swcarpentry.github.io/r-novice-inflammation/11-supp-read-write-csv.html).

Here, we will use the [readr](https://readr.tidyverse.org/) 
package from the *tidyverse*. First you need to install it:

```r
install.packages("readr")
```

Then load it:

```r
library(tidyverse)
```

Let's read the dataset:

```r
data <- read_csv("publications2024.csv")
```

**Read json data**

Inverted abstracts are stored in the JSON format which we already encountered
in the previous chapter. In R, you can read and write JSON using the 
[jsonlite](https://github.com/jeroen/jsonlite) library.

```r
install.packages("jsonlite")
library(jsonlite)
```

Let's read the inverted abstracts:

```r
abstracts_inverted <- read_json("abstracts_inverted.json")
```

To obtain the original abstracts, you need to process the data further.
More examples on how to work with JSON data in R, can be found 
[here](https://datacarpentry.github.io/r-socialsci/07-json).


::::::::::::::::::::::::::::::::::::::::::::::::

## Method 2: get data via API

::::::::::::::::::::::::::::::::::::::::: callout

For this part, we will need HTTP libraries for either Python or R.
We will use the most common libraries, but if you are already familiar with another, feel free to use those.

:::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: group-tab

### Python

First, we need to install the `requests` library:

```bash
pip install requests
```

Now, we can import both `requests` and the built-in library `json` to parse json
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

First, we need to install and load the [httr2](https://httr2.r-lib.org/articles/httr2.html) 
package:

```r
install.packages("httr2")
library(httr2)
```

`httr2` uses objects and you can use the pipe to build a request step-by-step.
We retrieve the data using our URL from before:

```r
# Prepare the request
req <- request("https://api.openalex.org/works?filter=institutions.ror:04dkp9463,publication_year:2024")

# Submit the request
resp <- req %>% req_perform()

# Retrieve data from the response
data <- resp %>% resp_body_json()
```

There is also an R library that simplifies using the OpenAlex API:
[openalexR](https://github.com/ropensci/openalexR). The library is well-documented
and its usage won't be covered in this workshop.

::::::::::::::::::::::::::::::::::::::::::::::::


