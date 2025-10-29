---
title: "Examples and exercises"
teaching: 5 # teaching time in minutes
exercises: 60 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 

- How can I apply this knowledge?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Explore, experiment, showcase

::::::::::::::::::::::::::::::::::::::::::::::::

We've covered the basics of what an API is, how to interact with it and looked 
at two API specifications. It is now time to put this knowledge into practice.
Below you'll find examples and links to language-specific scripts with GenAI use cases. We
also provide additional links for further exploration.

::::::::::::::::::::::::::::::::::::: discussion

In pairs or groups of 3, use the available data and try to come up with a generative
AI (research) application - if you feel comfortable enough you can start entirely from scratch,
otherwise, follow the example scripts. Possible outcomes can be tables, graphs, summaries, 
or small pieces of software (advanced).

::::::::::::::::::::::::::::::::::::::::::::::::

## Example 1: SDG classification

Our dataset contains both titles and abstracts of publications. A common task 
for a generative AI would be to assign topics to these publications, such as
[Sustainable Development Goals](https://sdgs.un.org/goals).

Since we have a finite set of labels (17 SDGs in total), we will be using
[structured outputs](https://platform.openai.com/docs/guides/structured-outputs)
to instruct the model to only return those labels as response, as opposed to 
a lengthy and possibly random reply.

The steps are therefore as follows:

- read a subset of publications (to save costs and time)
- define system and user prompts 
- define schema for structured outputs
- send requests and retrieve labels
- repeat for abstracts; since they are inverted, we need to pre-process them first

::::::::::::::::::::::::::::::::::::: group-tab

### Python

You can either develop a solution from scratch or follow 
[this notebook](https://github.com/paulmaxus/litellm-workflow/blob/main/structured.ipynb)

### R

You can either develop a solution from scratch or reuse 
[this script](https://github.com/paulmaxus/litellm-workflow/blob/main/structured.R)

::::::::::::::::::::::::::::::::::::::::::::::::

## Example 2: RAG

*Note: this is an advanced topic and requires additional reading and setup.*

[Retrieval-augmented generation (RAG)](https://en.wikipedia.org/wiki/Retrieval-augmented_generation) 
can be a powerful tool to generate more reliable output. By providing a set of
domain-specific documents, the LLM is able to query those documents before 
generating its answer to the user.

To implement RAG, you will need to use an embeddings model next to the LLM, e.g.
`text-embedding-ada-002`.

::::::::::::::::::::::::::::::::::::: group-tab

### Python

*LlamaIndex* can be used to implement RAG. Two resources that might be useful:

- [vector store](https://developers.llamaindex.ai/python/framework/module_guides/indexing/vector_store_index/#loading-data-into-the-index)
- [chat engine](https://developers.llamaindex.ai/python/framework/module_guides/deploying/chat_engines/usage_pattern#available-chat-modes)

**More**

[PandasAI](https://docs.pandas-ai.com/v3/getting-started) can be used to quickly
run inference on your pandas dataframes. You can follow the instructions on their
website. For research purposes, it is usually desirable to have more control over parameters,
for instance by using a library such as `requests`.

### R

[ragnar](https://ragnar.tidyverse.org/) is an R library to implement RAG.

**More**

Besides the more generic httr2 library, there are AI-specific libraries such as
[Ellmer](https://ellmer.tidyverse.org/) to interact with the API (and others).

::::::::::::::::::::::::::::::::::::::::::::::::
