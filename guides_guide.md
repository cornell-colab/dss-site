# CoLab Guides Guide
This file serves a guide to the features built into the Just the Docs Template for the Digital Scholarship Services Guides site. This does not include documentation for how to use the [Just the Docs Jekyll template](https://just-the-docs.com/), though some sections may overlap.

## Git Setup
In order to edit the Guides site locally, you can either create and edit a Markdown file on your computer and then upload the new Markdown file to the GitHub Repository's pages folder; or edit the whole site locally by making a copy.

To edit locally in VSCode:
1. Go to the remote repository at https://github.com/cornell-colab/guides-site.
2. Click *Code* > *GitHub CLI*. 
3. Clone the repository: Copy the command under GitHub CLI and paste it into the Command Line/Terminal on your computer.
4. After the command runs, change into the directory for your new cloned repository.
5. Run `git remote add main https://github.com/cornell-colab/guides-site.git`.

You should now have a local version of the repository's main branch on your computer. In every editiong session BEFORE you make a change to the site, use git to pull the remote repository changes. Then push your changes to the remote repository when you're done.

## Folder Structure
The index.md (homepage) files, _config.html, and other general, whole site files are stored at the root folder at dss-site. The *_data* folder holds .csv files and other files that can be processed by *includes*, like a list of images for a page, list of items for a card gallery, etc. The *_includes* folder holds all of the extra code that makes interactive functions and buttons, like cards, galleries, dropwdowns, and image text boxes, work. The *_layouts* folder contains the default layout for the homepage, which exists outside of just-the-docs. the *_sass* folder contains stylesheets for just-the-docs only. The assets folder contains all images, scripts, and other stylesheets for the site. The pages folder contains each page on the guides site, excluding the homepage. The drafts folder contains pages that you do not want to be published yet.

Below is the file structure, provided in a diagram:
├── dss-site/
├── index.md
├── guides_guide.md
├── .gitignore
├── _config.yml
├── Gemfile
├── Gemfile.lock
│   ├── _data/
│   │   ├── cad-tools.csv
|   ├── _includes/
│   │   ├── banner.html
│   │   ├── card.html
│   │   ├── carousel-js.html
│   │   ├── grid.html
│   │   ├── img-txt.html
│   │   ├── dropdown-js.html
│   │   ├── toc-js.html
│   │   ├── tocbot-init-js.html
│   │   ├── colab-footer.html
│   │   ├── colab-head.html
│   │   ├── colab-navigation.html
|   ├── _layouts/
│   │   ├── category.html
│   │   ├── colab-default.html
│   │   ├── colab-page.html
│   │   ├── post.html
|   ├── _sass/
│   │   ├── color_schemes
│   │   |   ├── colabs.scss
│   │   ├── custom
│   │   |   ├── custom.scss
|   ├── _site/
|   ├── .jekyll-cache/
|   ├── .vscode/
|   ├── assets/
│   │   ├── js/
│   │   |   ├── make-ids.js
│   │   |   ├── tocbot.min.js
│   │   ├── img/
│   │   |   ├── img.jpg
│   │   |   ├── img.png
│   │   ├── css/
│   │   |   ├── main.css
│   │   |   ├── tocbot.css
|   ├── drafts/
│   │   ├── draft_guide_01.md
│   │   ├── draft_guide_02.md
│   │   ├── draft_guide_03.md
|   ├── pages/
│   │   ├── guide_01.md
│   │   ├── guide_02.md
│   │   ├── guide_03.md

## Editing the Site
### Adding a Page
To add a page to the site, simply create a new Markdown file (.md) and add it to a page in the *pages* folder. 

### Page Frontmatter
Each page needs YAML frontmatter at the top. You can see a template of the available frontmatter options at `pages/template.md`. The options include:

```
---
title: "TITLE FOR YOUR PAGE"
layout: page
permalink: /guides/FILENAME W/O EXTENSION
parent: FILENAME W/O EXTENSION FOR PARENT PAGE
nav_order: NUMBER
nav_enabled: true
nav_exclude: true
search_exclude: true
---
```

### Editing a Page
You can edit a page simply by adding new [Markdown-formatted](https://www.markdownguide.org/) content to the page.

#### Adding Includes
You can add include to a page by identifying the space in the page you'd like to add your include and inserting:
{% include FILENAME OF INCLUDE W/O EXTENSION %}. Each include has its own arguments or parameters that can be included to determine what content appears. Each include in the *_includes* folder lists its parameters as a comment at the top of the file.

#### Adding Files/Links
To avoid hotlinking, please upload any PDFs, images, scripts, videos, or other media files to the *assets* folder, within an approriately titled subfolder. Your link to said media item will then be internal to the site, rather than pulling from an external server. Because of this internal structure, you can use shortened relative paths instead of full links, e.g. "/assets/img/digital-colab.png".

### Editing the Navigations
To edit the items available in the navigation bar on the homepage, go to `_includes/colab-navigation.html`. To edit the items available in the sidebar navigation for the Guides, you will need to edit the YAML frontmatter for an individual page.

### Editing Appearance/Aesthetics 
I recommend reaching out to Kiran to edit the CSS or SCSS for this site. Since Just the Docs relies on a Jekyll-imported Ruby gem to function, it does not have a local stylesheet that can be manipulated easily to edit the appearance of the pages.

## A Note for File-Editing
I do not recommend editing the _site, .jekyll-cache, .vscode, or other associated files. The site folder is the HTML-rendered output of Jekyll's ruby conversions, and won't actually edit the code behind the site. The .jekyll-cache and .vscode folders are just for directing Jekyll and VSCode to process the site data in specific ways.

