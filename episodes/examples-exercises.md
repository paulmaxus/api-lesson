---
title: "Examples and exercises"
teaching: 10 # teaching time in minutes
exercises: 2 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 

- How can I apply this knowledge?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Explore, experiment, showcase

::::::::::::::::::::::::::::::::::::::::::::::::

We've covered the basics of what an API is, how to interact with it and two
specific API specifications. It is now time to put this knowledge into practice.
Below you'll find (1) some general ideas for what to use LiteLLM for. (2) we provide
language-specific approaches and techniques such as using PandasAI to apply
inference on the dataset directly, or specific endpoints to explore, such as
`embeddings`.

::::::::::::::::::::::::::::::::::::: discussion

In pairs or groups of 3, use the available data to come up with a generative
AI research application. See below for examples. Possible outcomes are graphs,
summaries, or small pieces of software (advanced). Ideally, you can share these
outcomes with the other workshop participants at the end of the exercise.

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: group-tab

### Python

**Example 1: SDG classification using titles**

We read a subset of publications and abstracts, and use structured outputs
to retrieve labels for publication titles and abstracts. You can find the code
[here](https://github.com/paulmaxus/litellm-workflow/blob/main/sdg.ipynb).

**Example 2: Embeddings**

TODO

**More**

[PandasAI](https://docs.pandas-ai.com/v3/getting-started) can be used to quickly
run inference on your pandas dataframes. You can follow the instructions on their
website. For research purposes, it is usually desirable to have more control over parameters,
for instance by using a library such as `requests`.

### R

TODO

::::::::::::::::::::::::::::::::::::::::::::::::
