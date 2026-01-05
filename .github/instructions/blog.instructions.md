---
description: 'Blog post specific content standards and validation'
applyTo:
  - 'docs/blog/**/*.md'
  - 'blog/**/*.md'
  - 'posts/**/*.md'
---

# Blog Post Instructions

## Front Matter Requirements

All blog posts must include YAML front matter at the beginning of the file with the following required fields:

- `post_title`: The title of the post.
- `author1`: The primary author of the post.
- `post_slug`: The URL slug for the post.
- `microsoft_alias`: The Microsoft alias of the author.
- `featured_image`: The URL of the featured image.
- `categories`: The categories for the post. These categories must be from the list in /categories.txt.
- `tags`: The tags for the post.
- `ai_note`: Indicate if AI was used in the creation of the post.
- `summary`: A brief summary of the post. Recommend a summary based on the content when possible.
- `post_date`: The publication date of the post.

## Content Standards

Blog posts must follow the general markdown content rules defined in `markdown.instructions.md`.

## Validation

- Ensure all required front matter fields are present and properly formatted.
- Verify that categories match those in `/categories.txt`.
- Follow the project's markdown linting rules from `.markdownlint.yaml`.
- Run `pre-commit run markdownlint -a` to verify locally.
