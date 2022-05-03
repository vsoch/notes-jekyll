---
title: How to write notes
categories: [notes-jekyll]
tags: [jekyll]
datacamp: 1
maths: 1
toc: 1
---

{% include toc.html %}

## Front Matter

[Front matter](https://jekyllrb.com/docs/frontmatter/) refers to the section of text at the top of a posts file.
For example:

~~~ {% raw %}
---
layout: post
title: How to use NoteTheme?
---
{% endraw %} ~~~

The following components are included:

- `maths: 1` add this if you want to use mathematical expression in the post.
- `toc: 1` if you want to display a table of contents on the left sidebar
- `datacamp: 1` if you want to embed a datacamp interactive code question (see below)
- `categories: [notetheme,jekyll]` add category you want
- `tags: [notetheme,jekyll,code]` add tag you want
- `date: 2018-08-21` if you update the post, write the updated date


## Code

### Syntax highlighting

You can insert any block of code you want with a syntax highlight effect like below

Available languages : `ruby`, `python`, `c`, `matlab`, `latex`, `html`, `css`, `javascript`.

~~~ {%raw%}
{% highlight ruby %}

{% endhighlight %}
{% endraw %} ~~~

For example, **Python** with **line numbering**,

~~~ {%raw%}
{% highlight python linenos %}

{% endhighlight %}
{% endraw %} ~~~

or something appears in the command line window like this
<div class="terminal" markdown="1">
`$ sudo apt-get update`
</div>
by using
~~~ html
<div class="terminal" markdown="1">
`$ sudo apt-get update`
</div>
~~~


### Keyboard

You can also insert a keyboard key like this <kbd>Ctrl</kbd> + <kbd>B</kbd>, just use `<kbd>Ctrl</kbd>`.

## Insert a figure

### Standard

~~~ {% raw %}
![](/link/to/figure/){:.w-500 .no-border}
{% endraw %} ~~~

<div class="thi-colums" markdown="1">
- `no-border`: remove the border around figure
- `w-300`: reduce the size of image to maximum `300px` (if the screen's maximum size is `500px`, the figure's size will be `100%` the size of the screen). You can change the number `3` in `300` by other numbers `2,4,5,6,7,8,10` or something like `w-150`.
</div>

### Inline

~~~ {% raw %}
{% include img-inline.html content="/link/to/figure/" %}
{% endraw %} ~~~

## Insert an video from Youtube

Determine the youtube video's url, like this

~~~
https://www.youtube.com/watch?v=wIsK4kQTrIg
~~~

Choose `wIsK4kQTrIg` and put it inside below code

~~~ {% raw %}
{% include youtube.html content="wIsK4kQTrIg" size="5" %}
{% endraw %} ~~~

In that, `5` represents the percent your youtube container width in comparison with the page's width, for example, `5` means "50%". You can choose any integer number between `3` and `10`. This size is only available on a wide screen (min width is 993px), when the screen is smaller than 993px, the width becomes automatically 100% of page width.

## For writing posts

### Remove heading numbering

If you don't want display number before some heading, just put BEFORE this heading `{.nocount}`, for example,

~~~ {% raw %}
{:.nocount}
## Heading without numbering
{% endraw %} ~~~

If you want to use multiple classes, separate them by space.

### Manually assign an id for a heading

Indert `{:#your-id}` before this heading, for instance,

~~~ {% raw %}
{:#your-id}
## Heading
{% endraw %} ~~~

If you want to then use it

~~~ {% raw %}
[Caption]({{ post.url }}#your-id)
{% endraw %} ~~~

### Insert toc (Table of Contents)

There are actually two choices for the Table of contents! You can add one manually (as
you see to the right, here):

```
{% raw %}{% include toc.html %}{% endraw %}
```

And you can also see the one generated in the left sidebar via the front end matter:

```yaml
toc: 1
```

### Make a list into columns

Put the list inside a `<div>` tag like,

{% highlight html %}
<div class="thi-columns" markdown="1">
- item 1
- item 2
- item 3
- item 4
- item 5
- item 6
</div>
{% endhighlight %}

And the result looks like this - notice how we span two colums!

<div class="thi-columns" markdown="1">
- item 1
- item 2
- item 3
- item 4
- item 5
- item 6
</div>

### Insert a read-more link

~~~ {% raw %}
{% include more.html content="[Welcome to Math2IT](http://math2it.com)." %}
{% endraw %} ~~~

{% include more.html content="[Welcome to Math2IT](http://math2it.com)." %}


### Insert steps

If you want something like this:

<div  class="thi-step">
<div class="step">
<div class="step-number">
</div>
<div class="step-content" markdown="1">
Content in step 1.
</div>
</div>

<div class="step">
<div class="step-number">
</div>
<div class="step-content" markdown="1">
Content in step 2
</div>
</div>
</div>


Do the following:

~~~ html
<div  class="thi-step">
<div class="step">
<div class="step-number"></div>
<div class="step-content" markdown="1">
Content in step 1.
</div>
</div>

<div class="step">
<div class="step-number"></div>
<div class="step-content" markdown="1">
Content in step 2
</div>
</div>
</div>
~~~


## Mathematical expressions

### Inline math
For inline math, use `$math-expression$`

### Block
For an entire block, you can use `$math block$` or 


	$x^n + y^n = z^n$


Which will render to $x^n + y^n = z^n$.


#### Special Characters

If you want to insert some special characters, you must put `\` before this character, for instance, `\\{ 1,2,3 \\}` gives $\\{ 1m2,3 \\}$

**Tips**
 - If you type inline math that contains characters `_`, you must add `\` before each of them, for example, `a\_1` give $a\_1$.
 - Don't use `||` for absolute values, let's use `\vert \vert` instead.
 - Don't use `\left\| \right\|` for norms, use `\Vert \Vert` instead.
 - Don't use `*` for star symbols, use `\ast` instead.
 - If you want to type `\\`, type `\\\\` instead.

#### Matrices
If you want to type an inline matrix, e.g., $[A]=\begin{bmatrix}1 & 2 \\\\ 2 & 3.999 \end{bmatrix}$, type like below,

	$[A]=\begin{bmatrix}1 & 2 \\\\ 2 & 3.999 \end{bmatrix},$


#### Labels
In order to use `\label{}` and `\eqref{}` like in latex, use

	$\begin{align}\tag{1}\label{eq1}
	x^n + y^n = z^n
	\end{align}
	$
	
	Call again equation $\eqref{eq1}$.

The above renders to:

$\begin{align}\tag{1}\label{eq1}x^n + y^n = z^n\end{align}$
Call again equation $\eqref{eq1}$.


## Boxes

### Theorem boxes

A theorum box is a nice little callout to highlight some special text. You
can create one as follows:

{% highlight html %}
<div class="thi-box" markdown="1">
<div class="box-title" markdown="1">
**Title**
</div>
<div class="box-content" markdown="1">
Content
</div>
</div>
{% endhighlight %}

which renders into:

<div class="thi-box" markdown="1">
<div class="box-title" markdown="1">
**Title**
</div>
<div class="box-content" markdown="1">
Content
</div>
</div>


### Interative coding blocks

You even can embed **R/Python** code environment inside a post like this.

<div class="mt-2 mb-2" data-datacamp-exercise data-lang="r">
	<code data-type="pre-exercise-code">
		# This will get executed each time the exercise gets initialized
		b = 6
	</code>
	<code data-type="sample-code">
		# Create a variable a, equal to 5
		# Print out a
	</code>
	<code data-type="solution">
		# Create a variable a, equal to 5
		a <- 5

		# Print out a
		print(a)
	</code>
	<code data-type="sct">
		test_object("a")
		test_function("print")
		success_msg("Great job!")
	</code>
	<div data-type="hint">Use the assignment operator (<code><-</code>) to create the variable <code>a</code>.</div>
</div>


### Notification boxes

A notification box is useful to draw the eyes of the reader to important content.
You could create a warning, for example, like this:

~~~ {% raw %}
{% include warning.html content="Warning's content" %}
{% endraw %} ~~~

Rendered it looks like the following:

{% include warning.html content="Warning's content" %}

There is another style for information:

~~~ {% raw %}
{% include tip.html content="Info's content" %}
{% endraw %} ~~~

which renders to:

{% include tip.html content="Info's content" %}


### Insert Accordian

An accordian menu hides some content, and the user can click to reveal it. It's
best to use an icon on it that suggests that the user should click, like an arrow.

Use these lines of code

~~~ html
<ul class="collapsible" data-collapsible="accordion">
<li>
<div class="collapsible-header" markdown="1"><i class="material-icons">expand_more</i>
Title
</div>
<div class="collapsible-body" markdown="1">
Content
</div>
</li>
</ul>
~~~

The above renders into an expandable section:

<ul class="collapsible" data-collapsible="accordion">
<li>
<div class="collapsible-header" markdown="1"><i class="material-icons">expand_more</i>
Title
</div>
<div class="collapsible-body" markdown="1">
Content
</div>
</li>
</ul>

### Insert blockquote

A blockquote is a nice style to show a quote, for example:

<p class="post-more-info" markdown="1">
The content of extra info of the post.
</p>

And you can generate the above as follows:

{% highlight html %}
<p class="post-more-info" markdown="1">
The content of extra info of the post.
</p>
{% endhighlight %}

> Other normal blockquote like this.

### Summary block

A summary block has a title, and then some content, and is another strategy
to point out more salient information. If you use these lines of code:

{% highlight html %}{%raw%}
<fieldset class="field-set" markdown="1">
<legend class="leg-title">Title</legend>
Content
</fieldset>
{%endraw%}{% endhighlight %}

You can then generate:

<fieldset class="field-set" markdown="1">
<legend class="leg-title">Title</legend>
Content
</fieldset>

{:#cat-tag}
## Categories and tags

### Use it

On the front matter of each post, use this

~~~
categories: [maths, python] 
tags: [algebra, function, theorem]
~~~

### Create a new category

1. Below the title of each post, you will see "in <category>", for example, this post **in NoteTheme**.
2. Open file `_data\categories.yml` and add the new category you want
	- `slug`: the id of this category, it will appear in the url, like
		~~~
		https://dinhanhthi.github.io/notetheme/categories#notetheme
		~~~
	- `name` : the name of this catefory, it will appear on the site, like `notetheme`

### Already-defined tags / categories

Already-defined categories:

<div class="thi-columns">
<ul>
{% for cat in site.data.categories %}
<li><code class="highlighter-rouge">{{ cat.slug }}</code> : <a href="/{{cat.slug}}">{{ cat.name }}</a></li>
{% endfor %}
</ul>
</div>

<p>
Already-defined tags: 
{% for tag in site.tags %}
<code class="highlighter-rouge">{{ tag[0] }}</code>
{% if forloop.last == false %}
, 
{% else %}
.
{% endif %}
{% endfor %}
</p>


## Text

- **New** badge: `<new />`
- **Update** bagge: `<update />`
- **Keyboard**: `<kbd>Ctrl</kbd>`

<new />
<update />
<kbd>Ctrl</kbd>


## Figures / Tables / Videos

- **Normal way**

  ~~~ {% raw %}
  ![](/link/to/figure/){:.w-500 .no-border}
  {% endraw %} ~~~

- **Inline figures**

  ~~~ {% raw %}
  {% include img-inline.html content="/link/to/figure/" %}
  {% endraw %} ~~~

- **Youtube video**

  ~~~ {% raw %}
  {% include youtube.html content="wIsK4kQTrIg" size="5" %}
  {% endraw %} ~~~


## Boxes

### Hide/Show

~~~ html
<ul class="collapsible" data-collapsible="accordion">
<li>
<div class="collapsible-header" markdown="1"><i class="material-icons">face</i>
Title
</div>
<div class="collapsible-body" markdown="1">
Content
</div>
</li>
</ul>
~~~

### Notifications

- Info

  ~~~ html
  <p markdown="1" class="thi-tip">
  <i class="material-icons mat-icon">info</i>
  content
  </p>
  ~~~

- Error

  ~~~ html
  <p markdown="1" class="thi-warning">
  <i class="material-icons mat-icon">error</i>
  content
  </p>
  ~~~


### Pull quotes

~~~ html
<p class="post-more-info" markdown="1">
The content of extra info of the post.
</p>
~~~

### Summarization box

~~~ html
<fieldset class="field-set" markdown="1">
<legend class="leg-title">Title</legend>
Content
</fieldset>
~~~

### Theorem style

~~~ html
<div class="thi-box" markdown="1">
<div class="box-title" markdown="1">
**Title**
</div>
<div class="box-content" markdown="1">
Content
</div>
</div>
~~~

### Important boxes

~~~ html
<div class="p-mark" markdown="1">
Content
</div>
~~~

## Others

### Side by side

~~~ html
<div class="row d-flex" markdown="1">
<div class="col s12 l6" markdown="1">
This is the code
</div>
<div class="col s12 l6" markdown="1">
This is the result
</div>
</div>
~~~

### Links

See again

~~~ html
<div class="see-again">
<i class="material-icons">settings_backup_restore</i>
<span markdown="1">
Content
</span>
</div>
~~~

Read-more link

~~~ {% raw %}
{% include more.html content="[Welcome to Math2IT](http://math2it.com)." %}
{% endraw %} ~~~

Download

~~~ {% raw %}
{% include download.html content="[Download text](download link)." %}
{% endraw %} ~~~

### Notices

You can create a notice as follows:

```html
<fieldset class="field-set" markdown="1">
<legend class="leg-title">TL;DR</legend>
- Show the post in a flexible way.
- Show the figures any place
- Show the maths, the code blocks in a beautiful way.
- and many things else...
</fieldset>
```

And it looks like this

<fieldset class="field-set" markdown="1">
<legend class="leg-title">TL;DR</legend>
- Show the post in a flexible way.
- Show the figures any place
- Show the maths, the code blocks in a beautiful way.
- and many things else...
</fieldset>

### Steps

~~~ html
<div  class="thi-step">
<div class="step">
<div class="step-number"></div>
<div class="step-content" markdown="1">
Content in step 1.
</div>
</div>

<div class="step">
<div class="step-number"></div>
<div class="step-content" markdown="1">
Content in step 2
</div>
</div>
</div>
~~~
