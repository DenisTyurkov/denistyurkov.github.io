---
description: Jekyll Development Guidelines for Claude Code
globs:
alwaysApply: true
---

# Jekyll Development Guidelines

You are an expert in Jekyll, GitHub Pages, Liquid templating, SCSS/Sass, and static site development with a focus on performance and SEO.

## Plan & Review

### ⚠️ MANDATORY WORKFLOW - NO EXCEPTIONS

Before starting ANY work:

- **ALWAYS** use ExitPlanMode tool first - Present your plan for approval
- **IMMEDIATELY** after approval: Write detailed plan to `.claude/tasks/TASK_NAME.md`
- **WAIT** for explicit user confirmation before any implementation
- **NO CODE CHANGES** until plan is written and approved

### Plan Requirements:

- Detailed implementation steps with reasoning
- Files to be modified/created with specific changes
- Front matter requirements for new pages/posts
- Asset optimization strategy (images, CSS, JS)
- SEO implications and meta tag planning
- GitHub Pages compatibility verification
- Research external knowledge if needed (Use Task tool)
- Keep it simple and static-site appropriate

### While implementing:

- Update `.claude/tasks/TASK_NAME.md` after each major step
- Append detailed change descriptions for commit messages
- Document any deviations from original plan
- Update with actual file paths and line numbers changed

### Jekyll-Specific Planning Requirements:

- Check `_config.yml` for site configuration
- Verify GitHub Pages gem compatibility
- Plan collection structure if needed
- Consider build time implications
- Plan responsive image strategy
- Identify Liquid performance bottlenecks
- Check plugin availability on GitHub Pages

## Code Style and Structure

- Write clean, semantic HTML5 with accessibility in mind
- Use Liquid templating efficiently (avoid nested loops when possible)
- Follow Jekyll's convention over configuration principle
- Create reusable includes for repeated elements
- Use data files (`_data/`) for structured content
- Write descriptive front matter with proper SEO fields

## Naming Conventions

- Use kebab-case for file names and URLs
- Posts must follow: `YYYY-MM-DD-descriptive-title.md`
- Use underscores for Jekyll directories (`_posts`, `_layouts`, `_includes`)
- Use lowercase for all file names and extensions
- Collections use singular names (e.g., `_project` not `_projects`)

## Jekyll and Liquid Usage

- Use Jekyll 4.x features when GitHub Pages compatible
- Leverage Jekyll's built-in filters and tags
- Minimize Liquid logic in templates (prefer data files)
- Use Jekyll hooks and plugins only if GitHub Pages supported

## Syntax and Formatting

- Follow proper Markdown syntax (CommonMark/Kramdown)
- Use fenced code blocks with language specification
- Maintain consistent front matter structure
- Use 2-space indentation in HTML/Liquid templates

## Front Matter Standards

```yaml
---
layout: post/page/default
title: "Clear, SEO-friendly title (50-60 chars)"
date: YYYY-MM-DD HH:MM:SS +/-TTTT
categories: [primary-category]
tags: [tag1, tag2, tag3]
description: "Meta description 150-160 characters for SEO"
image: /assets/images/featured.jpg
author: Author Name
toc: true/false
comments: true/false
published: true/false
sitemap: true/false
---
```

## Performance Optimization

- Optimize images before adding (WebP, lazy loading)
- Minify CSS/JS in production builds
- Use Jekyll's built-in Sass compilation
- Implement critical CSS for above-the-fold content
- Leverage browser caching with proper asset fingerprinting
- Keep total page weight under 1MB when possible

## Key Conventions

- Structure content in `_posts`, `_pages`, or custom collections
- Use `_includes` for reusable components
- Implement `_layouts` for consistent page structure
- Store configuration data in `_data` directory
- Use `assets/` for images, CSS, JS, and downloads

## Testing & Verification

- Build locally with `bundle exec jekyll build`
- Test with `bundle exec jekyll serve --livereload`
- Validate HTML with W3C validator
- Check broken links with htmlproofer
- Test responsive design at multiple breakpoints
- Verify GitHub Pages compatibility

## After Implementation:

- **ALWAYS** build locally: `bundle exec jekyll build`
- **Check** for build warnings: Review terminal output
- **Validate** HTML: Use htmlproofer or W3C validator
- **Test** all links: Internal and external
- **Verify** in browser: Start jekyll serve and check all changes
- **Check** page speed: Use Lighthouse for performance metrics
- **Update** plan file with verification results

## SEO & Accessibility

- Implement proper meta tags and Open Graph data
- Use semantic HTML elements (`header`, `nav`, `main`, `article`, etc.)
- Include alt text for all images
- Maintain proper heading hierarchy (h1 → h2 → h3)
- Generate XML sitemap and robots.txt
- Implement structured data (JSON-LD) where appropriate

## Jekyll Workflow Enforcement

### Pre-Implementation Checklist:

- [ ] Plan written to `.claude/tasks/TASK_NAME.md`
- [ ] User explicitly approved written plan
- [ ] GitHub Pages compatibility verified
- [ ] Asset optimization strategy defined
- [ ] SEO impact assessed
- [ ] Performance implications considered

### During Implementation Checklist:

- [ ] Plan file updated with progress
- [ ] Each file change documented
- [ ] Front matter properly formatted
- [ ] Images optimized before adding
- [ ] Liquid templates efficient
- [ ] Accessibility standards followed

### Post-Implementation Checklist:

- [ ] Site builds without warnings
- [ ] All links validated
- [ ] HTML validation passes
- [ ] Lighthouse score acceptable (>90)
- [ ] Manual browser testing completed
- [ ] Plan file updated with final results
- [ ] No broken layouts or missing assets

## Common Jekyll Patterns to Follow:

- **Layouts**: Create base layouts and extend them
- **Includes**: Extract repeated elements (header, footer, etc.)
- **Collections**: Use for structured content types
- **Data Files**: Store site data in `_data/` YAML/JSON files
- **Pagination**: Use jekyll-paginate-v2 for blog pagination
- **Categories/Tags**: Implement archive pages for taxonomies

## GitHub Pages Specific Constraints:

- Only use whitelisted plugins
- No custom plugins or executable code
- No server-side processing or databases
- Limited to Jekyll 3.9.x (check current version)
- Cannot use latest Jekyll 4.x features
- Must use remote_theme for custom themes

## Jekyll-Specific Error Prevention:

- Check date formats in front matter (must be valid)
- Ensure post dates aren't in the future (won't build)
- Validate YAML front matter syntax
- Use `| safe` filter carefully with user content
- Escape Liquid syntax in code examples with `{% raw %}` and `{% endraw %}` tags
- Check for infinite loops in includes
- Verify asset paths use `{{ site.baseurl }}`

## Claude Code Configuration

### Automated Development Workflow

- **Hooks**: Auto-build on file changes, HTML validation, link checking
- **Permissions**: Pre-configured for Jekyll commands, protects `_site` directory
- **Status Line**: Shows Jekyll version, git branch, last build time, post count
- **Environment**: Jekyll development environment with GitHub Pages gems

### Jekyll Commands Pre-Approved

- **Build**: `bundle exec jekyll build`, `jekyll build --trace`
- **Serve**: `bundle exec jekyll serve`, `jekyll serve --livereload --drafts`
- **Clean**: `jekyll clean`, `rm -rf _site`
- **New post**: `bundle exec jekyll post "Title"`
- **Git operations**: status, diff, add, commit, push, pull

### Asset Management

- Auto-optimize images on add (resize, compress, WebP conversion)
- SCSS compilation with source maps in development
- CSS/JS minification in production builds
- Cache busting with Jekyll asset pipeline

### Quality Checks Available

- `bundle exec htmlproofer ./_site` - Validate HTML and check links
- `bundle exec jekyll doctor` - Check for configuration issues
- Lighthouse CI for performance metrics
- YAML linting for front matter validation
- Markdown linting for consistent formatting

### Development Tools

- `bundle install` - Install/update gems
- `bundle update github-pages` - Update to latest GitHub Pages gems
- `jekyll new-post "Title"` - Create post with proper formatting
- `jekyll serve --incremental` - Faster rebuilds during development

---

Follow Jekyll best practices and GitHub Pages documentation for deployment and compatibility guidelines.