---
title: Authoring
subject: Preparing your submission
venue: Authoring
---

Submissions in the Notebooks Now! format can be prepared using either of two popular open-source toolchains [MyST Markdown](https://mystmd.org) and [Quarto](https://quarto.org). The submission system can recognize the configuration information of each tool and build the manuscript, PDFs and other publishing assets automatically.

```{note} Collaborative Open Source Development
:class: dropdown
During the Notebooks Now! initial phase, members of the teams behind MyST Markdown ([Executable Books](https://executablebooks.org), [Curvenote](https://curvenote.com)) and Quarto ([Posit](https://posit.co)) participated in a number of working groups, collaborating together and with others to converge on a common output format for notebook-based scientific articles.

This collaboration and the work by these groups has ensured that both toolchains can be used to create the correct assets required for modern notebook publishing. See [Notebooks in Publishing](https://notebooks_now.curve.space/jats) for details on that collaborative work.
```

## Authoring Content

Each toolchain has different Markdown flavors and authoring can be carried out in a variety of editors. For a full treatment, refer to the documentation for each tool ([MyST](https://mystmd.org/guide/quickstart-myst-documents), [Quarto](https://quarto.org/docs/manuscripts/)). Here we include a brief explanation of how to set up each tool and what to expect from the local editing experience in each case.

::::{tab-set}
:::{tab-item} MyST Markdown

Authoring with MyST Markdown relies on a command line tool `mystmd` and optionally (but highly recommended) a Jupyter Lab extension `jupyterlab-myst`.

🛠 To setup `mystmd`, run through the [installation instructions](https://mystmd.org/guide/quickstart).

🛠 To confirm your installation was successful, run:

```bash
myst -v
>> v1.1.37
```

🛠 To start the authoring environment and get a live preview of your manuscript in the browser, run (replace `my-nn-submission` with the name of your repository set up from the template):

```bash
cd my-nn-submission
myst start
```

```{figure} images/myst-browser-preview.png
A local preview of the sample paper from the submission template, displayed in the web browser using MyST.
```

:::
:::{tab-item} Quarto

🛠 To setup `quarto`, run through the [installation instructions](https://quarto.org/docs/manuscripts/).

The manuscript features are new in the upcoming Quarto 1.4 release.
To use the feature now, you’ll need to download and install the Quarto pre-release.

The [quarto documentation](https://quarto.org/docs/manuscripts/) has more instructions on getting setup with authoring.

```{figure} images/quarto-browser-preview.png
:class: framed
A local preview of the sample paper from the submission template, displayed in the web browser using Quarto.
```

:::
::::

As long as your development server is running changes to any `.md`, `.ipynb` or configuration files, all edits will be reflected immediately in the preview, giving you a view of your final manuscript that is updated in real time ⚡️. Make changes to any of these files using the editor or IDE of your choice.

## Adding Content

At this stage you're able to replace the sample template content with your own manuscript and notebooks.

The contents of `article.md` can also be replaced, but in doing so you should take note of the existing document structure (i.e. headings like data availability!).

In MyST, new files need to be added to the `_toc.yml` ([docs](https://mystmd.org/guide/table-of-contents)). In order to work on your notebooks reliably within the repository, you should also set up your [Execution Environment](./environment.md), which we'll cover in the next step.

### Frontmatter

At the top of `article.md` is a frontmatter section (delimited by `---`):

```yaml
---
# File metadata may be provided as frontmatter YAML
title: La Palma Seismicity 2021
description: Analysis of the seismic earthquake data during the eruption
date: 2021-11-10
license: CC-BY-4.0
---
```

Consider updating the existing frontmatter section to reflect your new submission's metadata. Learn more about valid frontmatter fields in [MyST](https://mystmd.org/guide/frontmatter) and [Quarto](https://quarto.org/docs/authoring/front-matter.html).

### Abstract

::::{tab-set}
:::{tab-item} MyST Markdown

In MyST Markdown, `parts` are blocks of content that have special roles and can be treated differently when the manuscript is displayed. In the sample content, a part is used to add the abstract to the manuscript with the following syntax.

```md
+++ { "part": "abstract" }

The abstract should begin with a short description
of the problem addressed, briefly describe the new data or analyses,
then briefly state the main conclusion(s) and how they are supported,
and address any uncertainty.

+++
```

Replace this with the abstract for your manuscript.

:::
:::{tab-item} Quarto

In Quarto, an abstract can be added to the frontmatter of your article. As abstracts are usually multiline, use the `: |` syntax in YAML to include your abstract.

```yaml
abstract: |
  The abstract should begin with a short description
  of the problem addressed, briefly describe the new data or analyses,
  then briefly state the main conclusion(s) and how they are supported,
  and address any uncertainty.
```

:::
::::

### References

Replace the contents of `references.bib` with `bibtex` for all of your citations. Usually, you can export a `bibtex` file directly from your reference management software. Once populated, it is easy to add citations to your manuscript using the `bibtex` tags.

You can also cite directly using a DOI and add multiple `.bib` files if you need them. Read more about [citations in MyST here](https://mystmd.org/guide/citations) and [citations in Quarto](https://quarto.org/docs/authoring/footnotes-and-citations).

## Writing in Jupyter Lab

Writing a manuscript can be easily achieved using any text editor. Working with notebooks themselves is best carried out in a Jupyter client such as Jupyter Lab. Both MyST and Quarto have a Jupyter Lab extensions.

::::{tab-set}
:::{tab-item} MyST Markdown
🛠 Install an extension using `pip install jupyterlab-myst`

To learn more about installing and using the extension, see [the tutorial](https://mystmd.org/guide/quickstart-jupyter-lab-myst).
:::
:::{tab-item} Quarto
🛠 Install an extension using `pip install jupyterlab-quarto`

To learn more about installing and using the extension, see [the instructions](https://quarto.org/docs/tools/jupyter-lab-extension.html).
:::
::::

The extensions enables MyST Markdown or Quarto to be used directly in the markdown cells of Notebooks, and shows a fast rendered preview of your documents. This means you can do a significant amount of your authoring in Jupyter Lab alone.

Next start Jupyter Lab for Notebook development:

🛠 open a new terminal and run:

```bash
cd my-nn-submission
jupyter lab
```

This will start Jupyter Lab in the same directory as your development server, which is desired, and any changes made to your notebooks in Jupyter Lab will be reflected immediately in your manuscript preview.

```{figure} images/jupyterlab-myst.webp
A Notebook with frontmatter and MyST Markdown rendered in Jupyter Lab.
```

## Next Steps

Now that you are able to add your content to the repository via your text editor or Jupyter Lab, it's time to think about setting up and codifying a local execution environment. [We'll cover that in the next step](environment), as this not only helps you work more reliably while you are authoring, but is essential in creating a fully reproducible execution environment that will work on any computer.
