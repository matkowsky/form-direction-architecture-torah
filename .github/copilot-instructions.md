# Copilot Instructions

This repository contains a scholarly research paper about a mathematical-mystical framework for Jewish philosophy. Please follow these guidelines when working with this codebase.

## Repository Overview

This is an academic research project that:
- Addresses theological tensions between Maharal of Prague and Lurianic Kabbalah through mathematical frameworks
- Uses Markdown for all documentation and paper content
- Employs markdownlint for style consistency
- Is currently in draft status and not ready for citation

## Key Files

- `README.md` - Project overview and status
- `MAIN-PAPER.md` - Core theoretical framework
- `ABSTRACT.md` - Paper abstract
- `CONTRIBUTING.md` - Contribution guidelines
- `PART-*.md` - Main paper sections (Literature Review, Mathematical Foundations, Consciousness, Test Cases, Analysis)
- `.markdownlint.yml` - Markdown linting configuration

## Build and Test

### Markdown Linting

```bash
npm install -g markdownlint-cli
markdownlint '**/*.md' --ignore node_modules
```

The repository uses a lenient markdownlint configuration suited for academic content. See `.markdownlint.yml` for details.

### CI Checks

The CI pipeline validates:
1. Markdown linting
2. Link checking
3. Repository structure (required files present)

## Content Guidelines

### Academic Standards
- Maintain scholarly rigor with proper source citations
- Preserve technical precision while ensuring accessibility
- Respect both mathematical and mystical aspects of the research
- Use LaTeX-style notation for mathematical expressions when appropriate

### Markdown Conventions
- Follow existing document structure and formatting
- Use consistent heading hierarchy within each document
- Include proper frontmatter where applicable (title, author, date)
- Maintain the established citation and reference style

### Mathematical Content
- Use inline math with `$...$` notation where supported
- Use display math with `$$...$$` for standalone equations
- Define variables and symbols before using them
- Include units and dimensions where relevant

## What Not to Change

- Do not modify the dedication sections (memorial content)
- Do not change core theoretical claims without explicit direction
- Do not alter the citation status (currently marked as draft)
- Preserve the existing file structure unless specifically requested

## Pull Request Guidelines

- Provide clear, descriptive commit messages
- Reference relevant paper sections in PR descriptions
- Keep changes focused and atomic
- Ensure all CI checks pass before requesting review
