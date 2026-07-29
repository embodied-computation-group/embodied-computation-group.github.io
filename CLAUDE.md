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
- Optional `header-img`: thumbnail on `/blog`. Path has **no** leading slash
  (`blog.md` prepends one); image paths in the post body **do** need one.
- Optional `author` (byline) and `author_url` (links the byline, usually to the
  writer's profile, e.g. `/people/micah_allen/`). Both optional: posts without
  `author` render date-only as before.

**Posts with citations** (pandoc source): posts drafted in pandoc markdown with
`[@key]` citations are converted to a Jekyll post with citations baked in as
static HTML, since Jekyll does not run citeproc. Do not hand-number citations.

```bash
# 1. Render an HTML fragment with citations resolved (no -s, no --embed-resources)
pandoc blog-post-draft.md --citeproc --bibliography=references.bib \
  --csl=nature.csl -t html --wrap=preserve -o fragment.html

# 2. Drop the leading <h1> (post.html renders page.title itself),
#    rewrite src="img/..." to src="/images/post/<slug>/...",
#    prepend the frontmatter block, save as _posts/YYYY-MM-DD-<slug>.md
# 3. Copy the referenced figures into images/post/<slug>/
```

`style.scss` styles pandoc's output under `.post`: `figure`/`figcaption`,
`.citation sup`, `.csl-bib-body`/`.csl-entry` (hanging-indent reference list),
`.hero` (full-width header image) and `.disclaimer`. Keep those class names if
changing the pipeline. Existing pre-pandoc posts instead use markdown images
followed by an italic caption line; both styles coexist.

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
