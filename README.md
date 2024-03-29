# vvtk-docs
This is the website of [VVTk: A Toolkit for Volumetric Video Researchers](https://github.com/nus-vv-streams/vvtk).

You can open the website: [`https://nus-vv-streams.github.io/vvtk-docs/`](https://nus-vv-streams.github.io/vvtk-docs/)

## Requirements
1. [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
2. [Node.js and NPM](https://nodejs.org/en/download)
3. [GO](https://go.dev/doc/install) (optional)
4. [Hugo](https://gohugo.io/installation/) (optional)

## Installation
1. Clone the repository to your local computer
2. `cd` into the project directory and run `npm install` to install the dependencies
3. Run `npm run dev` to start development server
4. Open this URL: `http://localhost:1313/` to start browsing your site locally. Note that it lets you preview your work and automatically refreshes your browser when you make changes.

## Project Structure
This website is a [Doks](https://getdoks.org/) project.

### Directories and Files
- `assets/`: Your project assets (scripts, styles, images, etc.)
- `config/`: Configuration files (Hyas, Hugo, PostCSS, etc.)
- `content/`: Your project content (docs, blog, etc.)
- `layouts/`: Your project layouts (partials, shortcodes, etc.)
- `static/`: Your non-code, unprocessed assets (fonts, icons, etc.)
- `package.json`: A project manifest (scripts, dependencies, etc).

### Project contents
````
.
├── assets/
├── config/
│   └───_default/
│       ├───hugo.toml - The site configuration file.
│       ├───menus.toml - The site menus file.
│       ├───module.toml - The Hugo mounts configuration file.
│       └───params.toml - The Doks + Hyas integrations configuration file.
│   └───production/
│       ├───hugo.toml - Overrides for production environment.
├── content/
│   └───docs/
│       ├───basics/
│       │   ├───_index.md
│       │   └───vv.md
│       │   └───vvplay.md
│       ├───guides/
│       │   ├───_index.md
│       │   └───getting-started.md
│       ├───reference/
│       │   ├───_index.md
│       │   └───developer.md
│       └───_index.md
│       └───privacy.md
├── layouts/
│   └───index.html - Go template for Home page
├── static/
└── package.json
````
### Add pages
Add new pages to your site by creating `.md` or `.html` files in `content/docs/`. Use sub-folders to organize your files and to create multiple path segments.

For example, the following command will generate a `.md` page at `docs/guides/faq`:

```shell
npm run create docs/guides/faq.md
```

#### Frontmatter

All Doks pages share a customizable common set of [frontmatter properties](https://getdoks.org/docs/reference/frontmatter/) to control how the page appears — for documentation pages:

```md
---
title: "Example Guide"
description: ""
summary: ""
date: 2023-09-07T16:04:48+02:00
lastmod: 2023-09-07T16:04:48+02:00
draft: true
weight: 999
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

```

## Reference
- [Doks document](https://getdoks.org/)
- [Hyas document](https://gethyas.com/)