---
title: Repository Setup
subject: Preparing your submission
venue: Repository Setup
---

Submission templates are available via the [Notebooks Now! GitHub Organisation (github.com/Notebooks-Now)](https://github.com/Notebooks-Now).

```{figure} images/agu-github-org.png

```

🛠 Select one of the **full** templates corresponding to the authoring tools you wish to use for your submission either MyST Markdown or Quarto.

- 🔗 [Notebooks-Now/submission-myst-full](https://github.com/Notebooks-Now/submission-myst-full)
- 🔗 [Notebooks-Now/submission-quarto-full](https://github.com/Notebooks-Now/submission-quarto-full)

🛠 To create your own submission repository on GitHub, click `Use This Template` and select `Create a new repository`

```{figure} images/myst-full-create-repo.png

```

🛠 Enter the details for your new repository

- Choose a unqiue name for the repository
- Add a meaningful description
- Mark the repository as **public** or **private**. Links to public repositories can be provided directly to the NN submission system, whilst private repositories will be submitted via a `.zip` file. Repositories on GitHub can be made public/private at a later time.

```{figure} images/create-repo-from-template.png

```

🪄 The new repository is now available in your GitHub account

```{figure} images/new-nn-repo.png

```

🛠 Make a local working copy of your repository

How you create a local clone of your repository depends on how you are used to working with `git`. Assuming that you are using the `git` command line and have `ssh` configured:

- copy the `ssh` clone URI from GitHub (as shown above)
- Open a terminal or command prompt and navigate to a suitable working folder
- run `git clone git@github.com:username/my-repo.git`, replacing the `git` URI with your own

```{tip} Working with git
:class: dropdown
Add some information on how to get started with git in different ways? command line, windows, codespaces
```

### Next step

You have created your own repository that you can start working in. The repository has example content, configuration files, an example executable environment and GitHub actions that automate preview builds of your content.

Next, [learn about the structure of the repository](structure) and how you can customize it to fit your submission.
