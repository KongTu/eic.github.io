---
title: How-to
name: howto
layout: default
---
{% include layouts/title.md %}

#### Overview
The following will be of interest to the collaborators interested in contributing to this
site or involved in its maintenance.

Please take a look at the <a href="https://github.com/eic/eic.github.io" target="_blank">repository</a>
to get an idea of the general organization of the data, layouts and supporing logic.
The idea is to shape the code and content in a way that is easy to navigate
and modify. The following sections explain how this is achieved.
Development of this site involves the following aspects:
* adding and modifying the structured data content
* adding "assets" i.e. documents, images etc - although this needs to be done sparingly: one
needs to keep in mind that there are practical limits on the size of any repository, as well
as hard limits on repositories of sites which are hosted as "GitHub pages"
* interfacing the navigation tools on this site, which for the most part consists
of the top navigation bar and the dropdown menus

#### The Navigation Bar
Entries in the navigation bar on top are named similar to the folders in this
project, for example the "Software" is associated with the folder "_software" etc.
These folders are treated as "collections" by the Jekyll framework and they need to be declared
in the main configuration file
<a href="https://github.com/eic/eic.github.io/blob/master/_config.yml" target="_blank">_config.yml</a>.
As one can see in 
<a href="https://github.com/eic/eic.github.io/blob/master/_includes/layouts/navbar.html" target="_blank">the navigation bar code</a>,
its menu entries are generated automatically based on the content of the file
<a href="https://raw.githubusercontent.com/eic/eic.github.io/master/_data/menus.yml" target="_blank">_data/menus.yml</a>.
The content and order of top entries in the navigation bar as well as content and ordering of all items in all dropdown
menus are defined in that file.

#### Front Matter
"Front Matter" is a piece of YAML code (typically short) on the very top of a Markdown-formatted
document which can contain any sort of data, for example variables used to render the page.
It can be used to define the behavior and treatment of the page in higher-level
contructs referencing it, since the data in the Front Matter is accessible as object attributes.
Importantly, it also serves to inform the platform "Jekyll" that this particular page needs to be
rendered into HTML for inclusion in the site being built.

All files are expected to be in the Markdown (MD) format, and 
**each MD file is to be equipped with the "front matter" section**, which could look like the excerpt below.
```
---
title: My Cool Software
name: my_cool_software
category: mysoftware
layout: default
---
```

There is no source code (i.e. markdown page content) for links to external resources included in the menus.
Examples are easy to spot in the file <a href="https://raw.githubusercontent.com/eic/eic.github.io/master/_data/menus.yml" target=_blank>_data/menus.yml</a>.
To include a divider right above an entry in a dropdown menu the following line should be added
respective section of the _data/menus.yml file: "**div: yes**". Additionally, the "exclude" attribute is provided, mainly for development purposes, if
a section of the menu needs to be ignored when building the site.

#### Managing Data
Jekyll is fairly flexible when it comes to storing and manipulating structured data.
The data component of the site can reside in the "front matter" section of the Markdown-formatted
files or in separate YAML (or JSON, CSV etc) data sources. The front matter approach works well
for small sites. For scalability, it is recommended to rely mostly on dedicated data files (i.e.
files in the "<a href="https://github.com/eic/eic.github.io/tree/master/_data" target="_blank">_data</a>" folder)
and keep the content of the front matter sections of individual MD files to a minimum.

The <a href="https://shopify.github.io/liquid/" target="_blank">Liquid</a> template language
features a variety of filters that can be applied to the data stored in YAML and other data sources
as well as in the front matter blocks of pages, and decent (not perfect) support for collections,
iterators and flow control constructs.

Information assets on this site (e.g. imaged, PDF files etc) are stored in the aptly named
"<a href="https://github.com/eic/eic.github.io/tree/master/assets/" target="_blank">assets</a>"
folder and its subsiduaries. This convention should be kept going forward.

#### Formatting
We aim to provide a uniform look and feel across the site. To that end, whenever possible
the head (title) of each page is formatted by using the standard include layouts/title.md - please
look a the code for examples of its use. It's renders the page title from the front matter sections.

Headers of sections within a page are currently formatted in Markdown as "header level 4" i.e. prepended
with four hash characters like in **"#### My section header"**. Take a look at the header (Formatting)
of this section to get an idea of how it's rendered.

#### Development

To productively participate in the development of this site one needs to learn the
<a href="http://jekyllrb.com/">Jekyll</a> framework and perform its installation on
a development machine. This way any modification can be validated immediately since
the locally running development server provided by Jekyll will render the site
on the local host. Basic knolwede of the <a href="https://shopify.github.io/liquid/" target="_blank">
Liquid</a> template language and in particular the "filters" that are part of it is extremely helpful.

#### Checking the Results of Your Contribution

It is often desirable to assess the result of changes before publishing them. There is no services at GitHub to do that: 
you can only render the markdown contents, without all the CSS and other things. To achieve this, you need to install 
Jekyll on your local machine. Detailed instructions can be found on Jekyll [web site](https://jekyllrb.com/docs/installation/) 
but the short story is:

* Install [Ruby](https://www.ruby-lang.org/en/downloads/) and [RubyGems](https://rubygems.org/pages/download)
* Install Bundler (a Ruby package manager):

  ```bash
  gem install bundler
  ```

* If you don't have one yet, create a clone of the website repository and move to the directory created:

  ```bash
  git clone https://github.com/eic/eic.github.io.git
  cd eic.github.io
  ```

* Install/update your Jekyll installation (must be done regularly):

  ```bash
  bundler update
  ```

* Run Jekyll installation:

  ```bash
  bundler exec jekyll serve
  ```


Once Jekyll has been started you can view the web site by connecting to `localhost:4000`.
Changes made to files are immediately reflected on the displayed site (at the next page load). This makes it extremely efficient to make changes and debug entirely locally before uploading the final changes to GitHub.

At this point, pushes are allowed for site developers. A pull request/approval process may be put in place later if needed.



