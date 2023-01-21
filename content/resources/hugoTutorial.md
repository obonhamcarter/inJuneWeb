---
title: "Build a Hugo Site with a Theme"
date: 2023-01-20T18:28:30-05:00
draft: false
---


**Making a website with Hugo**: You might want to use this bare-bones website template for an online research website.

Below is code to create a website and then to add posts (blogs) to the project. Each of these posts that you create could be akin to pages in a book that you could organize chronologically. Have fun!
<!-- add a line drop -->
<center>
&#x200B;

&#x200B;
</center>

<center>
<img src="/images/main/posts.png" alt="Huge Research Notebook" style="width:500px;"/>
</center>

<!-- add a line drop -->
<center>
&#x200B;

&#x200B;
</center>


### Creating a Web Site

* `hugo new site myAnubisThemeSite`
* Get the site ready to add to github: `git init`

#### Adding Posts

* Add a directory "Post" and place in it a Markdown file post1.md: `hugo new /post/post1.md`

#### Theme
You could use seemingly any theme that you want to use -- there are [quite a lot available](https://themes.gohugo.io/). In this tutorial, we will use a simple one called [Anubis](https://github.com/mitrichius/hugo-theme-anubis) that will provide a basic page by page view of notes. 

Add a submodule of the theme to `themes/` directory. Note adding repository as a submodule allows us to embed a GitHub project within another GitHub project. Git does not like multiple `.git` directories in a project.

```bash
git submodule add 
  https://github.com/mitrichius/hugo-theme-anubis.git
  themes/anubis
```

#### Connect site to a theme: Add the following to `confit.toml`

``` bash
baseURL = "http://example.org/"
languageCode = "en-us"
title = "My Amazing Site!"
theme = "anubis"
```

#### Add a Menu System: Add the following to `confit.toml`
Note, you can add as many menu items as necessary. Be sure to increment the `weight` variable by one for each item.   
``` bash
[menu]

[[menu.main]]
identifier = "about"
name = "posts"
url = "/posts/"
weight = 1
```

### Adding a photo to a post

* Store all photos in the `static/ directory in the root. Note: it might be better to organize photos by different directories.
* Add a header and then place code to access the png file.

``` bash
## A photo of the Allegheny College Mascot

![Photo](/graphics/mascot.png)
```