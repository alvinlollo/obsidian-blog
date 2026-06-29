---
title: How I created this blog
author: Alvin Vilaythong
created: 2026-06-20
modified: 2026-06-29
tags:
  - Tutorials
  - Discursive
date: 2026-06-20
---
This blog post is how I made this Hugo blog post and styled it to my liking as well as how I made this connect with my note-taking app to automatically make new posts.

If you want to see the code of my blog, take a look on GitHub: https://github.com/alvinlollo/alvin.vilaythong.us This blog post is created to show what programs that is used to make it work.

## Programs I used

The programs that I used to generate the web page is [Hugo](https://goHugo.io/) with the [Blowfish](https://github.com/nunocoracao/blowfish) theme, [Obsidian](https://obsidian.md/), [git](https://git-scm.com/), [GitHub](https://github.com) and [Syncthing](https://syncthing.net/). 

Obsidian is my note-taking app, Obsidian uses Markdown to display text in rich text using prefixes. e.g: `#` for headings, `**` For bolding and italics, `== ==` For highlighting, `>` For quotes, etc.
Hugo is a program that generates static HTML code from markdown files. Using [Syncthing](https://syncthing.net/) I am able to automatically transfer files to my server running Hugo to generate the HTML files for my blog. I use the Blowfish Hugo theme as a template for my blog. 
[Git](https://git-scm.com/) is a version control software that is used by developers for open source projects. It is usually used in the command line. A repository is a term used in git to declare that project they are in, the shorthand term "repo" is typically used by developers.
## How I set up Hugo 

In Hugo  `content/posts/` is a git submodule pointing to an Obsidian vault repository. That means post content lives in a separate repository and needs a `git submodule update --remote --init content/posts` to sync. Commit and push happens inside the submodule first, then the root repo tracks the submodule pointer.

The root `Hugo.toml` is only three lines - minimal. All the real config lives in `config/_default/` with separate files for parameters, markup, menus, languages, and modules. The theme is Blowfish v2.103.0 tucked away in `themes/blowfish/`.

There are two build output directories: `built-site/` and `public_new/`. The `built-site/` directory has the `CNAME` file for the custom domain, so that's the deployment target for GitHub Pages on the `gh-pages` branch. The `public_new/` directory appears to be an experimental secondary build.

## The auto-commit daemon

The most interesting part is the auto-commit system. Four scripts in `scripts/` get wired up as systemd services. One watches the Obsidian vault for changes and auto-commits. Another watches the Hugo blog directory. A third polls the submodule every 60 seconds. A fourth orchestrates all three. If something breaks, check `/var/log/git-auto-commit.log`. The installation instructions are in `docs/systemd.md`.
## What happens when it commits

Using the power of GitHub actions, I don't need to build my HTML files on my server. Using GitHub actions, it automatically retrieves my Obsidian files, builds, and posts my blog onto GitHub pages that is serving my content. On my domain name provider (Cloudflare) I have put the DNS record pointing to GitHub pages IP address so that anyone who visits https://alvin.vilaythong.us will see my blog hosted on GitHub Pages.
