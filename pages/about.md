---
layout: page
title: How do I take notes?
css: ["about.css", "animate.css", "morphext.css"]
js: ["morphext.min.js", "about.js"]
permalink: /about/
---

### Overview

This is a Jekyll template that will make it easy to:

1. Add references to `references.bib` and papers to the `papers` folder.
2. Create pages with notes and automatically render and cite references on any page.
3. Push to the main branch and trigger a build for GitHub pages
4. Search or otherwise interact with the interface

Each point is explained in more detail below.

#### 1. References

If you simply want to interact with the references here, the `references.bib` in the base
of the repository can be linked to the `papers` folder and you can open them in your citation
manager of choice. An example manager tool is [BibDesk](https://bibdesk.sourceforge.io/).
By default, you should expect the name of the paper pdf to match the name of the citation 
(and BibDesk will do this automatically for you, this is called "AutoFile") and it's
suggested to do a format like `papers/%f{Cite Key}`. You can also just add citations
and papers manually, it's up to you!

#### 2. How to take notes

Once you have your papers, you of course want to take notes! Basically, any post
that you write under `_posts` will render into a page of notes. Any reference
that you add to your references file will automatically render on the home page,
and can be easily read from here (not implemented yet) or referenced in any page.

The rederences will generally be available to cite anywhere in the site where you can write Markdown.
I chose this approach because I like writing in Markdown.
While we could investigate solutions to run a web server and render a PDF, the simpler
approach of using Markdown will likely be more comfortable for users with different
editor preferences.

##### Citations

The simplest thing you might want to do is cite something. For example,
if I type:

```
{% raw %}{% cite metz2011nonrigid %}{% endraw %}
```

If you want to cite a particular set of pages or lines, you can do:

```
{% raw %}{% cite metz2011nonrigid --locator 23-5 %}{% endraw %}
```

And then I can include the entire list of references, usually at the end of the page, as follows:

```
{% raw %}{% bibliography --cited %}{% endraw %}
```

You can remove the `--cited` to include all references, regardless of being mentioned or
not. And then I can easily render the citation {% cite hinsen2019dealing %}.
Or make a citation that references lines {% cite metz2011nonrigid --locator 23-5 %}.
You should be able to click either of those numbers and be taken to the references at the bottom.

##### References

In the same spirit as the above, you can print the reference for any particular citation
as follows:

```
{% raw %}{% reference metz2011nonrigid %}{% endraw %}
```

That renders to the following (and note the class is "citation" if you want to edit the
style):

{% reference metz2011nonrigid %}

##### Quotes

You might also want to quote text, verbatim. That might look like this, for the same
paper:

```
{% raw %}{% quote metz2011nonrigid %}
Lorem ipsum dolor sit amet, consectetur adipisicing elit,
sed do eiusmod tempor.

Lorem ipsum dolor sit amet, consectetur adipisicing.
{% endquote %}{% endraw %}
```

And here is the rendered version of that.

{% quote hinsen2019dealing %}
Lorem ipsum dolor sit amet, consectetur adipisicing elit,
sed do eiusmod tempor.

Lorem ipsum dolor sit amet, consectetur adipisicing.
{% endquote %}

{% bibliography --cited %}

More detail will be added here as the theme is developed!
