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

## Architecture

This is a Jekyll-based static site for the Embodied Computation Group, deployed via GitHub Pages to https://embodied-computation-group.github.io/

### Content Collections

**People** (`_people/`): Lab member profiles using the `profile` layout
- Required frontmatter: `name`, `position`, `avatar`, `joined`
- Position values: `pi`, `postdoc`, `gradstudent`, `researchstaff`, `visiting`, `alumni`
- Avatar images go in `images/people/`

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

### Adding Content

New lab member: Create `_people/firstname_lastname.md` with frontmatter, add photo to `images/people/`

New blog post: Create `_posts/YYYY-MM-DD-title.md` with frontmatter

New publication: Edit `publications.md` directly

New news item: Add entry to `_data/news.yml`
