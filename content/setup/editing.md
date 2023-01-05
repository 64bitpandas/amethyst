---
title: "Editing Content"
tags:
- setup
weight: -4
---

## Editing 
Amethyst runs on top of [Hugo](https://gohugo.io/) so all notes are written in [Markdown](https://www.markdownguide.org/getting-started/).

### Folder Structure
Here's a rough overview of what's what.

**All notes you want to publish should go in the `/content` folder.** To make edits, you can open any of the files and make changes directly and save it. You can organize content into any subfolder you'd like.

**To edit the main home page, open `/content/_index.md`.**

To create a link between notes in your garden, just create a normal link using Markdown pointing to the document in question. Please note that **all links should be relative to the root `/content` path**. 

```markdown
For example, I want to link this current document to `setup/config.md`.
[A link to the config page](setup/config.md)
```

Similarly, you can put local images anywhere in the `/content` folder.

```markdown
Example image (source is in content/setup/images/example.png)
![Example Image](/content/setup/images/example.png)
```

You can also use wikilinks if that is what you are more comfortable with!

### Front Matter
Hugo is picky when it comes to metadata for files. Make sure that your title is double-quoted and that you have a title defined at the top of your file in the front matter like so. You can also add tags here as well.

```yaml
---
title: "Example Title"
tags:
- example-tag
---

Rest of your content here...
```

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


### Obsidian
Amethyst is built especially for use with [Obsidian](http://obsidian.md/) as a text editor. 

See below for more information:

> 🔗 Step 3: [How to setup your Obsidian Vault to work with Amethyst](setup/obsidian.md)

## Previewing Changes
This step is purely optional and mostly for those who want to see the published version of their digital garden locally before opening it up to the internet. This is *highly recommended* but not required.

> 👀 Step 4: [Preview Changes](setup/preview%20changes.md)

For those who like to live life more on the edge, viewing the garden through Obsidian gets you pretty close to the real thing.

## Publishing Changes
After you've finished editing your notes, you can publish them to the internet!

> 🌍 Step 5: [Hosting Amethyst online!](setup/hosting.md)

Having problems? Check out our [FAQ and Troubleshooting guide](setup/troubleshooting.md).
