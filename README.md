# Truveris Engineering Blog

This is the source repository for our engineering site.  Rendering occurs in
the `output/` directory created on the fly and managed in the separate `master`
branch.


## Directory structure
 * **Makefile**:       build, serve and publish rules
 * **bin/**:           tools and library used to administrate and render the site
 * **authors/**:       article authors
 * **site/**:          site templates
 * **site/articles/**: blog articles
 * **site/jobs/**:     Job positions


## Serve it locally
Make your changes in the `site/` directory while the following command is
running to see your updates directly without re-generating the output:

```shell
make serve
```


## Build the static site
Generates the full site into the `output/` directory:

```shell
make
```


## Publish the static site to our GitHub user page
Edit, commit, publish:

```shell
vim site/things.html
git commit -am "Updated Jimmy's email."
make publish
```


## Adding a new author
Create a new folder named after your GitHub account in the `authors/`
folder and create the following files:
 * **name**: your full name
 * **email**: your email address
 * **avatar**: name of a file located in `site/lib/img/` used in the footer of
       the article as an avatar image.


## Adding a new article
Create a new folder in the `site/articles/` folder and create the following files:
 * **author**: must contain your GitHub account name. A matching folder is
       required with meta data as defined above.
 * **illustration**: name of a file located in `site/lib/img/` used in the
       header of the article.  It is important to keep the same style, one
       should not just add any image as header.
 * **index.html**: this is the actual content of the article in HTML format,
       copy another article to get all the proper mako format and dependencies
       in place.
 * **timestamp**: when the article was created in ISO8601 format.
 * **short.html**: short introduction HTML used in the index page. Do *not* use
       links in this file, they are distracting the user from the "Read more".
 * **description**: a couple of sentences describing the article (metadata).
 * **canonical**: an optional canonical reference meta tag (metadata).

Keep all the images related to this article in the same folder (minus the
illustration which should be generic enough to be re-usable).


## Adding a new page
If you need to extend the site outside of the above, create an `index.html` in
a folder within the `site/` folder.  It is important to come up with a simple
dash-separated name since it will be used as its permanent URL for the rest of
time.


## Updating the CSS
Since we use SCSS/SASS for all our stylesheets, you should never touch a CSS
file in this project. Once you are done playing with the .scss file, just run
`make css` from the root folder.  If you don't have Sass installed, you can
install it quickly with:

```
sudo gem install sass
```
