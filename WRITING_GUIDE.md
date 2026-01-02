# Writing Blog Posts - Quick Guide

Your Jekyll site is now set up for easy blog writing! No more copying HTML files around.

## Quick Start

### 1. Create a New Post

Create a file in `_posts/` with this naming format:
```
_posts/YYYY-MM-DD-post-title.md
```

Example: `_posts/2025-01-02-my-awesome-post.md`

### 2. Add Front Matter

Every post needs front matter at the top:

```markdown
---
layout: post
title: "Your Post Title"
date: 2025-01-02
---
```

### 3. Write Your Content

Write in Markdown below the front matter:

```markdown
---
layout: post
title: "My Great Post"
date: 2025-01-02
---

This is the intro paragraph that appears in the blog list.

<!--excerpt-->

Everything after this comment is the full post content.

## Headings Work

You can use **bold**, *italic*, and `code`.

### Code Blocks

```python
def hello():
    print("Hello, world!")
```

### Lists

- Item one
- Item two
- Item three

### Links

[Link text](https://example.com)
```

## Workflow

### Local Development

1. **Write your post** in `_posts/`
2. **Preview locally**:
   ```bash
   bundle exec jekyll serve
   ```
   Open http://localhost:4000
3. **View your changes** live as you edit

### Publishing

1. **Commit your changes**:
   ```bash
   git add _posts/2025-01-02-my-post.md
   git commit -m "Add new post: My Post Title"
   ```

2. **Push to GitHub**:
   ```bash
   git push origin gh-pages
   ```

3. **Done!** GitHub Pages automatically builds and deploys your site in 1-2 minutes.

## Markdown Cheat Sheet

```markdown
# Heading 1
## Heading 2
### Heading 3

**bold text**
*italic text*
`inline code`

[link text](https://url.com)

![image alt text](/path/to/image.jpg)

> Blockquote

- Unordered list item
- Another item

1. Ordered list item
2. Another item

```code block```
```

## Tips

- **Excerpt**: Use `<!--excerpt-->` to control what shows on the blog index page
- **Drafts**: Keep unpublished posts in `_drafts/` (without date in filename)
- **Images**: Put images in `assets/img/` and reference with `/assets/img/photo.jpg`
- **Local URLs**: Use `{{ site.url }}` for absolute URLs or just `/path` for relative

## File Structure

```
├── _posts/                 # Your blog posts (Markdown)
│   └── 2025-01-02-title.md
├── _layouts/               # Page templates
│   └── post.html          # Blog post template
├── _includes/              # Reusable components
├── _site/                  # Generated site (don't edit)
├── assets/                 # CSS, JS, images
├── blog.html              # Blog index page
└── index.html             # Homepage
```

## Troubleshooting

### Site not updating on GitHub Pages?
- Wait 1-2 minutes for the build
- Check your repository settings → Pages section
- Branch should be `gh-pages`

### Post not showing up?
- Check filename format: `YYYY-MM-DD-title.md`
- Check date in front matter isn't in the future
- Make sure file is in `_posts/` directory

### Local server won't start?
```bash
bundle install
bundle exec jekyll serve
```

## What Changed?

**Before:**
- Write in separate repo
- Generate HTML/CSS manually
- Copy files to `blog/` directory
- Multiple repos to manage

**After:**
- Write Markdown in `_posts/`
- Commit and push
- GitHub Pages builds automatically
- Single repository

## Next Steps

1. Delete your separate blog repository (after backing up any drafts)
2. Start writing new posts in `_posts/`
3. Consider modernizing the design later (optional)

Happy writing! 🎉
