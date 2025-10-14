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
Below you'll find links to language-specific scripts with GenAI use cases. We
also provide additional links for further reading.

::::::::::::::::::::::::::::::::::::: discussion

In pairs or groups of 3, use the available data to come up with a generative
AI (research) application - possible outcomes can be tables, graphs, summaries, 
or small pieces of software (advanced). Ideally, you can share these
outcomes with the other workshop participants at the end of the exercise.

::::::::::::::::::::::::::::::::::::::::::::::::

**Example 1: SDG classification**

We read a subset of publications and abstracts, and use structured outputs
to retrieve labels for publication titles and abstracts.

**Example 2: RAGs**

[Retrieval-augmented generation (RAG)](https://en.wikipedia.org/wiki/Retrieval-augmented_generation) 
can be a powerful tool to generate more reliable output. By providing a set of
domain-specific documents, the LLM is able to query those documents before 
generating its answer to the user.

To implement RAG, you will need to use an embeddings model next to the LLM, e.g.
`text-embedding-ada-002`.

::::::::::::::::::::::::::::::::::::: group-tab

### Python

SDG classification:

- [code](https://github.com/paulmaxus/litellm-workflow/blob/main/structured.ipynb)

RAG (LlamaIndex):

- [vector store](https://developers.llamaindex.ai/python/framework/module_guides/indexing/vector_store_index/#loading-data-into-the-index)
- [chat engine](https://developers.llamaindex.ai/python/framework/module_guides/deploying/chat_engines/usage_pattern#available-chat-modes)

**More**

[PandasAI](https://docs.pandas-ai.com/v3/getting-started) can be used to quickly
run inference on your pandas dataframes. You can follow the instructions on their
website. For research purposes, it is usually desirable to have more control over parameters,
for instance by using a library such as `requests`.

### R

SDG classification:

- [code](https://github.com/paulmaxus/litellm-workflow/blob/main/structured.R)

RAG:

- [ragnar](https://ragnar.tidyverse.org/)

**More**

Besides the more generic httr2 library, there are AI-specific libraries such as
[Ellmer](https://ellmer.tidyverse.org/) to interact with the API (and others).

::::::::::::::::::::::::::::::::::::::::::::::::
