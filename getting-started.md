---
title: Getting Started
subject: Preparing your submission
venue: Getting Started
description: A guide to preparing your submission, from initial repository setup, and suggested authoring workflows as well as final submission checks and using the submission system.
---

This guide will take you through the process of preparing your submission, from initial repository setup, through suggested authoring workflows to final submission checks and using the submission system.

Authors should be familiar with Notebooks, GitHub, and LaTeX.

You will use one of the templates available in the [Notebooks Now GitHub Organization](https://github.com/notebooks-now). There are templates for single notebook submissions ("lite") and Markdown based manuscript submissions with linked notebooks ("full") for each of the supported tool chains. The goal of these template repositories is to serve the same purpose as a $\LaTeX$ submission template: something that authors can copy, delete content, and replace with their notebooks, data and articles.

In this guide we will use the "full" template for MyST Markdown or Quarto as an example. The full templates allow for separate notebooks that are focused on several specific aspects – for example, creating a figure – and then the outputs of those notebooks are displayed in the scientific article ([](#articles-and-notebooks)).

:::{figure} ./images/articles-and-notebooks.png
:name: articles-and-notebooks
The purple and orange components, interactive figure or other computational outputs, are created in a computational notebook and subsequently displayed as a graphic in the presentation-focused version of the Notebook article.
:::

```{tip} Template Design
:class: dropdown

These notebooks are submission instruction notebooks, and should follow the following constraints:

Metadata
: Show all relevant metadata that is required for publishing.

Speed & Dependencies
: The instruction notebooks should be portable across different systems and be fast to run. These notebooks should be able to run easily on Binder.

Realistic, but simple
: The data and example content should resonate with a geoscientist, and also present a mix between submission instructions/features that are specific to AGU.

There are four different example repositories for Python-based content: first, with a single notebook as the paper (similar to many Earthcube submissions, but with simplified content); second, a markdown document with multiple associated notebooks that do different components of a scientific workflow (e.g. data-cleaning, interrogation, figure generation, etc.).

In this submission guide we have focussed on the "full" template as this gives the most freedom over the manuscript's narrative flow and avoids some of the difficulties encountered when trying to compose the whole paper in a single notebook file.

For more information on the single notebook approach see the "lite" templates in [Submission Templates](./templates.md).
```

## Step by step

Following the steps below will take you though the main aspects of preparing your submission.

1. [Repository Setup](setup) - clone a template and add your content
1. [Review Repository Structure](structure) - understand the repository contents, configuration files, where content is and how it is referenced
1. [Authoring](authoring) - write, develop notebooks and preview your changes with a brief introduction to each of the supported toolchains
1. [Computational Environment](environment) - define the computational environment for your submission, starting with dependency management while also considering overall reproducibility
1. [Pushing to GitHub](pdf-preview) - push changes to your remote repository and allow GitHub Actions to test and build your submission
1. [Add Metadata](metadata) - add machine readable scholarly and submission metadata to your project
1. Submission - Automated checks and final build
