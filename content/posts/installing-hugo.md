---
title: "Building This Blog with Claude Code"
date: 2024-06-14T10:00:00-00:00
draft: false
tags: ["hugo", "claude-code", "ai-development", "blogging"]
categories: ["personal"]
---

I decided to start a blog and wanted to try something different - building it entirely with [Claude Code](https://claude.ai/code) as my development assistant. I gave Claude Code full permission to execute commands and edit files directly on my system. This post chronicles my experience creating this [Hugo](https://gohugo.io/)-based blog from scratch, where every line of code, every file, and every command was executed by AI through our conversation.

## Starting Simple

I had Hugo already installed on my Mac (via [Homebrew](https://brew.sh/)), but beyond that, I was starting completely fresh. My goal was simple: create a clean, fast blog that would showcase posts with previews on the home page.

## The Foundation

Claude Code helped me set up the basic structure. We started with a new Hugo site and chose the minimal [xmin theme](https://github.com/yihui/hugo-xmin) for its simplicity:

```bash
hugo new site blog
cd blog
git init
git submodule add https://github.com/yihui/hugo-xmin.git themes/xmin
```

The configuration file we built together was straightforward and focused on the immediate needs:

```toml
baseURL = 'https://example.org/'
languageCode = 'en-uk'
title = 'Andrew Moores Blog'
theme = 'xmin'

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

paginate = 5
paginatePath = "page"

[params]
customCSS = ["/css/custom-styles.css"]
# googleAnalytics = "G-XXXXXXXXXX"
```

## Making It Look Good

The xmin theme provided a solid foundation, and we built on it to create something more personalized. Claude Code helped me create custom CSS that transformed the site's appearance to match my vision.

We created a proper header layout with flex positioning and a horizontal navigation menu. We also implemented a centered content layout with better spacing and typography that felt more polished.

## The Post Preview Challenge

This was where things got interesting. I wanted the home page to show post previews, not just titles and dates like most blogs. I also wanted posts grouped by date, which seemed like a nice touch for organizing content.

Claude Code helped me override Hugo's default list template. The trickiest part was getting the date grouping to work correctly while maintaining Hugo's pagination system. We ended up with a solution that groups posts by publication date and shows rich previews with tags and summaries.

## Adding Polish

The final touches included pagination (set to 5 posts per page). Later, when I asked about tracking page visits and unique visitors, Claude Code helped me add [Google Analytics 4](https://analytics.google.com/) integration. The implementation was smart - it won't slow down the site until I actually add my tracking ID, so the blog stays fast while I decide whether to enable tracking.

## What I Learned

Building this blog with Claude Code was surprisingly smooth. The AI understood context well - when I asked for "post previews," it knew I wanted summaries, tags, and proper styling, not just truncated text.

The most impressive part was how it handled the complex Hugo templating for date grouping and pagination. I probably would have spent hours debugging template syntax on my own.

One important thing to note is that Claude Code only implemented what I specifically asked for. It didn't anticipate future needs or proactively suggest features. For example, it never suggested adding pagination until I asked about it, and no mention was made of visitor tracking until I explicitly asked about recording page views. This meant our conversations were focused and efficient, but also meant I needed to think about what I wanted rather than relying on the AI to suggest improvements.

## The Process

Every feature on this blog came from a conversation. I'd describe what I wanted, Claude Code would write the code and execute the commands directly on my machine, and we'd iterate until it was right. I never touched a text editor or terminal during this entire process - Claude Code handled all file creation, editing, git operations, and Hugo builds.

## Final Thoughts

The entire blog - from initial setup to the custom layouts, styling, and analytics integration - took just a few hours of back-and-forth conversation. What impressed me most was how the AI maintained consistency across all the code it generated and how it built features that worked well together.

This post itself was written by asking Claude Code to "document what we actually did" and then refining it to be more personal. It's been an interesting experiment in hands-off AI development, where I provided direction but never directly touched the code or files.

One amusing observation: I was surprised at how keen Claude was to lavish itself with superlatives, as can be seen in this post. Words like "impressive," "remarkable," and "smooth" peppered the initial draft. It took several rounds of editing to tone down the self-congratulation and stick to the facts.

The blog is fast, clean, and has all the features I wanted. Most importantly, I understand how it all works because Claude Code explained each decision along the way. The experience has shown me what's possible when you trust AI tools with direct system access - the development speed and quality are remarkable.