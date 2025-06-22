+++
date = '2025-06-22T14:50:24+01:00'
draft = false
title = 'Analyzing Posts for AI Involvement'
+++

## Introduction

After building this blog and writing the first post in collaboration with Claude Code I wanted to understand how easy it would be to recognise that the post had some AI involvement.  This post will be primarily written by me with some suggestions from Claude.

I've never investigated this area, but I assume it's a big concern for blogging sites such as Medium or longer-form sites such as Substack.

So I decided to ask a different Chat application to analyze.

## ChatGPT analysis

The first thing I found was that ChatGPT was unable to access my blog.  So I had to paste the `.md` file into the prompt.

It told me that `Indicators suggest the post might be AI-generated`:

1. Very Clear, Structured, and Consistent Writing
2. Formal and Neutral Tone
3. Repetitive Positive Framing
4. No Obvious Typos or Grammar Errors
5. Focus on Describing AI Actions

It also found some indicators of human involvement:

1. Personal Reflections
2. Specific Technical Details
3. Balanced Criticism

In summary:

```
The blog post was very likely written with significant AI assistance, specifically from Claude Code as stated openly in the text.
  • However, it was also clearly reviewed, edited, and personalized by a human, especially the parts reflecting on the AI's style and limitations.
  • This mix — AI-generated draft plus human curation — is becoming very common in tech blogs about AI tools.
```

I then decided to fix all the access issues.  I had to make numerous config changes to get it working:

* Adding a robots.txt
* Adding SEO meta tags
* Making the slugs amtch the page title
* Manually submitting the blog post for indexing by Google

I used ChatGPT to walk me through making all these changes.

When it could finally access the post I asked it again:

```
Now analyse the blog post to determine if it was written by an AI
```

This time its analysis was different:

```
The blog post is almost certainly human-written, detailing a human‑AI collaboration in coding—but not authored by an AI. The author intentionally shares that Claude Code executed the development, but the narrative and style are clearly his.
```

## Why ths shift in position?

```
That's an excellent and insightful question—and you're right to challenge the shift.

Here's the key point:

The change in analysis isn't due to the site becoming indexable—Google or hosting access has no influence on how I assess the writing itself. Rather, it's about the surrounding signals and context that were visible during each analysis.
```

It further explained:

```
You're actually proving a broader point: context matters immensely in attribution. It's not just what is written, but how, where, and why. Once seen in context, the authorship intent was much clearer
```

## Conclussion

So, context matters as much as content.  Inconsistency, typos and a somewhat negative tone are good indicators that a Human was the author.  Very clear, consistent writing, repeated positivity about AI and a sunny outlook are indicators that an AI was the author.

I don't want to change the way I write (create?) blog posts to disguise the fact that I am using AI tools but I do want to develop a style that is more natural and can become associated with me.

