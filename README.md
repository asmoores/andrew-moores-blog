# Andrew Moores Blog

A Hugo-based static blog built with the minimal xmin theme, featuring extensive customizations for post previews, date grouping, and enhanced styling.

## Prerequisites

- [Hugo](https://gohugo.io/installation/) (static site generator)
- Git (for theme submodule management)

## Quick Start

### 1. Clone the Repository
```bash
git clone <repository-url>
cd blog
```

### 2. Initialize Theme Submodule
```bash
git submodule update --init --recursive
```

### 3. Local Development
Start the development server to preview your site locally:
```bash
hugo server -D
```

The site will be available at `http://localhost:1313`. The `-D` flag includes draft posts.

### 4. Build for Production
Generate static files for deployment:
```bash
hugo
```

This creates the `public/` directory containing all files that will be served by your web server.

## Project Structure

```
blog/
├── hugo.toml                    # Site configuration
├── content/                     # Markdown content
│   ├── about.md                 # About page
│   └── posts/                   # Blog posts
├── layouts/                     # Custom template overrides
│   ├── _default/list.html       # Homepage layout
│   └── partials/                # Reusable template parts
├── static/css/                  # Custom stylesheets
├── themes/xmin/                 # Base theme (git submodule)
└── public/                      # Generated site (build output)
```

## Content Management

### Creating New Posts
```bash
hugo new posts/my-new-post.md
```

### Post Front Matter
```yaml
+++
date = '2024-01-01'
draft = false
title = 'My New Post'
categories = ['tutorials']
tags = ['hugo', 'blogging']
+++
```

## Local Development Details

### Development Server Features
- **Live reload**: Changes automatically refresh the browser
- **Draft posts**: Include drafts with `-D` flag
- **Fast rebuilds**: Hugo rebuilds only changed files
- **Port configuration**: Use `--port 8080` to change port

### Viewing Generated Files
The `public/` directory contains the exact files that will be served:
- `index.html` - Homepage
- `posts/` - Individual post pages
- `css/` - Stylesheets
- `sitemap.xml` - Search engine sitemap

### Theme Development
The xmin theme is included as a git submodule. Custom overrides are located in:
- `layouts/` - HTML template overrides
- `static/css/custom-styles.css` - Custom styling

## Configuration

### Site Settings (`hugo.toml`)
- **baseURL**: Set to your domain for production
- **title**: Site title shown in header
- **menu**: Navigation menu items
- **pagination**: Posts per page (currently 5)

### Custom Features
- **Post previews**: Homepage shows post summaries
- **Date grouping**: Posts grouped by publication date
- **Tag system**: Posts categorized with styled tags
- **Responsive design**: Mobile-friendly layout
- **Analytics ready**: Google Analytics 4 integration available

## Deployment

### Static Hosting
The generated `public/` directory can be deployed to any static hosting service:
- GitHub Pages
- Netlify
- Vercel
- Traditional web servers

### Build Process
1. Hugo processes Markdown files
2. Applies templates and layouts
3. Generates HTML, CSS, and assets
4. Outputs complete static site to `public/`

## Maintenance

### Updating Theme
```bash
git submodule update --remote themes/xmin
```

### Adding Menu Items
Edit `hugo.toml`:
```toml
[[menu.main]]
name = "New Page"
url = "/new-page/"
weight = 4
```

### Customizing Styles
Edit `static/css/custom-styles.css` to modify appearance.

## Troubleshooting

### Common Issues
- **Theme not found**: Run `git submodule update --init --recursive`
- **Posts not showing**: Check `draft = false` in front matter
- **Styles not loading**: Verify `customCSS` parameter in `hugo.toml`

### Development Tips
- Use `hugo server --navigateToChanged` to auto-navigate to changed content
- Add `--disableFastRender` if experiencing rendering issues
- Check `hugo version` to ensure compatibility

## Features

### Homepage
- Post previews with summaries
- Date-based grouping
- Tag display
- Pagination (5 posts per page)

### Responsive Design
- Mobile-first approach
- Flexible header layout
- Responsive typography
- Touch-friendly navigation

### Performance
- Minimal JavaScript
- Optimized CSS loading
- Static file serving
- Fast page loads

This blog was created and customized using Claude Code, demonstrating AI-assisted web development with Hugo.