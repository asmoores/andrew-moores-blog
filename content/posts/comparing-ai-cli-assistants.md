+++
date = '2025-06-22T15:45:00+01:00'
draft = false
title = 'Comparing AI CLI Assistants'
+++

# Comparing AI CLI Assistants

## Introduction

I'm currently using an AI coding assistant in my day job, and based on my experience, I wanted to test the tools available in this space. With the popularity of AI-powered development tools, several command-line interface (CLI) assistants have emerged to help developers work more efficiently. This post explores and compares the major players based on my hands-on testing.

This blog post is about using a specification for a specific non-trivial change and letting the assistant work out the best approach, rather than the incremental step-by-step prompting I typically use for smaller improvements.

## How I Tested

I have been using step-by-step prompting - the small prompt by small prompt approach - to making changes and improvements to code, which has been a boost to productivity as I've been refactoring code and improving test coverage when previously I might not have due to time constraints. However, for this test, I wanted to try a different approach.

I wanted to find a typical day-to-day coding task. Most days developers aren't creating new applications from scratch - they're more likely updating or extending existing apps. One of the things I needed to do recently was introduce a new class to centralize code related to user permissions. Code that checked what a User could do was scattered throughout the codebase and used a variety of techniques.

The long-term goal is to standardize on a preferred approach for representing the business logic, backing store used, etc. The interface for this new manager class was already designed so implementation simply involved migrating the existing code and then using the methods from the new manager throughout the codebase. The prerequisites were basic: code should compile, tests should pass.

The test was to update one of the classes where code could be migrated and, once I was happy with the first migration, to use a specification to migrate the code from the remaining classes.

### Prompts and Specifications

I used the following sequence of prompts for each assistant:

**1. Confirming the tool can find the required class**

> Look for a class called PermissionsManager

**2. Testing the tool's ability to find related classes**

> Now find which classes are using PermissionDecision

**3. Assessing the tool's understanding of the migration scope**

> The intention of PermissionManager is to replace all the various code snippets that check if a user can do something due to a lock being in place. The class is read only. The interface the class implements is complete and does not need altering. Give me a list of the remaining classes that could re-use methods already defined on PermissionManager or have code migrated to methods on PermissionManager.

**4. Requesting a detailed implementation specification**

> Based on the work already done in the login class create a specification for how to do this change. Key points are that no new public methods need be added to PermissionManager; the unit and integration tests should be updated and confirmed as passing; the work should be done on a per class basis and each small step should be committed before proceeding to the next step; the aim of small commits is to make it easy for a reviewer to understand what has changed and why; before making a commit approval must be sought; commit messages should follow the 50/70 rule and always start with some free text describing why these changes are being made before going into detail; the project must compile and all tests pass for each commit.

## What I Used

For this comparison, I tested four AI-powered command line assistants that represent the major players in the space:

- **Claude Code** - Anthropic's offering with direct file system access
- **Gemini CLI** - Google's command line interface for their Gemini model
- **OpenAI Codex** - OpenAI's coding assistant accessible via command line
- **Amazon Q CLI** - Amazon's AI coding assistant with AWS integration

They were all easy to install, mostly using Homebrew. However, Amazon Q came with quite a lot of command line popup functionality which I disabled.

## What I Found

The takeaway from this testing is that Claude Code and Amazon Q are the best and passed the test; Gemini CLI and OpenAI Codex were unable to complete the test.

### Amazon Q

1. **Found the new manager class despite typo in name in prompt**
2. **Server issues, had to tell it to continue**
3. **Made changes, compile errors**
4. **Targeted use of gradle builds - not building and running all tests each time**

### Gemini CLI

1. **Failed to find the new manager class due to the typo**
2. **Took a lot more time than Claude, possibly because it was running the full integration test suite repeatedly**
3. **Got a 502 and stopped but continued when prompted to**
4. **Repeatedly creates code that won't compile**
5. **When it uses gradle to compile or run tests it just uses the basic tasks and doesn't do it specifically for the classes it's changed**
6. **Got stuck in a loop and exited**

### Claude Code

1. **Didn't run or recognise that integration tests might need updating until the specification was updated**

### OpenAI Codex

1. **Doesn't have an init function where it scans the repo and produces a summary md file**
2. **Had problems writing the spec to a file**
3. **Couldn't find a Java runtime and couldn't run gradle - due to non interactive shell creation**

## Conclusion

My testing revealed clear differences between the AI CLI assistants. While all tools were useful, only Claude Code and Amazon Q successfully completed the full migration task. The initial insight is that while some tools successfully handled complex refactoring work, the quality and reliability vary significantly between providers, requiring careful evaluation and review of their output.

**Key Takeaways:**
- **Claude Code and Amazon Q** demonstrated the ability to handle complex, multi-step development tasks
- **Gemini CLI and OpenAI Codex** struggled with the same task, highlighting the importance of testing tools in the workflow
- **Daily usage limits** are a real constraint that affects productivity and tool evaluation

**Looking Forward:**
I will be revisiting each tool in more detail in future blog posts, going into more detail on each tool's strengths, weaknesses, and specific use cases that I find them best for.

Of course this may all change next week so I will be automating the test suite, using an AI coding assistant of course, so the tests can be repeated easily.