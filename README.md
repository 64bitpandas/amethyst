# Amethyst Hugo Theme

[![Hugo](https://img.shields.io/badge/hugo-0.96-blue.svg)](https://gohugo.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)



![amethyst screenshot](https://github.com/64bitpandas/amethyst/blob/e8429e790e25dc6f3318826905f4e4a031d04363/images/screenshot.png)

## Why Amethyst?
I write most of my [notes](https://notes.bencuan.me) in [Obsidian](https://obsidian.md/). When trying to find a suitable open-source alternative for Obsidian Publish, I couldn't find exactly what I was looking for: a simple, customizable theme with sidebar navigation that supported Obsidian features (like backlinks or LaTeX) in such a way that didn't require me to reformat my notes.

Amethyst is an attempt to deliver this by combining the navigational features of [hugo-book](https://github.com/alex-shpak/hugo-book) with the Obsidian integrations of [quartz](https://github.com/jackyzha0/quartz) to provide a hassle-free place to store and host personal notes or documentation.

## Features

Amethyst preserves most of the features of quartz and hugo-book, including:
 - Navigation sidebars on left and right of content
 - Obsidian-style callouts 
 - Interactive graph view
 - MermaidJS charts
 - User-togglable dark mode
 - Search bar
 - Multi-language support
 - Mobile support
 - Obsidian-style back/forward links and page previews

Some new features that were added on top:
 - Custom formatting of tabs, sections, and expands specifically for Q&A-style interaction
 - Easy customization of theme colors and fonts
 - LaTeX enabled out of the box with no additional config
 - Support for both absolute and relative links, Obsidian-style

## Documentation
If you just want to use Amethyst for your own notes hosting, go to [amethyst.bencuan.me](https://amethyst.bencuan.me) for a demo and documentation on how to use it.

Keep reading if you want to help develop Amethyst, or make changes to the code base for your own needs.

## Requirements

- **Go 1.16 or higher**: [installation instructions](https://golang.org/doc/install)
- **Hugo 0.93 or higher:** [installation instructions](https://gohugo.io/getting-started/installing/) 
  - If installing on Ubuntu/Debian-based systems, this is a higher version than is available in apt at the time of writing. Install the extended version from the [releases page](https://github.com/gohugoio/hugo/releases) instead.
- **Hugo-obsidian:** Run `go install github.com/jackyzha0/hugo-obsidian@latest`.
  - If you're getting a `command not found` error, [ensure that your PATH is configured properly so that binaries in the GOPATH can be executed](https://stackoverflow.com/questions/21001387/how-do-i-set-the-gopath-environment-variable-on-ubuntu-what-file-must-i-edit).

## Live Server

Start the live server using `make serve`. Content will be served to `localhost:1313` by default.

The server will need to be restarted to preview changes to navigation (internal links and sidebar menu).

## Configuration

### Site Configuration

Most configuration can be done by creating a `config.yaml` file in the root directory and editing the parameters. You can start by copying the example [here](https://github.com/64bitpandas/amethyst/blob/main/config.yaml).

Graph-specific configuration can be added to `data/graphConfig.yaml`. (Example [here](https://github.com/64bitpandas/amethyst/blob/main/data/graphConfig.yaml))


### Multi-Language Support

Theme supports Hugo's [multilingual mode](https://gohugo.io/content-management/multilingual/), just follow configuration guide there. You can also tweak search indexing configuration per language in `i18n` folder.

### Page Configuration

You can specify additional params in the front matter of individual pages:

```toml
# Set type to 'docs' if you want to render page outside of configured section or if you render section other than 'docs'
type = 'docs'

# Set page weight to re-arrange items in file-tree menu (if BookMenuBundle not set)
weight = 10

# (Optional) Set to 'true' to mark page as flat section in file-tree menu (if BookMenuBundle not set)
bookFlatSection = false

# (Optional) Set to hide nested sections or pages at that level. Works only with file-tree menu mode
bookCollapseSection = true

# (Optional) Set true to hide page or section from side menu (if BookMenuBundle not set)
bookHidden = false

# (Optional) Set 'false' to hide ToC from page
bookToC = true

# (Optional) If you have enabled BookComments for the site, you can disable it for specific pages.
bookComments = true

# (Optional) Set to 'false' to exclude page from search index.
bookSearchExclude = true

# (Optional) Set explicit href attribute for this page in a menu (if BookMenuBundle not set)
bookHref = ''
```

### Partials

There are layout partials available for you to easily override components of the theme in `layouts/partials/`.

In addition to this, there are several empty partials you can override to easily add/inject code.

| Empty Partial                                      | Placement                                   |
| -------------------------------------------------- | ------------------------------------------- |
| `layouts/partials/docs/inject/head.html`           | Before closing `<head>` tag                 |
| `layouts/partials/docs/inject/body.html`           | Before closing `<body>` tag                 |
| `layouts/partials/docs/inject/footer.html`         | After page footer content                   |
| `layouts/partials/docs/inject/menu-before.html`    | At the beginning of `<nav>` menu block      |
| `layouts/partials/docs/inject/menu-after.html`     | At the end of `<nav>` menu block            |
| `layouts/partials/docs/inject/content-before.html` | Before page content                         |
| `layouts/partials/docs/inject/content-after.html`  | After page content                          |
| `layouts/partials/docs/inject/toc-before.html`     | At the beginning of table of contents block |
| `layouts/partials/docs/inject/toc-after.html`      | At the end of table of contents block       |

### Extra Customisation

| File                     | Description                                                                           |
| ------------------------ | ------------------------------------------------------------------------------------- |
| `static/favicon.png`     | Override default favicon                                                              |
| `assets/_custom.scss`    | Customise or override scss styles                                                     |
| `assets/_variables.scss` | Override default SCSS variables                                                       |
| `assets/_fonts.scss`     | Replace default font with custom fonts (e.g. local files or remote like google fonts) |
| `assets/_colors.scss`    | Change the default color schemes |
| `assets/mermaid.json`    | Replace Mermaid initialization config                                                 |

### Plugins

There are a few features implemented as plugable `scss` styles. Usually these are features that don't make it to the core but can still be useful.

| Plugin                            | Description                                                 |
| --------------------------------- | ----------------------------------------------------------- |
| `assets/plugins/_numbered.scss`   | Makes headings in markdown numbered, e.g. `1.1`, `1.2`      |
| `assets/plugins/_scrollbars.scss` | Overrides scrollbar styles to look similar across platforms |

To enable plugins, add `@import "plugins/{name}";` to `assets/_custom.scss` in your website root.

### Hugo Internal Templates

There are a few hugo templates inserted in `<head>`

- [Google Analytics](https://gohugo.io/templates/internal/#google-analytics)
- [Open Graph](https://gohugo.io/templates/internal/#open-graph)

To disable Open Graph inclusion you can create your own empty file `\layouts\_internal\opengraph.html`.
In fact almost empty not quite empty because an empty file looks like absent for HUGO. For example:
```
<!-- -->
```

## Versioning

This theme follows a simple incremental versioning. e.g. `v1`, `v2` and so on. There might be breaking changes between versions.

If you want lower maintenance, use one of the released versions. If you want to live on the bleeding edge of changes, you can use the `main` branch and update your website when needed.

## Contributing

Contributions are welcome! Please make an issue or pull request if there are any changes you'd like to see.

## Credits

A large portion of Amethyst's code base can be derived from the following two projects. Original attribution goes to the creators of these projects; I just put them together, squashed all the bugs, and customized the styles to fit my needs for Amethyst.
 - [Hugo Book](https://github.com/alex-shpak/hugo-book)
 - [Quartz](https://github.com/jackyzha0/quartz)
