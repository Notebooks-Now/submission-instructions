---
title: Reproducible Environment
subject: Preparing your submission
venue: Reproducible Environment
---

In addition to providing content and notebooks within your submission, you also need to provide the means for it to be run reproducibly, on any computer. There are some immediate steps the you should take to move in that direction, followed by further steps to finalize your submission and test it on a `binderhub` service.

## Dependencies

If you don't already work with virtual environments and codify your dependencies, then you'll need to start doing this for your submission.

If you already use virtual environments and requirement files as part of your working practices, then the suggestions below may go further than you're used to! The approach laid out here are aimed at recording fine-grained, pinned dependencies to avoid dependency problems over time.

### `python` and `pip`

`pip` and `pip-compile` from the `pip-tools` package should be used for dependency management. To do this install `pip-tools` in your base python environment, it's needed for development only, so there is no need to add it to the requirements for your reproducible environment.

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

🛠 Next create a `requirements.in` file and add your python dependencies to it, in the **full** template this file already exists and contains:

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

🛠 To add or remove dependencies from your submission you should edit `requirements.in` and then run `pip-compile`.

This will carry out dependency analysis and (create or) update the `requirements.txt` file with a full listing of dependencies and their pinned versions.

🛠 To setup your virtual environment, run:

```bash
python -m venv env
source env/bin/activate
which python
>> <current-folder>/env/bin/python
python -m pip install -r requirements.txt
```

Using this workflow for dependency management makes it easy to work locally as you write and develop but also automatically means a detailed, pinned dependency set is available for use on `binderhub` or on reader's computer.

```{important}
**Both the `requirements.in` and `requirements.txt` should be committed to the repository.** An `environment.yml` file **should not** be included as this will interfere with the use of the correct pinned dependencies from `requirements.txt`.
```

### `python` and `conda`/`mamba`

`conda` and `mamba` are other popular python package managers that usually work with an `environment.yml` file.

As there is no equivalent to `pip-compile` in these managers, submissions should still adhere to using a `requirements.in`/`requirements.txt` file as outlined above for dependency management.

While it is possible to setup a `conda` environment from `requirements.txt` generated from `pip-compile` in practice this can fail due to specific versions of dependencies resolved on `pip` not being available on `conda`'s channels.

For this reason we support the `pip` and `requirements.[in/txt]` method only.

## Additional Runtime Dependencies & Platform Considerations

Depending on your research work, `python` or high level language dependencies may only be only represent a portion of the code needed to run your notebooks another computer.

Also, the `binderhub` used to execute your notebooks for reviewers and readers will be a linux (Ubuntu) based machine, which may differ from your local environment.

You'll need to give careful thought to managing these dependencies and make use of the variety of files available in [REES](https://repo2docker.readthedocs.io/en/latest/configuration/index.html) to accomplish your configuration. In some cases it may be necessary to use a `Dockerfile` to acheive this, which is advanced configuration.

Ultimately, the test of whether your submission repository is portable will be made when you attempt to [submit to the Notebooks Now! system](submitting), however you can also test the environment by attempting to launch your repository on the public [mybinder.org](https://mybinder.org) service.

## Data

It is possible to include data within your submission repository but this is not recommended except for the smallest of **intermediate** data files, of the order of a few 100's of KiloBytes or less, and not recommended in any case for original unprocessed data.

Consider the following:

Release of your data clearly and FAIRly
: By adding your data files to the subission repository you are essentially making a public release, either via a public GitHub repository or via the publication assets that will be built from it. At that point what happens to you data? under which license or permissions is it released? How can it be used and how is it structured? Any data used within a notebook based submission should be made available in line with [FAIR Principles](https://www.go-fair.org/fair-principles/), ideally released independently in a recognized data repository, with appropraite metadata and accessed via a DOI.

Data fetching is part of your reproducible workflow
: Write code to fetch and validate your data and incorporate this into your workflow. This code might be present directly in one of your Notebooks, or perhaps it's included in a script, documented in your repository's README file and invoked using the [`start` script hook provided by REES](https://repo2docker.readthedocs.io/en/latest/config_files.html#start-run-code-before-the-user-sessions-starts). In any case, to be portable and reproducible you must include data fetching in your workflow.

How much data is needed?
: The goal of a Notebooks Now! submission is not to strive towards fully reproducible science, which may be unattainable in many circumstances. The goal instead is to provide compelling, valuable research articles that can be reproduced and readily built upon. Research articles may even be specifically crafted to enable exploration and interactive control over result and other data, as well a providing hard conclusions and traditional figures. This may be acheived using intermediate processed data, or precomputed output data over a number of variables instead of the full source dataset. The goal should be improved communication of the science using the Notebook format and reproducibility here means that the article will function on a standalone computer and for the foreseeable future.

Publication Artifacts
: Once your manuscript and repository is submitted, publication artifacts are automatically built, used throughout the remainder of the publication's lifetime and will eventually be archived. Including large datasets in your subission will increase the size of these file, which is highly ineffective. The NN submission system will limits the size of submissions and reject any that are too large.

Repository bloat
: Larger repositories are slower and more difficult to work with, adding and updating large data files, especially binary files can cause problems and you may hit repository size limits on GitHub even before making a submission.

```{note}
The discussion on this page was inspired by python package management and common practices used by python developers. If you're using another language you'll need to translate some of this to how dependencies are managed in that language, however the overall principles of creating an appropraite environment using mechanisms set out in [REES](https://repo2docker.readthedocs.io/en/latest/specification.html) remain the same.
```
