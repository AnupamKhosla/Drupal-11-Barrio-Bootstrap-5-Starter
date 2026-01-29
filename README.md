# Olivero Dark Mode – Drupal Theme

Custom Drupal theme extending **Olivero** to add proper **dark mode support** and optional manual toggle.

## Project Goals

* Add reliable dark mode to Olivero (Drupal 11)
* Support system preference (`prefers-color-scheme`)
* Optional manual dark/light toggle
* Centralized CSS variable overrides
* No hacks to core Olivero files

## Tech Stack

* Drupal 11
* Olivero base theme
* DDEV local environment
* Custom theme (sub-theme of Olivero)

## How Dark Mode Works

Drupal 11 Olivero no longer ships full dark-mode overrides.
This project adds:

* Dark color variable overrides
* Component-level dark styles
* Optional JS toggle (adds class or data-attribute to `<html>`)

Example approach:

```css
@media (prefers-color-scheme: dark) {
  :root {
    --color--gray-5: #f5f5f5;
    --color--gray-100: #0f172a;
    /* etc */
  }
}

html[data-theme="dark"] {
  /* Manual override */
}
```

## Local Setup (DDEV)

```bash
ddev start
ddev composer install
ddev drush cr
```

## Theme Structure

```
web/themes/custom/olivero_dark/
  olivero_dark.info.yml
  olivero_dark.libraries.yml
  css/
    dark.css
  js/
    toggle.js
```

## Git Setup (from Mac Terminal)

### 1. Initialize repo locally

```bash
cd /path/to/your/project
git init
git add .
git commit -m "Initial Olivero dark mode theme"
```

### 2. Create remote repo (GitHub)

Option A — Using GitHub CLI (recommended):

```bash
brew install gh
gh auth login
gh repo create olivero-dark-mode --public --source=. --remote=origin --push
```

Option B — Manually on GitHub website:

1. Create empty repo on GitHub
2. Then run:

```bash
git remote add origin git@github.com:YOURUSER/olivero-dark-mode.git
git branch -M main
git push -u origin main
```

## What NOT to Commit

* `vendor/`
* `web/sites/*/files`
* `settings.php` with secrets
* `.ddev/.db`

## Roadmap

* [ ] Add full variable dark palette
* [ ] Add manual toggle UI
* [ ] Persist user preference (localStorage)
* [ ] Contrast + accessibility tuning

## License

GPL-2.0-or-later (same as Drupal)
