# The Minimal Light Theme

\[[See the theme](https://kumaripriyankasingh.github.io/)\]
 
*This is the source code of my homepage. I build this website based on [minimal](https://github.com/pages-themes/minimal).*
<br>
*Feel free to use and share the source code anywhere you like.*


## Features

- Simple and elegant personal homepage theme
- Jekyll theme, automatically deployed by GitHub Pages
- Basic search engine optimization
- Mobile friendly
- Supporting Markdown 
- Supporting dark mode

## Project Architecture

```
.
├── _includes                    
|   ├── publications.md          # the Markdown file for publications
|   
├── _layouts                  
|   └── homepage.html            #  the html template for the homepage 
├── _sass                     
|   └── minimal-light.scss       #  this file will be compiled into a CSS file to control the style of the page
├── assets                       #  some files
├── .gitignore                   #  this file specifies intentionally untracked files that Git should ignore
├── CNAME                        #  the custom domain, will be used by GitHub page sevice
├── Gemfile                      #  a RubyGems related file
├── LICENSE                      #  the license file
├── README.md                    #  the readme file (English)
├── _config.yml                  #  the Jekyll configuration file, including some options of the page  
└── index.md                     #  the content of the index page, using Markdown
```

## Getting Started

This template can be used in the following two ways: 
- **Using with the GitHub Pages Service.** GitHub will provide you with a server to generate and host web pages.
- **Using locally with Jekyll.** You may install Jekyll on your own computer and generate static web pages (i.e., HTML files) with this template. After that, you may upload the HTML files to your server.

The detailed instructions are available below.


### Using with the GitHub Pages Service

There are two ways to use this template on GitHub:

#### Fork this repository
- Fork this repository (or [use this repository as a template](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template)) and change the name to `your-username.github.io`.

- Enable the GitHub pages for that repository following the steps [here](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site#creating-your-site).


### Using Locally with Jekyll

First, install [Ruby](https://www.ruby-lang.org/en/) and [Jekyll](https://jekyllrb.com/). The install instructions can be found here: <https://jekyllrb.com/docs/installation/#guides>

Then, clone this repository:

```bash
git clone https://github.com/kumaripriyankasingh/kumaripriyankasingh.github.io
cd kumaripriyankasingh.github.io
```
Install and run:

```bash
bundle install
bundle exec jekyll server
```
View the live page using `localhost`:
<http://localhost:4000>. You can get the HTML files in `_site` folder.

## Customizing

### Configuration variables

The Minimal Light theme will respect the following variables, if set in your site's `_config.yml`:

### Edit `index.md`

Create `index.md` and add your personal information. It supports **Markdown** and **HTML** syntax.


### Stylesheet

If you'd like to add your own custom styles, you may edit `_sass/minimal-light.scss`.

### Layouts

If you'd like to change the theme's HTML layout, you may edit `_layout/homepage.html`.


## Acknowledgements

Our project uses the source code from the following repositories:

* [pages-themes/minimal](https://github.com/pages-themes/minimal)

* [minimal-light.yyliu](https://github.com/yaoyao-liu/minimal-light)
