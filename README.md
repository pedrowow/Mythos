# Mythos — A Greek Mythology Atlas

A personal reading site for Greek mythology: narrative-driven stories, connected characters, readable on any device.

## Structure

```
index.html          — home page with story grid
characters.html     — full character index
css/style.css       — all styles
js/progress.js      — reading progress bar
stories/
  chaos.html        — Chaos and the First Void
  titans.html       — The Age of the Titans
  titanomachy.html  — The Titanomachy
characters/
  chaos.html
  gaia.html
  uranus.html
  cronus.html
  rhea.html
  zeus.html
  prometheus.html
  nyx.html
```

## Deploy to GitHub Pages

1. Create a new repository on GitHub (e.g. `mythos`)
2. Push this folder to the `main` branch:

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/mythos.git
git push -u origin main
```

3. Go to **Settings → Pages** in the repository
4. Under "Source", select `main` branch, root folder (`/`)
5. Save — your site will be live at `https://YOUR_USERNAME.github.io/mythos/` within a minute

## Adding new stories

Each story follows the same template as the existing ones:
- Breadcrumb navigation at the top
- Hero title + subtitle
- Wikipedia Commons image (free to use)
- Story body with `.char-link` for character links and `.story-link` for related stories
- Sidebar with characters and next/previous navigation

Add the new story card to `index.html` in the appropriate section, and add character entries to `characters.html` and `characters/` as needed.

## Image sourcing

All images used are from Wikimedia Commons (public domain). For new stories, search:
- https://commons.wikimedia.org
- Filter by "public domain" or pre-1928 works
- Classical paintings, Greek vase paintings, and 19th-century academic art work well
