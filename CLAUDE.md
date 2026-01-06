# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build and Development Commands

```bash
# Install Jekyll (one-time setup)
gem install jekyll rouge

# Run local development server
jekyll serve
# Site will be available at http://localhost:4000
```

## Deployment

- **Live site**: https://www.the-ecg.org (custom domain)
- **GitHub Pages**: https://embodied-computation-group.github.io/
- **Default branch**: `master` (not main)
- Builds automatically on push to master

## Architecture

This is a Jekyll-based static site for the Embodied Computation Group, deployed via GitHub Pages.

### Content Collections

**People** (`_people/`): Lab member profiles using the `profile` layout
- Required frontmatter: `name`, `position`, `avatar`, `joined`
- Position values: `pi`, `postdoc`, `gradstudent`, `researchstaff`, `visiting`, `alumni`, `inactive`
- Use `inactive` to hide profiles without deleting them
- Avatar images go in `images/people/`

**Alumni-specific frontmatter**:
```yaml
position: alumni
joined: 2019
left: 2024
former_role: Postdoctoral Fellow
current_position: Senior Data Scientist, Company Name
```

**Posts** (`_posts/`): Blog posts using date-prefixed filenames (YYYY-MM-DD-title.md)
- Required frontmatter: `title`, `description`, `categories`
- Use `categories: blog` for blog posts

**News** (`_data/news.yml`): Homepage news items with `date` and `details` fields

### Key Configuration

`_config.yml` defines:
- Site metadata (name, description)
- Navigation menu items in `nav` array
- URL structure via `permalink`
- Collection settings for `people`

### Layouts

- `default.html`: Base layout with navbar
- `page.html`: Standard content pages
- `post.html`: Blog posts
- `profile.html`: People profiles

### Images

- `images/people/`: Profile photos
- `images/logo/`: Logo variants
  - `lablogo_2024.png`: Full logo with text (used on homepage, social sharing)
  - `lablogo_ecg_trans.png`: Transparent logo without text (used in navbar, favicon)
- `images/others/`: Research page images and other assets

### Publications

The publications page (`publications.md`) automatically fetches from Zotero API:
- Zotero User ID: `5500260`
- Public library at: https://www.zotero.org/ecg_lab/publications
- Grouped by year, sorted newest first

### Adding Content

New lab member: Create `_people/firstname_lastname.md` with frontmatter, add photo to `images/people/`

New blog post: Create `_posts/YYYY-MM-DD-title.md` with frontmatter

New publication: Add to Zotero library (auto-syncs to website)

New news item: Add entry to `_data/news.yml`

New research image: Add to `images/others/`, reference in `research.md`

## Important Rules

- NEVER add Claude Code attribution or "Generated with Claude Code" to commit messages or code
- NEVER add "Co-Authored-By: Claude" or similar attribution lines
- Keep commit messages clean and conventional without AI attribution footers
