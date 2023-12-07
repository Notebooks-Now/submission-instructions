---
title: Publishing Computational Notebooks
subject: Overview
---

To enable compatibility and interoperability with the scholarly publication ecosystem, as well as scalable peer-review and reading and computation of notebooks, certain types and formats of notebooks are supported. Please use and follow the submission templates below in developing your computational notebook. Some guidance includes:

- Both Jupyter and R-Studio notebooks are supported. These will be standardized for publication using the tools Quarto and MyST and post-processed by Curvenote.
  - This processing includes transforming the text into HTML, PDF, LaTeX, and JATS-XML formats, creating a standard file package for interoperability with the peer review and publication systems, and collating the metadata into a standard XML format.
- Your notebooks should tell the story of your research in the same way as a text-based publication.
  - It should contain all common elements and metadata of a text-based publication—like titles, authors, abstract, acknowledgments, references, etc.
  - It can also contain many elements that make computational notebooks powerful and that provide richer information about the research such as: code, datasets, dynamic figures, and other embedded notebooks.
  - The templates provide further guidance.
- The full notebooks will be available for peer-reviewers, as well as any reader once published.
- The text in the notebooks can also be transformed to HTML and PDF views. These will also be available to reviewers and readers, including at the home page of the journal.

### Computations and Data

- Any computations in the publication notebook should be able to be run in a typical binder environment by readers (and reviewers). The templates provide guidance. This means that, in telling the story of your research, you can include in your notebook datasets and codes that are supported and can run in reasonable time (for a reader) in this environment.
- Complex or large datasets and models or model output may need to be appropriately abstracted in the publication Notebook (for example, via a summary data set); the full datasets and models should be cited in the text, included as data or software citations in the references, and linked. Other linked notebooks can be included as well; these are not all expected to be enabled in the binder environment.
- New data or data compilations should also be formally deposited in an appropriate FAIR-enabled repository. The best repositories are those that provide curation for that type of data. Significant new code should also be archived and cited using best practices for software citation.

### Published Notebooks

- Currently published notebooks will be a specific article type in selected AGU Journals. This model can be easily adopted by other journals and publishers.
- The published notebook will be considered as an archival record. Further changes will be “locked,” requiring an erratum or correction.
- The text of the notebook will be copy edited and proofed as usual by the journal.
- The notebook and journal article will receive a single DOI that will resolve to the Notebook landing page (with a link back to the journal article). An HTML and PDF view is supported also on the Notebook landing page. The journal view will provide an immediate link to the Notebook.
- The Notebook will be included in the Journal contents and will be indexed in downstream services that provide a record of that journal (MedLine, ADS, ACS abstracts, GeoRef, Web of Science, Scopes, etc). If authors include their ORCID, they will receive a publication record automatically after publication.
- All Notebooks will be published under a mixed open license, where the text is under a CC-BY license, data are under a CC0 license, and code is under an open software license. Further information is in the templates.

Submitting and Hosting Notebooks
Curvenote is providing the platform for Notebook submission, peer review, and publication. Please submit the notebook to this platform using the link below. This platform will:

- Provide integrity checks to ensure that the notebook is formatted correctly.
- Automatically execute the notebook on demand
- At submission, check that it executes successfully.
- After all checks are completed, it will automatically pass necessary metadata and files (LaTeX and PDF) to start and complete much of a submission into the peer review system for an AGU journal.
- The corresponding author will need to log into the AGU system to complete the submission.
- A link in the peer review system will provide secure access to the notebook for reviewers.

## Submission Templates

Submissions are made by either providing a link to a public github repository or uploading a `.zip` file with the contents of your private repository. Although it's possible to put together your own repository with the minimum requirements for submission, there are a number of template repositories available as a starting point.

:::{card} Getting Started 🚀
:link: getting-started.md
To start with your submission using a template follow the Getting Started Guide.
:::
