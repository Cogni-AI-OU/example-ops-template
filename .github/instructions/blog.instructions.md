---
description: 'Blog post content creation standards and front matter requirements'
applyTo:
  - 'blog/**/*.md'
  - 'posts/**/*.md'
  - 'content/**/*.md'
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

## Content Guidelines

Blog posts should follow all general markdown formatting rules specified in `markdown.instructions.md`, including:

- Proper heading hierarchy (H2, H3, etc.)
- Appropriate use of lists, code blocks, and tables
- Line length limits (120 characters)
- Proper whitespace and formatting

## Headings

Do not use an H1 heading in the blog post content, as this will be generated based on the `post_title` field in the front matter.

## Validation

- Ensure all required front matter fields are present and correctly formatted.
- Run `pre-commit run markdownlint -a` to verify compliance with markdown linting rules.
- Verify that categories reference valid entries from `/categories.txt`.
