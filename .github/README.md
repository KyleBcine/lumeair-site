# LumeAir website

The source of the LumeAir website, published with GitHub Pages.

**Read it at [kylebcine.github.io/lumeair-site](https://kylebcine.github.io/lumeair-site/).**

> The pages here are Markdown files that GitHub Pages turns into the website. Opened on GitHub, they show as plain source and some things don't work there. In particular, the **Install firmware** button on the build guide only works on the website.

## Pages

| Page | What's on it | Source |
|---|---|---|
| [Home](https://kylebcine.github.io/lumeair-site/) | What LumeAir is and what it measures | [`index.md`](../index.md) |
| [Build your own LumeAir](https://kylebcine.github.io/lumeair-site/Build) | Parts, board, case and firmware, step by step | [`Build.md`](../Build.md) |
| [Support](https://kylebcine.github.io/lumeair-site/Support) | Setup, readings, alerts, Home Assistant and factory reset | [`Support.md`](../Support.md) |
| [Privacy policy](https://kylebcine.github.io/lumeair-site/Privacy) | What the LumeAir Home app stores and shares | [`Privacy.md`](../Privacy.md) |

## What's in this repository

| Path | What it does |
|---|---|
| `index.md`, `Build.md`, `Support.md`, `Privacy.md` | The pages |
| `_layouts/default.html` | The template every page uses: header, navigation and footer |
| `assets/css/lumeair.css` | The site's styles, in light and dark mode |
| `_includes/head-custom.html` | Loads the Install firmware button on the build guide, and hides the "reading on GitHub" notes on the website |
| `_config.yml` | The site's name and description, used in browser tabs and link previews |
| `firmware/` | The sensor firmware releases that the LumeAir Home app and the build guide install from |

## Related

- [LumeAir hardware](https://github.com/KyleBcine/lumeair-hardware): the board, parts list and case design files
- [LumeAir for Home Assistant](https://github.com/KyleBcine/lumeair-homeassistant): the Home Assistant integration
