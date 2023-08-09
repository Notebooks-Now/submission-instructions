---
title: Submission Templates
subject: Reference
---

The repository is expected to contain a [Reproducible Executation Environment Specification (REES)](https://repo2docker.readthedocs.io/en/latest/specification.html), the configuration files for your [MyST Markdown](https://mystmd.org) or [Quarto](https://quarto.org) project and your content (`.md`/`.qmd`/`.ipynb`), code, images and data files. For more guidance on preparing content and data see [Portable Notebooks](portability).

The goal of these template repositories is to serve the same purpose as a $\LaTeX$ submission template: something that authors can copy, delete content, and replace with their notebooks, data and articles.

These notebooks are submission instruction notebooks, and should follow the following constraints:

Metadata
: Show all relevant metadata that is required for publishing.

Speed & Dependencies
: The instruction notebooks should be portable across different systems and be fast to run. These notebooks should be able to run easily on Binder.

Realistic, but simple
: The data and example content should resonate with a geoscientist, and also present a mix between submission instructions/features that are specific to AGU.

There are four different example repositories for Python-based content: first, with a single notebook as the paper (similar to many Earthcube submissions, but with simplified content); second, a markdown document with multiple associated notebooks that do different components of a scientific workflow (e.g. data-cleaning, interrogation, figure generation, etc.).
