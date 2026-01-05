# Embodied Computation Group Website

This is the repository for the [Embodied Computation Group](https://embodied-computation-group.github.io/) webpage. We use Jekyll to run our GitHub page.

## Run the page locally using Jekyll

To run locally, follow instruction [here](https://jekyllrb.com/) to install Jekyll then run `jekyll serve` to see in `localhost:4000`. Here is a brief install guideline:

```bash
sudo gem install jekyll
sudo gem install rouge
jekyll serve
```

## Editing the lab website

Below, we explain how to edit the lab webpage.

### Add posts

All posts are located in `_posts` folder. Each post can be written in markdown format. You need to include headers before writing: `title`, `description` and `categories`. See the following example:

```markdown
---
title: New paper on interoception
description: Our latest paper on cardiac interoception is now published
categories: blog
---
```

### How to add posts

- **Directly edit on Github**: Go to `_posts` and click `New file` then create a markdown file e.g. `2026-01-05-post-name.md` and start writing.

- **Clone the repository**: Clone the repo, add new post file, commit and push.

The changes will take approximately 30 seconds to render.

### Add yourself

Create a file named `<firstname>_<lastname>.md` in the `_people` folder with the following header:

```markdown
---
name: Your Name
position: postdoc
avatar: your_photo.jpg
twitter: your_handle
joined: 2026
---
```

Position options: `pi`, `postdoc`, `gradstudent`, `researchstaff`, `visiting`, `alumni`

The avatar should be placed in `images/people/` folder.

### Add new publications

Publications are listed in `publications.md`. Add new publications following the existing format.

### Add news

News items are in `_data/news.yml`. Add new items following the YAML format:

```yaml
- date: 2026-01-05
  details: "Your news item here. You can include <a href='url'>links</a>."
```

## Getting Help

- For technical issues, contact Dr. Micah Allen
- Test locally with `jekyll serve` before pushing changes

## Credits

This website template is adapted from the [Kording Lab website](https://github.com/KordingLab/KordingLab.github.io).
