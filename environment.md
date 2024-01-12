---
title: Reproducible Environment
subject: Preparing your submission
venue: Reproducible Environment
---

The power of using Notebooks for scholarly output is that they allow executable elements and provide further transparency on the research and how data were handled, generated, or processed, in a format that is increasingly being used for research. All data and computation may not be able to be easily replicated in all circumstances (e.g. running a global climate model with terabytes of data, processing confidential data, and many other situations). However, any steps toward capturing more of the information to reproduce research, and showing detailed, open methodologies are important and valuable. Full computational reproduction is ideal and should be the standard to aim for; however, this need not block progress in including more methods and data in the archived literature. Similarly, keeping computational workflows working can be challenging, especially when they are dependent on external data sources, resources, packages, or services.

The Notebooks Now! approach, following the guidance below, will allow any reader (or reviewer) to execute your notebook. The published (and peer-reviewed) version of the notebook will be hosted on a cloud system that is linked to, and can call, the BinderHub environment.

In addition to providing content and notebooks within your submission, you thus also need to provide the means for it to be run reproducibly, on any computer. This guide presents some immediate steps you can take to move in that direction, followed by further steps to finalize your submission and test it on a `binderhub` service.

## Dependencies

If you don't already work with virtual environments and codify your dependencies, then you'll need to start doing this for your submission.

If you already use virtual environments and requirement files as part of your working practices, then the suggestions below may go further than you're used to! The approach laid out here is aimed at recording fine-grained, pinned dependencies to minimize deprecated functionality over time.

### `python` and `pip`

`pip` and `pip-compile` from the `pip-tools` package should be used for dependency management. To do this, install `pip-tools` in your base python environment. This tool set is needed for development only, so there is no need to add it to the requirements for your reproducible environment.

:::{tip} Why `pip-compile`?
:class: dropdown

For more discussion on using `pip-compile` and why it's preferred, [see this article](https://modelpredict.com/wht-requirements-txt-is-not-enough).

:::

🛠 To install `pip-compile`, run:

```bash
pip install pip-tools
pip-compile --version
pip-compile, version 7.3.0
```

🛠 Next create a `requirements.in` file and add your python dependencies to it. Note that in the **full** template this file already exists and contains:

```txt
numpy
matplotlib
pandas
scipy
seaborn
altair
plotly
jupyterlab>=4.0.0
jupyterlab-myst>=2.0.0
```

🛠 To add or remove dependencies from your submission, you should edit `requirements.in` and then run `pip-compile`.

This will carry out dependency analysis and create or update the `requirements.txt` file with a full listing of dependencies and their pinned versions.

🛠 To setup your virtual environment, run:

```bash
python -m venv env
source env/bin/activate
which python
>> <current-folder>/env/bin/python
python -m pip install -r requirements.txt
```

Using this workflow for dependency management makes it easy to work locally as you write and develop but also automatically means a detailed, pinned dependency set is available for use on `binderhub` or on another researcher's computer.

```{important} What to commit to Git?
**Both the `requirements.in` and `requirements.txt` should be committed to the repository.** An `environment.yml` file **should not** be included as this will interfere with the use of the correct pinned dependencies from `requirements.txt`.
```

### `python` and `conda`/`mamba`

`conda` and `mamba` are other popular python package managers that usually work with an `environment.yml` file.

While it is possible to set up a `conda` environment from `requirements.txt` generated from `pip-compile`, in practice this can fail due to specific versions of dependencies resolved on `pip` not being available on `conda`'s channels. This is important from a long-term archiving perspective for your Notebook content.

## Additional Runtime Dependencies & Platform Considerations

Depending on your research work, `python` or high-level language dependencies may only represent a portion of the code needed to run your notebooks on another computer.

Also, the `binderhub` environment used to execute your notebooks for reviewers and readers will be a linux (Ubuntu) based machine, which may differ from your local environment.

You'll need to give careful thought to managing these dependencies and make use of the variety of files available in [REES](https://repo2docker.readthedocs.io/en/latest/configuration/index.html) to accomplish your configuration. In some cases it may be necessary to use a `Dockerfile` to achieve this, which is an advanced configuration.

Ultimately, the test of whether your submission repository is portable will be made when you attempt to [submit to the Notebooks Now! system](submitting), however you can also test the environment by attempting to launch your repository on the public [mybinder.org](https://mybinder.org) service.

## Data

It is possible to include data within your submission repository, but this is not recommended except for small or intermediate data files, on the order of a few 100's of KiloBytes or less. In general, these can be derived data sets that are optimized for the Notebook publication and environment. An example might be summary data of complex model output to support or generate an animation or interactive graphic. Indeed, most graphics in scholarly articles are based on such derived or summary data sets. Original data sets can and should still be incorporated as described below, and included as references.

Consider the following for original data:

Release of your data clearly and FAIRly
: Adding original data files only to the submission repository raises several issues: You are essentially making a public release, either via a public GitHub repository or via the publication assets that will be built from it. This complicates the license for the data and any reuse, as well as automated retrieval.
: Instead, any original data used within a notebook based submission should be made available in line with [FAIR Principles](https://www.go-fair.org/fair-principles/). It should ideally be released independently in a recognized data repository, with appropriate metadata and accessed via a DOI. This allows a unique license for the data, separate authorship, as well as optimized metadata, and it incorporates the data with other like data. Leading repositories provide curation. Other previously published data that you use should also be cited and included as a reference.

Data fetching is part of your reproducible workflow
: Where possible, and where the datasets are not prohibitively complex, write code to fetch and validate your data, and incorporate this into your workflow, or perhaps an embedded notebook. This code might be present directly in one of your Notebooks, or perhaps it's included in a script, documented in your repository's README file and invoked using the [`start` script hook provided by REES](https://repo2docker.readthedocs.io/en/latest/config_files.html#start-run-code-before-the-user-sessions-starts). In any case, to be portable and reproducible, you should include data fetching in your workflow. Many leading disciplinary repositories provide such access. In any case, include data citations and separate references for data sets you use in your Notebook research.

Publication Artifacts
: Once your manuscript and repository are submitted, publication artifacts are automatically built, used throughout the remainder of the publication's lifetime, and will eventually be archived. Including large datasets in your submission will increase the size of these files, which is highly ineffective. The NN submission system will limit the size of submissions and reject any that are too large.

Repository bloat
: Larger repositories are slower and more difficult to work with, adding and updating large data files, especially binary files can cause problems and you may hit repository size limits on GitHub even before making a submission.

```{note}
The discussion on this page was inspired by python package management and common practices used by python developers. If you're using another language, you'll need to translate some of this to how dependencies are managed in that language, however the overall principles of creating an appropriate environment using mechanisms set out in [REES](https://repo2docker.readthedocs.io/en/latest/specification.html) remain the same.
```
