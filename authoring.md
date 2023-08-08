---
title: Authoring & Preview
subject: Preparing your submission
venue: Authoring & Preview
---

Submissions in the Notebooks Now! formatcan be prepared using either of two popular open source toolchains [MyST Markdown](https://mystmd.org) and [Quarto](https://quarto.org). The submission system can recognise the configuration information of each tool and build the manuscript, PDFs and other publishing assets automatically.

```{note} Collaborative Open Source Development
:class: dropdown
During the Notebooks Now! initial phase members of the teams behind MyST Markdown ([Executable Books](https://executablebooks.org), [Curvenote](https://curvenote.com)) and Quarto ([Posit](https://posit.co)) participated in a number of working groups, collaborating together and with others to converge on a common output format for notebook based scientific articles.

This collaboration and the work by these groups has ensured that both toolchains can be used to create the correct assets required for modern notebook publishing. See [Notebooks in Publishing](https://notebooks_now.curve.space/jats) for details on that collaborative work.
```

Each toolchain has different Markdown flavours and authoring can be carried out in a variety editors, for a full treatment see refer to the documentation for each tool. Here we include a brief explanation of how to setup and what to expect from the local editing experience in each case.

## Authoring with MyST Markdown

Authoring with MyST Markdown relies on a command line tool `mystmd` and optionally (but highly recommended) a Jupyter Lab extension `jupyterlab-myst`.

🛠 To setup `mystmd`, run through the [installation instructions](https://mystmd.org/guide/quickstart).

🛠 To confirm your installation was successfull, run:

```bash
node -v
>> v16.18.1
```

and

```bash
mystmd -v
>> v1.1.9
```

🛠 To start the authoring environment and get a live preview of your manuscript in the browser, run:

```bash
cd my-nn-submission
myst start
```

You should see build messages and a message that your development server has started.

```bash
...
📖 Built index.md in 45 ms.
📖 Built setup.md in 38 ms.
📖 Built submitting.md in 23 ms.
📚 Built 13 pages for project in 146 ms.


        ✨✨✨  Starting Book Theme  ✨✨✨



🔌 Server started on port 3000!  🥳 🎉


        👉  http://localhost:3000  👈

```

Open the link shown (e.g. http://localhost:3000) in your browser to preview your site.

```{figure} images/myst-browser-preview.png
A local preview of the sample paper from the submission template, displayed in the web browser.
```

As long as your development server is running changes to any `.md`, `.ipynb` or configuration files will be reflected immediately in the preview, giving your a view on your final manuscript that is updated in real time ⚡️. Make changes to any of these files using the editor or IDE of your choice.

### Jupyter Lab

Writing a manuscript in MyST Markdown can be easily acheived uing any text editor, and the uncluttered experience of a simple editor is often preferred when writing. Workign with notebooks themselves is best carried out in a Jupyter client such as Jupyter Lab.

🛠 To start Jupyter Lab for Notebook development, open a new terminal and run:

```bash
cd my-nn-submission
jupyter lab
```

This will start Jupyter Lab in the same directory as your development server, which is desired and any changes made to your notebooks in Jupyter Lab will be reflected immediately in your manuscript preview. Note: This works equally well with the classic Juypter notebook interface.

#### MyST extension for Jupyter Lab

The authoring experience with Jupyter Lab can be significantly improved by installing the `jupyterlab-myst` extension. This enables MyST Markdown used directly in the markdown cells with Notebooks to be rendered correctly, adds syntax highighting for MyST in `.md` files and adds a (currently limited) fast preview of MyST Markdown files. This means you can do a significant amount of your authoring in Jupyter Lab alone.

```{figure} images/jupyterlab-myst.webp
A Notebook with frontmatter and MyST Markdown rendered in Jupyter Lab.
```

🛠 To learn more about installing and using the extension, see [the tutorial](https://mystmd.org/guide/quickstart-jupyter-lab-myst)

### Adding your content

At this stage you're able to replace the sample template content with your own manuscript and notebooks.

The contents of `article.md` can also be replaced but in doing so you should take note of some of the existing structure in there.

As you add and remove files update the `_toc.yml` file to include and organise new source files. In order to work on your notebooks reliablt within the repository you should also setup your [Execution Environment](environment), which we'll cover in the next step.

#### Frontmatter

At the top of `article.md` is a frontmatter section (delimited by `---`):

```yaml
---
# File metadata may be provided as frontmatter YAML
title: La Palma Seismicity 2021
subtitle: An analysis of earthquake swarms in relation to the 2021 eruption
description: Analysis of the seismic earthquake data during the eruption
date: 2021-11-10
tags:
  - volcano
  - seismicity
  - la-palma
thumbnail: images/la-palma-eruption-2022-paper.png
---
```

Consider updating the existing frontmatter section to reflect you new submission's metadata. Learn more about [valid frontmatter fields here](https://mystmd.org/guide/frontmatter).

#### Abstract & Parts

In MyST Markdown, `parts` are blocks of content that have special roles and can be treated differently when the manuscript is displayed. In the sample content, a part is used to add the abstract to the manuscript wiith the following syntax.

```md
+++ {"part":"abstract"}

% The article should include an abstract block at the beginning. The block is delimited by `+++` before and after, and you must specify `"part": "abstract"` as JSON metadata on the block opener. This metadata is required for recognizing the content of this cell as the abstract.
% The abstract should begin with a short description of the problem addressed, briefly describe the new data or analyses, then briefly state the main conclusion(s) and how they are supported, and address any uncertainty.

+++
```

Replace this with the abstract for your manuscript.

#### References

Replace the contents of `references.bib` with `bibtex` for all of your citations. Usually, you can export a `bibtex` file directly from your reference management software. Once populated it is easy to add citations to you manuscript using the `bibtex` tags.

You can also cite directly using a DOI and add multiple `.bib` files if you need them. Read more about [citations in MyST here](https://mystmd.org/guide/citations).

## Authoring with Quarto

```{note}
Contributions Welcome!
```

## Next Steps

Now that your able to add your content to the repository via your text editor or Jupyter Lab, it's time to think about your setting up and codifying a local execution environment. [We'll cover that in the next step](environment) as this not only helps you work more reliably whilst you are authoring, but is essential in creating a fully reproducible execution environment that will work on any computer.
