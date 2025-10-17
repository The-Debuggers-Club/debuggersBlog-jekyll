# The Debuggers Blog (Jekyll)

A modern, responsive Jekyll site for The Debuggers (ISc. BHU Coding Club). This repository contains a Jekyll site located in the `debuggersBlog-jekyll/` subfolder and is configured for GitHub Pages.

- Live site: `https://rajsriv.github.io/debuggersBlog-jekyll/`
- Source folder: `./debuggersBlog-jekyll`

## Features
- Clean, typography-first design with responsive layout
- Home page with featured section, recent posts, and sidebar
- Posts, pages, and an `events` collection
- SEO tags (`jekyll-seo-tag`), RSS feed (`jekyll-feed`), and sitemap (`jekyll-sitemap`)
- Mobile navigation (hamburger + overlay)
- Easy theming via `assets/css/main.css`

## Tech Stack
- Jekyll (Ruby)
- GitHub Pages-compatible plugins: `jekyll-seo-tag`, `jekyll-feed`, `jekyll-sitemap`

## Repository Structure
```
.
├─ debuggersBlog-jekyll/
│  ├─ _config.yml           # Site configuration (url/baseurl, collections, navigation, social)
│  ├─ Gemfile               # Ruby dependencies
│  ├─ index.html            # Home page (uses `home` layout)
│  ├─ _data/                # Data files (navigation, social)
│  ├─ _includes/            # Reusable snippets (header, footer, contact form)
│  ├─ _layouts/             # Page layouts (default, home, page, post)
│  ├─ _pages/               # Static pages (about, contact, events)
│  ├─ _posts/               # Blog posts (YYYY-MM-DD-title.md)
│  └─ assets/
│     ├─ css/main.css       # Global styles
│     └─ js/main.js         # Mobile menu behavior
└─ README.md                # This file
```

## Getting Started (Local Development)

Prerequisites:
- Ruby (2.7+ recommended)
- Bundler (`gem install bundler`)

Install and run:
```bash
# Clone your fork
git clone https://github.com/rajsriv/debuggersBlog-jekyll.git
cd debuggersBlog-jekyll/debuggersBlog-jekyll

# Install gems
bundle install

# Serve locally (defaults to http://127.0.0.1:4000)
bundle exec jekyll serve
```

Tip: If you run from the repo root, `cd debuggersBlog-jekyll` first as shown above.

## Configuration
Main settings live in `debuggersBlog-jekyll/_config.yml`:
- `title`, `tagline`, `description`: Site metadata
- `url`, `baseurl`: Deployment URLs
  - For this project: `url: "https://rajsriv.github.io"`, `baseurl: "/debuggersBlog-jekyll"`
- `collections`: Defines `events` as an output collection
- `defaults`: Default layouts for posts/pages/events
- `plugins`: `jekyll-feed`, `jekyll-sitemap`, `jekyll-seo-tag`
- `social`: Handles social links used in the header
- `navigation`: Primary nav items
- `featured_post`, `about_text`: Content used on the home layout

Assets are referenced using Liquid filters with the `baseurl` applied, e.g.:
```html
<link rel="stylesheet" href="{{ '/assets/css/main.css' | relative_url }}">
<script src="{{ '/assets/js/main.js' | relative_url }}"></script>
```

## Content
- Posts: Add Markdown files to `debuggersBlog-jekyll/_posts/` using the naming convention `YYYY-MM-DD-title.md` with front matter like:
```yaml
---
layout: post
title: "My New Post"
date: 2025-10-17
category: "Event"
---
```
- Pages: Add Markdown files to `debuggersBlog-jekyll/_pages/` with front matter `layout: page` and a permalink if desired.
- Events: Add Markdown files to `debuggersBlog-jekyll/_events/` (folder created if needed) with `layout: event` (as defined in defaults) and front matter as appropriate.

## Deployment (GitHub Pages)
This repository deploys a Jekyll site from a subfolder.

1) In GitHub → Settings → Pages:
- Source: “Deploy from a branch”
- Branch: `main`
- Folder: `/debuggersBlog-jekyll`

2) In `debuggersBlog-jekyll/_config.yml`, ensure:
```yaml
url: "https://rajsriv.github.io"
baseurl: "/debuggersBlog-jekyll"
```

3) Commit and push. Wait 1–2 minutes for Pages to build, then visit:
- `https://rajsriv.github.io/debuggersBlog-jekyll/`

Alternative: If you prefer deploying from the repo root or `/docs`, move the site folder accordingly and update Pages settings and `baseurl`.

## Customization
- Styles: Edit `debuggersBlog-jekyll/assets/css/main.css`
- Header/Footer: Edit includes in `debuggersBlog-jekyll/_includes/`
- Navigation & Social: Edit data files in `debuggersBlog-jekyll/_data/`
- Home layout: `debuggersBlog-jekyll/_layouts/home.html`
- Default layout (adds CSS/JS and includes): `debuggersBlog-jekyll/_layouts/default.html`

## Troubleshooting
- CSS/JS not loading (404/blocked):
  - Confirm Pages source folder is `/debuggersBlog-jekyll` (or wherever the site lives)
  - Ensure `_config.yml` has correct `url` and `baseurl`
  - Verify assets resolve at: `https://<user>.github.io/<repo>/assets/css/main.css`
  - Hard refresh or clear cache
- Build errors locally: Run `bundle update` and re-try `bundle exec jekyll serve`
- Plugins: Only GitHub Pages-safe plugins are used here (no custom plugins required)

## Contributing
Pull requests are welcome. For larger changes, please open an issue to discuss what you’d like to change.

## License
Specify your project’s license (e.g., MIT). Create a `LICENSE` file if needed.

## Acknowledgements
- Jekyll community and GitHub Pages
- `jekyll-seo-tag`, `jekyll-feed`, `jekyll-sitemap` plugin authors
