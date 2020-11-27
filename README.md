# Notes-jekyll

This is a Jekyll template that is optimized to serve as a note-taking organizational tool.
Specifically, we can easily insert citations into Markdown (you heard that right, 
no LaTeX required here!) and render our notes on GitHub pages. The theme is based on 
[notetheme](https://github.com/dinhanhthi/notetheme) and has added 
[jekyll-scholar](https://github.com/inukshuk/jekyll-scholar) for citation management.

## Getting started

 - [Add papers](#how-to-add-or-view-papers) either manually or with a citation manager
 - [Take notes](#how-to-take-notes) in Markdown, as you typically would
 - [Push to GitHub](#deploy-to-github-pages) to use the GitHub action to automatically deploy the site.

Since the jekyll-scholar plugin doesn't work on GitHub pages, we provide a GitHub action to do it easily.

## How to add or view papers

If you want to interact with your bibliography via a citation manager, you can
easily use something like [BibDesk](https://bibdesk.sourceforge.io/) to keep track of papers.
For example, the references file under [_bibliography](_bibliography) is also 
linked in the root directory, and it could include links to papers in [papers](papers).
By default, we expect the name of the paper pdf to match the name of the citation 
(and BibDesk will do this automatically for you, this is called "AutoFile") and it's
suggested to do a format like `papers/%f{Cite Key}-%u%e`.

## How to take notes

Once you have your papers, you of course want to take notes!
So how can we turn a simple setup of a folder and bibtex file into a nice organizational
structure to take notes and easily cite references? The answer is to take advantage
of Jekyll, and provide a base container and suggested organization to take notes.
You can add references to [build.bib](build.bib), which is linked to the same file
in the [_bibliography](_bibliography) folder. These rederences will render on the front page,
and be available to cite anywhere in the site where you can write markdown.
While we could investigate solutions to run a web server and render a PDF, the simpler
approach of using Markdown will likely be more comfortable for users with different
editor preferences.

## Deploy to GitHub pages

When you push to the main branch, you will trigger a build defined as a [GitHub workflow](.github/workflows/build.yml)
that will deploy the site to GitHub pages.

## LICENSE

This code has inherited the original [LICENSE](LICENSE) that must be preserved
from the repositories where it originates from.

## TODO

- Need to add pdfs for each paper example
- We want to be able to click on a reference on any page and open the PDF
- We also want a link for each reference that shows all the places it's cited (harder)
- create usage guide
