---
title: "LiteLLM API"
teaching: 10 # teaching time in minutes
exercises: 2 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 

- What can I use the API for?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand the API endpoints
- Understand how requests are made

::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::: callout

In this episode, we will be working with the LiteLLM proxy server.
This infrastructure setup is specific to the University of Amsterdam.
However, if your institution uses LiteLLM as well, you should be able to follow
these instructions, too.

::::::::::::::::::::::::::::::::::::::::::::::::

## Overview

The API can be reached at https://ai-research-proxy.azurewebsites.net/

When you open the link in a browser, what you'll see is the so called 
[Swagger UI](https://github.com/swagger-api/swagger-ui), a user interface
that lists all of the API's endpoints, and allows you to test those, as long as
you have an API key.

Note that the list is quite long, but that most of those are not relevant
for this workshop and for most research purposes either.

:::::::::::::::::::::::::::::::::::::::: callout
For this part of the workshop, you'll need a working API key.
::::::::::::::::::::::::::::::::::::::::::::::::


## Using Swagger UI

In order to explore and test the available API endpoints, the Swagger UI is 
an ideal starting point. To be able to execute requests, you need to authorize
first (top right button) by inserting your API key.

Let's have a look at a simple GET request using `/models`:

We don't need to pass any data, simply press `Execute`. The status code of
our request should be `200` and the response body should contain a list of 
available models like this:

```json
{
  "data": [
    {
      "id": "gpt-4",
      "object": "model",
      "created": 1677610602,
      "owned_by": "openai"
    },
    {
      "id": "text-embedding-ada-002",
      "object": "model",
      "created": 1677610602,
      "owned_by": "openai"
    },
    {
      "id": "gpt-4.1",
      "object": "model",
      "created": 1677610602,
      "owned_by": "openai"
    },
    {
      "id": "Llama-3.3-70B-Instruct",
      "object": "model",
      "created": 1677610602,
      "owned_by": "openai"
    }
  ]
}
```

This information is handy once we start sending input text as we need to specify
the exact model to use.


## Using Python and R

In the previous episode, we installed and used the `requests` (Python) and 
`httr2` (R) libraries. We will now use those again to make requests to the
LiteLLM API.

Since it is now necessary to authorize ourselves using an API key, we need to 
send additional information to the server, so called 
[headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers).
In essence, we are specifying that we are going to send JSON data and that we
would like to receive JSON data as well. We are also sending the API key with 
each request so that the server is able to authorize us.

::::::::::::::::::::::::::::::::::::: group-tab

### Python

We first need to import the requests and json module.

```python
import requests
import json
```

Let's now set the headers:

```python
api_key = ""  # make sure to never expose this key to the public

headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
    "Authorization": f"Bearer {api_key}"
}
```

We can now repeat the request to `/models`, this time using Python:

```python
url = "https://ai-research-proxy.azurewebsites.net/models"

response = requests.get(url=url, headers=headers)

data = response.json()

for model in data.get("data"):
    print(model.get("id"))
```

We can now use one of these models to process our text input / prompt:

```python
prompt = ""  # insert a prompt
data = {
    "model": "gpt-4o-mini",
    "messages": [
        {"role": "user", "content": prompt}
    ]
}
response = requests.post(url=url, data=json.dumps(data), headers=headers)
```

Notice that we are now using `requests.post()` instead of `requests.get()`
since we are sending data to the server.

### R



::::::::::::::::::::::::::::::::::::::::::::::::



