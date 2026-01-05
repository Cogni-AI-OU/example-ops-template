---
description: 'General documentation and markdown content standards'
applyTo: '**/*.md'
---

# Markdown Instructions

These guidelines apply to all markdown files in the repository. For blog-specific requirements
(including front matter fields), see `blog.instructions.md`.

## Markdown Content Rules

The following markdown content rules are enforced in the validators:

1. **Headings**: Use appropriate heading levels (H1, H2, H3, etc.) to structure your content.
   Use H1 for the main document title, and H2/H3 for sections and subsections.
2. **Lists**: Use bullet points or numbered lists for lists. Ensure proper indentation and spacing.
3. **Code Blocks**: Use fenced code blocks for code snippets. Specify the language for syntax highlighting.
4. **Links**: Use proper markdown syntax for links. Ensure that links are valid and accessible.
5. **Images**: Use proper markdown syntax for images. Include alt text for accessibility.
6. **Tables**: Use markdown tables for tabular data. Ensure proper formatting and alignment.
7. **Line Length**: Limit line length to 120 characters to align with project linting.
8. **Whitespace**: Use appropriate whitespace to separate sections and improve readability.
9. **Front Matter**: YAML front matter is optional for general documentation. See `blog.instructions.md`
   for blog-specific front matter requirements.

## Formatting and Structure

Follow these guidelines for formatting and structuring your markdown content:

- **Headings**: Use `##` for H2 and `###` for H3. Ensure that headings are used in a
  hierarchical manner. Recommend restructuring if content includes H4, and more strongly
  recommend for H5.
- **Lists**: Use `-` for bullet points and `1.` for numbered lists. Indent nested lists with two spaces.
- **Code Blocks**: Use triple backticks (```) to create fenced code blocks. Specify the
  language after the opening backticks for syntax highlighting (e.g., `csharp`).
- **Links**: Use `[link text](URL)` for links. Ensure that the link text is descriptive and the URL is valid.
  - If a URL is long or reused, prefer reference-style links placed at the end of the file
    after `<!-- Named links -->`.
- **Images**: Use `![alt text](image URL)` for images. Include a brief description of the image in the alt text.
- **Tables**: Use `|` to create tables. Ensure that columns are properly aligned and headers are included.
- **Line Length**: Break lines at 120 characters to match `.markdownlint.yaml`. Use soft line breaks for long paragraphs.
- **Whitespace**: Use blank lines to separate sections and improve readability. Avoid excessive whitespace.

## Project Markdown Lint Rules

The project enforces the following markdownlint rules:

- Keep line length <=120 characters.
- Surround headings and lists with blank lines; fence code blocks with blank lines.
- Avoid trailing spaces; ensure a single trailing newline.
- Avoid hard tabs (MD010/no-hard-tabs).
- Headings must have blank lines around them (MD022/blanks-around-headings).
- Lists must be surrounded by blank lines (MD032/blanks-around-lists).
- Fenced code blocks need surrounding blank lines (MD031/blanks-around-fences) and a language.
- Files end with a single newline (MD047/single-trailing-newline).

## Validation

- Repository rules come from `.markdownlint.yaml`.
- Run `pre-commit run markdownlint -a` to verify locally.
