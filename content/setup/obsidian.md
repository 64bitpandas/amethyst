---
title: "Obsidian Vault Integration"
tags:
- setup
weight: -3
---

## Setup
Obsidian is the preferred way to use Amethyst. You can either create a new Obsidian Vault or link one that your already have.

### New Vault
If you don't have an existing Vault, [download Obsidian](https://obsidian.md/) and create a new Vault in the `/content` folder that you created and cloned during the [setup](setup/setup.md) step.

### Linking an existing Vault (simple)
The easiest way to use an existing Vault is to copy all of your files (directory and hierarchies intact) into the `/content` folder.

### Linking an existing Vault (using git)
If you're editing in an existing vault and don't want to have to keep copying your files over, one solution is to create a new Git repository for just the notes you want to publish.

Then, in both your vault and in Amethyst, run the following command, replacing the link with one to your new repository:
```bash
git submodule add https://github.com/<YOUR_USERNAME>/<REPO_NAME> content
```

## Settings
Now that you've added your notes to Amethyst, let's fix some settings so that they play well.

1. Under Options > Files and Links, set the New link format to always use Absolute Path in Vault.
2. Go to Settings > Files & Links > Turn "on" automatically update internal links.

![Obsidian Settings](/setup/images/obsidian-settings.png)*Obsidian Settings*

## Templates
Inserting front matter everytime you want to create a new Note gets annoying really quickly. Luckily, Obsidian supports templates which makes inserting new content really easily.

**If you decide to overwrite the `/content` folder completely, don't remove the `/content/templates` folder!**

Head over to Options > Core Plugins and enable the Templates plugin. Then go to Options > Hotkeys and set a hotkey for 'Insert Template' (I recommend `[cmd]+T`). That way, when you create a new note, you can just press the hotkey for a new template and be ready to go!

> 👀 Step 4: [Preview Changes](setup/preview%20changes.md)