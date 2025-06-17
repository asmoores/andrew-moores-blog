# Claude Code Reference for Andrew Moores Blog

## Overview
This is a Hugo-based static blog built with the minimal xmin theme, featuring extensive customizations for post previews, date grouping, and enhanced styling. The entire site was created and configured using Claude Code, demonstrating AI-assisted web development.

## Architecture

### Core Technology Stack
- **Hugo**: Static site generator (requires Hugo to be installed)
- **Theme**: [hugo-xmin](https://github.com/yihui/hugo-xmin) as git submodule
- **Deployment**: Static files generated to `/public/` directory
- **Content Format**: Markdown with TOML front matter

### Key Files Structure
```
/Users/andrewmoores/development/blog/
├── hugo.toml                    # Main configuration
├── .gitmodules                  # Git submodule for theme
├── archetypes/default.md        # Template for new posts
├── content/
│   ├── about.md                 # About page
│   └── posts/                   # Blog posts directory
├── layouts/                     # Custom layout overrides
│   ├── _default/list.html       # HEAVILY customized list template
│   └── partials/
│       ├── head_custom.html     # Custom head includes
│       └── header.html          # Custom header layout
├── static/css/
│   └── custom-styles.css        # Extensive custom styling
├── themes/xmin/                 # Git submodule theme
└── public/                      # Generated site (git ignored)
```

## Configuration Details

### Hugo Configuration (`hugo.toml`)
```toml
baseURL = 'https://example.org/'
languageCode = 'en-uk'
title = 'Andrew Moores Blog'
theme = 'xmin'

# Navigation menu
[[menu.main]]
name = "Home"
url = "/"
weight = 1

[[menu.main]]
name = "Posts"
url = "/posts/"
weight = 2

[[menu.main]]
name = "About"
url = "/about/"
weight = 3

# Pagination settings
paginate = 5
paginatePath = "page"

[params]
customCSS = ["/css/custom-styles.css"]
# googleAnalytics = "G-XXXXXXXXXX"  # Commented out until needed
```

## Major Customizations

### 1. Custom List Template (`layouts/_default/list.html`)
**KEY FEATURE**: This completely overrides the base theme's simple list template with:
- **Date grouping**: Posts grouped by publication date
- **Rich post previews**: Shows title, tags, summary, and "Read more" links
- **Pagination**: Custom pagination with Previous/Next buttons and page info
- **Responsive design**: Mobile-friendly layout

### 2. Custom Header Layout (`layouts/partials/header.html`)
**MAJOR OVERRIDE**: Replaces the theme's basic navigation with:
- Flexbox layout with site title and horizontal navigation
- Proper semantic HTML structure
- Integration with custom CSS classes

### 3. Custom CSS (`static/css/custom-styles.css`)
**EXTENSIVE STYLING**: 186 lines of custom CSS including:
- **Header styling**: Flexbox layout with centered title and horizontal nav
- **Post preview styling**: Cards with borders, typography, and spacing
- **Date grouping**: Styled date headers with blue accent borders
- **Tag styling**: Pill-style tags with background colors
- **Pagination**: Button-style navigation with hover effects
- **Responsive design**: Mobile breakpoints and flexible layouts

### 4. Analytics Integration (`layouts/partials/head_custom.html`)
**CONDITIONAL LOADING**: Smart Google Analytics 4 integration that:
- Only loads when `googleAnalytics` parameter is set
- Uses modern gtag.js implementation
- Includes custom CSS loading logic

## Content Strategy

### Post Front Matter Template (`archetypes/default.md`)
```yaml
+++
date = '{{ .Date }}'
draft = true
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
+++
```

### Content Organization
- **Posts**: Stored in `content/posts/` directory
- **Pages**: Root-level pages like `content/about.md`
- **Categories**: Used for post grouping (e.g., "personal", "tutorials")
- **Tags**: Multiple tags per post for detailed categorization

## Development Workflow

### Local Development
```bash
# Start development server
hugo server -D

# Build for production  
hugo

# Create new post
hugo new posts/my-new-post.md
```

### Git Workflow
- Theme managed as git submodule
- Generated `public/` directory not tracked
- Standard Hugo `.gitignore` patterns

## Special Features

### 1. Post Previews on Homepage
- Shows post summaries with "Read more" links
- Displays tags as styled pills
- Groups posts by publication date
- Responsive card-based layout

### 2. Pagination System
- 5 posts per page (configurable)
- Custom pagination navigation
- Page counter display
- Previous/Next button styling

### 3. Responsive Design
- Mobile-first approach
- Flexible header layout
- Responsive typography and spacing
- Mobile navigation stacking

### 4. Analytics Ready
- Google Analytics 4 integration prepared
- Conditional loading (no performance impact until enabled)
- Privacy-conscious implementation

## Theme Relationship

### Base Theme (xmin)
- Provides: Basic HTML structure, minimal CSS, footer
- Location: `themes/xmin/` (git submodule)
- Repository: https://github.com/yihui/hugo-xmin.git

### Custom Overrides
- **List template**: Completely replaced with rich preview system
- **Header partial**: Enhanced with flexbox navigation
- **CSS**: Extensive additions via custom stylesheet
- **Head partial**: Added analytics and custom CSS loading

## Deployment Considerations

### Build Process
1. Hugo generates static files to `public/` directory
2. All assets (CSS, images) are processed and copied
3. Site is entirely self-contained in `public/` folder

### Performance Features
- Minimal JavaScript (only Analytics when enabled)
- Optimized CSS loading
- Static file serving
- Responsive images ready

## Maintenance Notes

### Theme Updates
```bash
# Update theme submodule
git submodule update --remote themes/xmin
```

### Content Guidelines
- All posts should include tags and categories
- Use meaningful summaries for homepage previews
- Date format affects grouping display
- Draft posts won't appear in production builds

### Customization Points
- CSS variables could be added for easier theming
- Additional partials could be created for repeated elements
- Image optimization could be implemented
- Search functionality could be added

## AI Development Context

This entire site was built through Claude Code conversations, demonstrating:
- **Direct file manipulation**: All files created/edited by AI
- **Command execution**: Hugo builds and git operations via AI
- **Iterative development**: Features added through natural language requests
- **Context awareness**: AI maintained consistency across all customizations

The architecture reflects AI-assisted development patterns:
- Clean separation of concerns
- Logical file organization
- Comprehensive documentation
- Future-ready extensibility

## Quick Start for Claude Code

When working on this blog:

1. **Development server**: `hugo server -D`
2. **Build**: `hugo`
3. **New post**: `hugo new posts/title.md`
4. **Key files to modify**:
   - `hugo.toml` for configuration
   - `static/css/custom-styles.css` for styling
   - `layouts/_default/list.html` for homepage layout
   - `content/posts/` for new content

5. **Common tasks**:
   - Enable analytics: Uncomment `googleAnalytics` in `hugo.toml`
   - Add menu items: Add `[[menu.main]]` sections
   - Customize styling: Edit `custom-styles.css`
   - Update theme: `git submodule update --remote`