# Development Context - Local Workflow

## Quick Start Commands

### Daily Development
```bash
# Start development server with drafts
hugo server -D

# Start with specific port
hugo server -D --port 8080

# Start with live reload and navigation to changed content
hugo server -D --navigateToChanged

# Build for production testing
hugo --minify
```

### Content Creation
```bash
# Create new blog post
hugo new posts/my-new-post.md

# Create new page
hugo new about/new-page.md

# Create post with specific date
hugo new posts/$(date +%Y-%m-%d)-post-title.md
```

## Development Environment Setup

### Prerequisites Check
```bash
# Verify Hugo installation and version
hugo version

# Check Git submodules status
git submodule status

# Verify theme is properly initialized
ls -la themes/xmin/
```

### Initial Setup (for new clones)
```bash
# Clone repository
git clone <repository-url>
cd blog

# Initialize theme submodule
git submodule update --init --recursive

# Verify setup
hugo server -D
```

## Local Development Workflow

### 1. Starting a Development Session
```bash
# Navigate to project directory
cd /Users/andrewmoores/development/blog

# Pull latest changes
git pull origin main

# Update theme submodule if needed
git submodule update --remote themes/xmin

# Start development server
hugo server -D --navigateToChanged
```

### 2. Creating New Content
```bash
# Create new post
hugo new posts/$(date +%Y-%m-%d)-post-title.md

# Edit the post (example with VS Code)
code content/posts/$(date +%Y-%m-%d)-post-title.md
```

**Post Template Structure:**
```yaml
+++
date = '2024-07-06'
draft = true
title = 'Post Title'
categories = ['category']
tags = ['tag1', 'tag2']
+++

Your content here...

<!--more-->

Extended content after the summary break...
```

### 3. Content Development Process
1. **Draft Phase**: Keep `draft = true` while writing
2. **Preview**: Use `hugo server -D` to see drafts locally
3. **Review**: Check formatting, links, and styling
4. **Finalize**: Set `draft = false` when ready to publish
5. **Test**: Run `hugo server` (without -D) to verify published view

### 4. Theme Customization Workflow
```bash
# Edit custom styles
code static/css/custom-styles.css

# Modify layout templates
code layouts/_default/list.html
code layouts/partials/

# Test changes immediately (live reload active)
# Browser automatically refreshes
```

### 5. Pre-Deployment Testing
```bash
# Clean previous builds
rm -rf public/

# Build production version
hugo --minify

# Serve production build locally
cd public && python3 -m http.server 8000
# Visit http://localhost:8000

# Return to project root
cd ..
```

## Development Server Options

### Standard Development
```bash
hugo server -D
# - Includes drafts
# - Live reload enabled
# - Available at http://localhost:1313
```

### Advanced Development Options
```bash
# Custom port
hugo server -D --port 8080

# Disable fast render (for troubleshooting)
hugo server -D --disableFastRender

# Navigate to changed content automatically
hugo server -D --navigateToChanged

# Bind to all interfaces (for network testing)
hugo server -D --bind 0.0.0.0

# Enable verbose logging
hugo server -D --verbose
```

## File Watching and Live Reload

### What Triggers Rebuilds
- Content files (`.md` files in `content/`)
- Layout templates (`layouts/`)
- Static assets (`static/`)
- Configuration (`hugo.toml`)
- Theme files (`themes/xmin/`)

### What Doesn't Trigger Rebuilds
- Files in `public/` (build output)
- Hidden files (`.git`, `.idea`)
- Files matching `.gitignore` patterns

## Common Development Tasks

### Content Management
```bash
# List all posts
find content/posts -name "*.md" -exec basename {} \;

# Find draft posts
grep -r "draft = true" content/posts/

# Check for broken internal links
hugo --printI18nWarnings --printPathWarnings
```

### Theme Development
```bash
# View theme structure
tree themes/xmin/

# Compare custom layouts with theme defaults
diff -r layouts/ themes/xmin/layouts/

# Update theme to latest version
git submodule update --remote themes/xmin
```

### Performance Testing
```bash
# Build with timing information
hugo --templateMetrics

# Check build performance
time hugo

# Analyze generated files
du -sh public/
find public -name "*.html" | wc -l
```

## Troubleshooting

### Common Issues and Solutions

**Theme not found:**
```bash
git submodule update --init --recursive
```

**Posts not showing:**
- Check `draft = false` in front matter
- Verify date is not in the future
- Ensure file is in `content/posts/` directory

**Styles not loading:**
- Verify `customCSS` parameter in `hugo.toml`
- Check file path: `static/css/custom-styles.css`
- Clear browser cache

**Live reload not working:**
- Restart hugo server
- Check browser console for WebSocket errors
- Try `--disableFastRender` flag

**Build errors:**
```bash
# Verbose output for debugging
hugo --verbose

# Check Hugo version compatibility
hugo version
```

### Development Environment Reset
```bash
# Clean everything and start fresh
rm -rf public/
rm .hugo_build.lock
git submodule update --init --recursive
hugo server -D
```

## IDE Integration

### VS Code Setup
Recommended extensions:
- Hugo Language and Syntax Support
- Markdown All in One
- Front Matter CMS

### File Associations
- `.md` files → Markdown editor
- `.toml` files → TOML syntax highlighting
- `.html` files → HTML editor with Go template support

## Git Workflow Integration

### Pre-commit Checks
```bash
# Build without errors
hugo

# Check for draft posts in main branch
grep -r "draft = true" content/posts/ && echo "Warning: Draft posts found"

# Validate configuration
hugo config
```

### Branch Strategy
- `main` branch → Production deployment
- Feature branches for major content or theme changes
- Direct commits to `main` for regular posts

This development context provides a comprehensive workflow for efficient local development of your Hugo blog.
