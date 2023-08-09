---
title: Repository Structure
subject: Preparing your submission
venue: Repository Structure
---

A submission repository has a number of expected configuration files, content files and folders dependent on the authoring toolchain used, and if based on a template repository, will also contain GitHub Actions workflows.

Let's review and get familar with the various elements.

## Toolchain specific elements

::::{tab-set}
:::{tab-item} MyST Markdown

```{code-block} bash
:caption: Layout of a MyST Markdown based submission repository, in this case generated from the [`submission-myst-full`](https://github.com/Notebooks-Now/submission-myst-full) template.
:linenos:
:emphasize-lines: 4,7,9,12,19
.
├── .github
│   └── workflows
│       └── deploy.yml
├── .gitignore
├── README.md
├── _toc.yml
├── article.md
├── data
│   ├── catalogoComunSV_1663233588717.csv
│   └── lapalma_ign.csv
├── environment.yml
├── images
│   ├── banner.png
│   ├── la-palma-eruption-2022-paper.png
│   ├── la-palma-map.png
│   ├── reservoirs.png
│   └── stations.png
├── myst.yml
├── notebooks
│   ├── data-screening.ipynb
│   ├── seismic-monitoring.md
│   └── visualization-figure-creation-seaborn.ipynb
└── references.bib
```

**MyST Markdown specific elements**

`myst.yml`
: The main MyST configuration file - this configures the MyST project and [web based paper](https://mystmd.org/guide/quickstart-myst-websites#configuration) and is the place to add [frontmatter](https://mystmd.org/guide/frontmatter) including all scholarly metadata.

`_toc.yml`
: The table of contents definition file - this allows you to identify the root article (in this case `article.md`) and control the order that items appear in the table of contents. It is also possible to group items but groups may not be displayed in all web based themes. For help on customizing this see the [Table of Contents](https://mystmd.org/guide/table-of-contents) in the MyST documentation.

:::
:::{tab-item} Quarto

```{code-block}
:caption: Layout of a Quarto based submission repository, in this case generated from the [`submission-quarto-full`](https://github.com/Notebooks-Now/submission-quarto-full) template.
:linenos:
:emphasize-lines: 4,8,22,23,28,38
.
├── .github
│   └── workflows
│       └── publish.yml
├── .gitignore
├── .luarc.json
├── README.md
├── _extensions
│   └── quarto-journals
│       └── agu
│           ├── _extension.yml
│           ├── agu.lua
│           ├── agujournal2019.cls
│           ├── american-geophysical-union.csl
│           ├── partials
│           │   ├── _affiliations.tex
│           │   ├── _authors.tex
│           │   ├── _corresponding-author.tex
│           │   ├── before-body.tex
│           │   └── title.tex
│           └── trackchanges.sty
├── _quarto.yml
├── apt.txt
├── article.qmd
├── data
│   ├── catalogoComunSV_1663233588717.csv
│   └── lapalma_ign.csv
├── environment.yml
├── images
│   ├── la-palma-eruption-2022-paper.png
│   ├── la-palma-map.png
│   ├── reservoirs.png
│   └── stations.png
├── notebooks
│   ├── data-screening.ipynb
│   ├── seismic-monitoring-stations.qmd
│   └── visualization-figure-creation-seaborn.ipynb
├── postBuild
└── references.bib
```

**Quarto specific elements**

`_quarto.yml`
: The main Quarto project configuration file.

`_extensions`
: Project specific Quarto extensions - in this case providing the Quarto LaTeX template for exporting the project to a PDF in AGU journal format.

`apt.txt`
: Part of the reproducible environment configuration - installs `zip` and `jq` system dependencies.

`postBuild`
: Part of the reproducible environment configuration - installs `quarto` and `tinytex` as system dependencies.

:::
::::

## Common elements

The following elements are present independent of the authoring toolchain used in your submission.

`.github/workflows/*.yml`
: A [GitHub Actions]() deployment workflow that will attempt to build your submission on each push to your `main` branch. Learn more in [Pushing to GitHub](push-to-github). Normally, this file should not be changed.

`environment.yml`
: The template repositories use a standard `conda` environment file for loading python dependencies. If you are using `python` and `conda` then we describe updating this file in [Environment](environment) otherwise any set of [Reproducible Execution Environment Specification (REES)](reproducible environments) files can be used to configure your repository as needed. REES ensures that any `binderhub` instance can provide a properly configured Jupyter server with required dependencies to reviewers and readers. (Note: the Quarto templates already include an additional REES files `apt.txt`, `postBuild`),

`data/`
: Whether to provide data files directly in your submission repository should be carefully considered versus publishing these separately in a suitable data repository. For more on this topic see [Best Practices](best-practices).

`.gitignore`
: A standard git ignore file allowing you to exclude local files from your submission. This is useful if your scripts or notebooks generate additional temporary files when they are run, for example downloaded data files, temporary result files. Customize this file to fit your needs [by adding ignore patters](https://git-scm.com/docs/gitignore).

## Content

The image below shows the sample content and toolchain specific configuration files included in the repository.

::::{tab-set}
:::{tab-item} MyST Markdown

```{code-block}
:caption: Markdown (`.md`) and notebook (`.ipynb`) content alongside MyST Markdown specific configuration files.
:linenos:
:emphasize-lines: 3,4,11,15
.
├── _toc.yml
├── article.md
├── images
│   ├── banner.png
│   ├── la-palma-eruption-2022-paper.png
│   ├── la-palma-map.png
│   ├── reservoirs.png
│   └── stations.png
├── myst.yml
├── notebooks
│   ├── data-screening.ipynb
│   ├── seismic-monitoring.md
│   └── visualization-figure-creation-seaborn.ipynb
└── references.bib
```

:::
:::{tab-item} Quarto

```{code-block}
:caption: Markdown (`.qmd`) and notebook (`.ipynb`) content alongside Quarto specific configuration files.
:linenos:
:emphasize-lines: 5,9,14,19
.
├── .luarc.json
├── README.md
├── _quarto.yml
├── article.qmd
├── data
│ ├── catalogoComunSV_1663233588717.csv
│ └── lapalma_ign.csv
├── images
│ ├── la-palma-eruption-2022-paper.png
│ ├── la-palma-map.png
│ ├── reservoirs.png
│ └── stations.png
├── notebooks
│ ├── data-screening.ipynb
│ ├── seismic-monitoring-stations.qmd
│ └── visualization-figure-creation-seaborn.ipynb
├── postBuild
└── references.bib
```

:::
::::

With both toolchains:

`references.bib`
: References are provided in standard `bibtex` in a single file at the root of the repository. If you intend to rename this file, refer to your authoring tool's documentation.

`images/`, `notebooks/`
: You are free to organize images, notebooks, scripts and other data files within the repository as needed and reference these as normal from markdown or `ipynb` files, or otherwise use them as supported by the authoring tool that you are using.

`article.(md/qmd)`
: This markdown file at the root of the repository is the main manuscript that references and links to the other notebooks in the repository. The filename is not fixed, but if changed the configuration files for the authoring tool should be updated appropriately.

## Next Steps

Now that you are familar with the contents of your repository, let's look at [the authoring environment](authoring) available for each toolchain and understand how to work locally with your content.
