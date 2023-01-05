---
title: "Deploying Amethyst to the Web"
tags:
- setup
aliases:
- hosting
---

## Hosting on GitHub Pages
Amethyst is designed to be effortless to deploy. If you forked and cloned Amethyst directly from the repository, everything should already be good to go! Follow the steps below.

### Enable GitHub Actions
By default, GitHub disables workflows from running automatically on Forked Repostories. Head to the 'Actions' tab of your forked repository and Enable Workflows to setup deploying your site!

![Enable GitHub Actions](/setup/images/github-actions.png)*Enable GitHub Actions*

### Enable GitHub Pages

Head to the 'Settings' tab of your forked repository and go to the 'Pages' tab.

1. (IMPORTANT) Set the source to deploy from `master` (and not `hugo`) using `/ (root)`
2. Set a custom domain here if you have one!

![Enable GitHub Pages](/setup/images/github-pages.png)*Enable GitHub Pages*

### Pushing Changes
To see your changes on the internet, we need to push it them to GitHub. Amethyst is a `git` repository so updating it is the same workflow as you would follow as if it were just a regular software project.

```shell
# Navigate to Amethyst folder
cd <path-to-amethyst>

# Commit all changes
git add .
git commit -m "message describing changes"

# Push to GitHub to update site
git push origin main
```

Note: we specifically push to the `main` branch here. Our GitHub action automatically runs everytime a push to is detected to that branch and then updates the `deploy` branch for redeployment.

### Setting up the Site
Now let's get this site up and running. Never hosted a site before? No problem. Have a fancy custom domain you already own or want to use a subdomain? That's easy too.

> Don't want to use GitHub Pages? Continue following the instructions below, and simply point your hosting solution to serve the `deploy` branch with no additional build steps required.

Here, we take advantage of GitHub's free page hosting to deploy our site. Change `baseURL` in `/config.toml`. 

Make sure that your `baseURL` has a trailing `/`!

[Reference `config.yaml` here](https://github.com/64bitpandas/amethyst/blob/main/config.yaml)

```yaml
baseURL: "https://<YOUR-DOMAIN>/"
```

If you are using this under a subdomain (e.g. `<YOUR-GITHUB-USERNAME>.github.io/amethyst/`), include the trailing `/`. **You need to do this especially if you are using GitHub!**

```yaml
baseURL: "https://<YOUR-GITHUB-USERNAME>.github.io/amethyst/"
```

Change `cname` in `/.github/workflows/deploy.yaml`. Again, if you don't have a custom domain to use, you can use `<YOUR-USERNAME>.github.io`.

Please note that the `cname` field should *not* have any path `e.g. end with /amethyst` or have a trailing `/`.

[Reference `deploy.yaml` here](https://github.com/64bitpandas/amethyst/blob/main/.github/workflows/deploy.yaml)

```yaml {title=".github/workflows/deploy.yaml"}
- name: Deploy  
  uses: peaceiris/actions-gh-pages@v3  
  with:  
	github_token: ${{ secrets.GITHUB_TOKEN }} # this can stay as is, GitHub fills this in for us!
	publish_dir: ./public  
	publish_branch: deploy
	cname: <YOUR-DOMAIN>
```

Have a custom domain? [Learn how to set it up with Amethyst ](setup/custom%20Domain.md).

### Ignoring Files
Only want to publish a subset of all of your notes? Don't worry, Amethyst makes this a simple two-step process.

❌ [Excluding pages from being published](setup/ignore%20notes.md)

---

Now that your site is live, let's figure out how to make Amethyst really *yours*!

> Step 6: 🎨 [Customizing Amethyst](setup/config.md)

Having problems? Checkout our [FAQ and Troubleshooting guide](setup/troubleshooting.md).
