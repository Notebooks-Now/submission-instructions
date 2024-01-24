---
title: Pushing to GitHub
subject: Preparing your submission
venue: Pushing to GitHub
---

The submission templates for both `MyST Markdown` and `Quarto` provide GitHub Actions workflows for automatic build and publishing of your submission as a website, including building of the PDF file and other publication artifacts.

This workflow will be run on repository creation and on every subsequent commit to the `main` branch. If you visit the `Actions` page for your repository then you may see something like this:

```{figure} images/github-failed-action.png

```

Where the first run is listed and marked as failing. In order to publish the preview of your manuscript as a website GitHub pages must be enabled on your repository.

::::{tab-set}
:::{tab-item} MyST Markdown

🛠 To enable GitHub pages, go to `Settings`, and select `Pages` from the left hand sidebar. Then set `Source` to `GitHub Actions`.

```{figure} images/github-enable-pages.png
Enable GitHub pages on your repository.
```
:::

:::{tab-item} Quarto

The template manuscript is configured with a GitHub Action in .github/workflows/publish.yml. This action is triggered when there is a push to the main branch; it renders your manuscript and puts the manuscript website source on the gh-pages branch.

🛠 To ensure the action has permission to write to the gh-pages branch, you’ll need to make one change to your repository settings. Go to your repository and navigate to: Settings > Actions > General > Workflow Permissions. Check the “Read and Write Permissions” box.

```{figure} images/quarto-github-action-setting.png
Enable proper workflow permissions for publishing
```

Once you have enabled these workflow permissions, use the `quarto publish` to publish your manuscript to Github pages. You will only need to do this once (any edits you make after this initial publication will automatically be published).

In the terminal, from the root of your manuscript project:

```bash
quarto publish
```

Select `Github Pages` from the list of publishing targets. After confirmation, your document will be rendered and published.

:::
::::



🛠 To trigger a rebuild push a new commit to `main`

A second workflow run will appear and after a time, will complete and turn green ✅.

```{figure} images/github-action-success.png
Add a new commit to the repository and the action should complete!
```

## Examining preview builds

Once the GitHub action successfully completes, the preview website for your article will be available at `https://<username>.github.io/<reponame>`. A preview of the sample content from the template looks like this.

```{figure} images/github-website-preview.png
Preview of your website using MyST Markdown.
```

You should see the primary (root) manuscript and be able to access all the notebooks and additional mardkown files under the `SUPPORTING DOCUMENTS` listing.

A draft PDF in AGU format can also be downloaded as well as the other publishing specific artifacts (JATS, MECA).

## Next Steps

These preview builds will be run each time you commit to `main` allowing you to share the draft URL with collaborators and examine the PDF output without having to convert to LaTeX and build your manuscript locally.

Once you're manuscript is ready the next step is to [submit to the Notebooks Now! system for final checking and acceptance](submitting).
