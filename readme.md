The EasyBake Site
=================
A launching point for a simple CMS-based site.

* [Background](#background)
* [Quickstart](#quickstart)
* [Dependencies](#dependencies)
  * [Jekyll](#jekyll)
  * [Netlify](#netlify)
  * [Netlify CMS](#netlify-cms)
  * [UIKit](#ui-kit)
* [Documentation](#documentation)

Background
==========
While traditional CMSs like Drupal, Wordpress, and Joomla offer extremely flexible & extensible backends for building powerful sites, they have a few trade-offs:
- Complexity beyond what a small business may need or be able to afford
- Security concerns stemming from modules/plugins and permissions
- Requires a server-side processing

A large number of smaller clients don't need much more than a handful static pages and a small number of syndicated content types, so we developed the Midnet EasyBake template to streamline the creation of sites for our clients that don't need the superior customization or functionality that the big-name CMSs provide.

Quickstart
==========
1) Fork this repository
2) Configure CMS settings
3) Customize SASS variables
4) Set up site with Netlify
5) Profit!

For more in-depth step-by-step directions, see our [documentation](#documentation), or reference the docs for the dependencies below.

Dependencies
============
#### Jekyll
Jekyll is a simple, blog-aware, static site generator perfect for personal, project, or organization sites. Think of it like a file-based CMS, without all the complexity. Jekyll takes your content, renders [Markdown](https://www.markdownguide.org/cheat-sheet) and [Liquid](https://shopify.github.io/liquid/) templates, and spits out a complete, static website ready to be served by Apache, Nginx or another web server. Jekyll is the engine behind GitHub Pages, which you can use to host sites right from your GitHub repositories.

- [Official Site](https://jekyllrb.com/)
- [Official Documentation](https://jekyllrb.com/docs/)
- [Github](https://github.com/jekyll/jekyll)

#### Netlify
An all-in-one workflow that combines global deployment, continuous integration, and automatic HTTPS. And that’s just the beginning.

- [Official Site](https://www.netlify.com/)
- [Official Documentation](https://www.netlify.com/docs/)

#### Netlify CMS
A CMS for static site generators. Give non-technical users a simple way to edit and add content to any site built with a static site generator.


- [Official Site](https://www.netlifycms.org)
- [Official Documentation](https://www.netlifycms.org/docs/intro/)
- [Github](https://github.com/netlify/netlify-cms)

#### UI Kit
A lightweight and modular front-end framework
for developing fast and powerful web interfaces.

- [Official Site](https://getuikit.com/)
- [Official Documentation](https://getuikit.com/docs/)
- [Github](https://github.com/uikit/uikit)

Documentation
=============

*It's important to note that this template is not for every project or every client.*

The EasyMake site is designed to get a functioning site up and running in **less than one day** by leveraging a CSS/JS component framework to create a site with a simple, intuitive CMS, templated pages, and minimal custom functionality.

It's also important to note that while this project utilizes a CMS, it does not have an upgrade path to a more extensible CMS like Drupal, Wordpress, or Joomla. If a site will *eventually* have high-end features such as e-commerce, it may be a better use of your time to build the site in another CMS.

- [Initialization](#initialization)
- [Configuration](#configuration)
  - [Jekyll](#jekyll-config)
  - [Netlify CMS](#netlify-cms-config)
  - [Collections & Fields](#collections-and-fields)
- [Theming](#theming)
  - [UI Kit Components](#ui-kit-components)
  - [Includes](#includes)
  - [Layouts](#layouts)
  - [SCSS](#scss)
- [Deployment](#deployment)
  - [Netlify](#netlify)
  - [User Authentication](#user-authentication)

### Initialization

### Configuration

#### Jekyll Config

Default Jekyll Config

```yml
# Where things are
source              : .
destination         : ./_site
collections_dir     : ./collections
plugins_dir         : _plugins
layouts_dir         : _layouts
data_dir            : _data
includes_dir        : _includes
collections         :
  collection-one:
    output          : true
  collection-two:
    output          : true
  collection-three:
    output          : true
  collection-four:
    output          : true

# Handling Reading
safe                : false
include             : [".htaccess"]
exclude             : ["Gemfile", "Gemfile.lock", "node_modules", "vendor/bundle/", "vendor/cache/", "vendor/gems/", "vendor/ruby/"]
keep_files          : [".git", ".svn"]
encoding            : "utf-8"
markdown_ext        : "markdown,mkdown,mkdn,mkd,md"
strict_front_matter : false

# Filtering Content
show_drafts         : null
limit_posts         : 0
future              : false
unpublished         : false

# Plugins
whitelist           : []
plugins             :
  - jekyll-menus
  - jekyll-sitemap

# Conversion
markdown            : kramdown
highlighter         : rouge
lsi                 : false
excerpt_separator   : "\n\n"
incremental         : false

# Serving
detach              : false
port                : 4000
host                : 127.0.0.1
baseurl             : "" # does not include hostname
show_dir_listing    : false

# Outputting
permalink           : date
paginate_path       : /page:num
timezone            : null

quiet               : false
verbose             : false
defaults            : []

liquid:
  error_mode        : warn
  strict_filters    : false
  strict_variables  : false

# Markdown Processors
rdiscount:
  extensions        : []

redcarpet:
  extensions        : []

kramdown:
  auto_ids          : true
  entity_output     : as_char
  toc_levels        : 1..6
  smart_quotes      : lsquo,rsquo,ldquo,rdquo
  input             : GFM
  hard_wrap         : false
  footnote_nr       : 1
  show_warnings     : false

# Variables
# You can place more variables here and they will be available as {{ site.variable_name }}
```


#### Netlify CMS Config

Default Netlify CMS Config
```yml
backend:
  name: git-gateway
  branch: master # Branch to update (master by default)

media_folder: "assets/uploads" # Folder where user uploaded files should go

collections: # A list of collections the CMS should be able to edit
  - name: "blog" # Used in routes, ie.: /admin/collections/:slug/edit
    label: "Blog" # Used in the UI, ie.: "New Post"
    folder: "collections/_collection-one" # The path to the folder where the documents are stored
    sort: "date:desc" # Default is title:asc
    create: true # Allow users to create new documents in this collection
    slug: "blog/{{fields.title}}"
    fields: # The fields each document in this collection have
      - {label: "Layout", name: "layout", widget: "hidden", default: "post"}
      - {label: "Title", name: "title", widget: "string", tagname: "h1"}
      - {label: "Body", name: "body", widget: "markdown"}
      - {label: "Categories", name: "categories", widget: "string", required: false}
    meta: # Meta data fields. Just like fields, but without any preview element
      - {label: "Publish Date", name: "date", widget: "datetime", format: "YYYY-MM-DD hh:mm:ss"}
```

#### Collections and Fields

### Theming

#### UI Kit Components

#### Includes

#### Layouts

#### SCSS

### Deployment

#### Netlify

#### User Authentication
