Title: My first post with pelican octopress theme
date: 2014-04-03
comments: true
slug: my-first-post-with-pelican-octopress-theme
---

<!-- PELICAN_BEGIN_SUMMARY -->
Not a big fan of blog, but I was really fascinated by this idea of having a
static microblog site which is:

 * written in plain text with your preferred markup language
 * generated and themed on-the-fly
 * version controlled by git

While [Jekyll](http://jekyllrb.com) and [Octopress](http://octopress.org) are
two such excellent tools, they are all written in Ruby, which I'm not quite
familiar with.  I was not able to find a Python equivalent tool until not very
long ago I found [Jake's blog](http://jakevdp.github.io).  It was well themed
and all the articles are great to read.  I can't refrain the idea of having
a similar blog site of my own.  It turned out to be not very complicated, I
am using Ubuntu and followed the steps below.

<!-- PELICAN_END_SUMMARY -->

### Install prerequisites:

 * [pelican](http://getpelican.com) - a python based static site generator
 * [markdown](http://https://help.github.com/articles/markdown-basics)

``` shell
$ sudo apt-get install pip
$ sudo pip install pelican
$ sudo pip install markdown
```

### Install octopress theme for pelican

``` shell
$ git clone https://github.com/duilio/pelican-octopress-theme
$ sudo pelican-themes -i pelican-octopress-theme pelican-octopress-theme/
```

### [Kickstart](http://docs.getpelican.com/en/3.3.0/getting_started.html) the site with pelican

``` shell
$ pelican-quickstart 
Welcome to pelican-quickstart v3.3.0.

This script will help you create a new Pelican-based website.

Please answer the following questions so this script can generate the files
needed by Pelican.

    
> Where do you want to create your new web site? [.] 
> What will be the title of this web site? Another Code Farmer's Backyard
> Who will be the author of this web site? Eric Miao
> What will be the default language of this web site? [en] 
> Do you want to specify a URL prefix? e.g., http://example.com   (Y/n) n
> Do you want to enable article pagination? (Y/n) n
> Do you want to generate a Fabfile/Makefile to automate generation and publishing? (Y/n) 
> Do you want an auto-reload & simpleHTTP script to assist with theme and site development? (Y/n) 
> Do you want to upload your website using FTP? (y/N) 
> Do you want to upload your website using SSH? (y/N) 
> Do you want to upload your website using Dropbox? (y/N) 
> Do you want to upload your website using S3? (y/N) 
> Do you want to upload your website using Rackspace Cloud Files? (y/N) 
```

### Voila! Create your first article

Creating a plain text file in the folder of `content`, name the file in format
`yyyy-mm-dd-<post-topic>.md`.  For [example](http://docs.getpelican.com/en/3.3.0/getting_started.html#writing-content-using-pelican):


```
Title: My super title
Date: 2010-12-03 10:20
Category: Python
Tags: pelican, publishing
Slug: my-super-post
Author: Alexis Metaireau
Summary: Short version for index and feeds

This is the content of my super blog post.
```

### Change pelicanconf.py to use octopress theme:

``` diff
diff --git a/pelicanconf.py b/pelicanconf.py
index 590c26d..c6b05d1 100644
--- a/pelicanconf.py
+++ b/pelicanconf.py
@@ -29,3 +29,5 @@ DEFAULT_PAGINATION = False
 
 # Uncomment following line if you want document-relative URLs when developing
 #RELATIVE_URLS = True
+
+THEME = 'pelican-octopress-theme'
```

### Generate and check the site:

``` shell
$ make html
$ cd output && python -m SimpleHTTPServer
Serving HTTP on 0.0.0.0 port 8000 ...
```

### Deploy when satisfied

For example, [github pages](http://pages.github.com/) is a good choice.
