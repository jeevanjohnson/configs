---
name: enhance-documentation
description: 'Enhance markdown documentation (README, ARCHITECTURE, guides, etc.) by improving format, readability, grammar, and flow. Use when documentation exists but needs to be more professional, clearer, better organized, or easier to follow.'
argument-hint: 'Paste your markdown file or describe the documentation to enhance'
---

# Enhance Documentation

Review and improve markdown documentation files by systematically enhancing readability, grammar, structure, and professional presentation without changing core content.

## When to Use

- Documentation exists but feels hard to follow or poorly organized
- Grammar and language could be clearer or more professional
- Formatting is inconsistent or doesn't follow best practices
- Structure/flow makes it difficult to find information
- Document needs a pass for consistency and polish
- You want to maintain content but improve presentation

## Supported Document Types

- **Project overviews**: README.md, OVERVIEW.md
- **Architecture docs**: ARCHITECTURE.md, DESIGN.md, STRUCTURE.md
- **Guides**: CONTRIBUTING.md, GUIDE.md, HOW-TO.md
- **Setup/Installation**: SETUP.md, INSTALL.md, QUICKSTART.md
- **API docs**: API.md, ENDPOINTS.md, REFERENCE.md
- **Policy docs**: LICENSE, CODE_OF_CONDUCT.md
- **Any markdown file** requiring readability improvements

## Enhancement Procedure

### Step 1: Assess Current State
Review the document for:
- **Structure issues**: Missing headers, inconsistent hierarchy, poor organization
- **Readability problems**: Dense paragraphs, unclear sentences, passive voice
- **Formatting inconsistencies**: Mismatched bullets, code block styles, spacing
- **Grammar/language**: Typos, awkward phrasing, unclear terminology
- **Flow gaps**: Logical jumps, missing transitions, unclear progression

### Step 2: Improve Structure & Organization

**Header hierarchy** (use consistent levels):
- H1 (`#`) = Document title (exactly one)
- H2 (`##`) = Major sections
- H3 (`###`) = Subsections
- H4 (`####`) = Details (avoid deeper nesting)

**Logical flow**:
- Introduction/overview first
- Prerequisites/setup before usage
- Common tasks before advanced topics
- Conclusion/next steps last

**Guide suggestions**:
```
# Title

## Overview/Introduction
(What is this? Why does it matter?)

## Prerequisites
(Requirements before starting)

## Core Concept/Section
(Main information)

## How to Use / Procedures
(Steps or examples)

## Troubleshooting / Common Issues
(FAQ, problems, solutions)

## Advanced / Next Steps
(Optional deep dives)

## References / Related Links
(Additional resources)
```

### Step 3: Enhance Readability

**Simplify sentences**:
- ❌ "The system, which incorporates multiple layers of abstraction, provides functionality that enables users to accomplish their objectives."
- ✅ "The system provides multi-layered functionality to help users accomplish their goals."

**Use active voice**:
- ❌ "This document is maintained by the team."
- ✅ "The team maintains this document."

**Remove redundancy**:
- ❌ "I will explain the procedure and explain how to use it."
- ✅ "I'll explain the procedure and how to use it."

**Use shorter paragraphs**:
- Break dense paragraphs into 2-3 sentence chunks
- Use bullets for lists (don't embed in prose)
- Add whitespace between sections

**Clarify terminology**:
- Define acronyms on first use: "continuous integration (CI)"
- Avoid jargon without explanation
- Use consistent terms throughout (don't switch between "config" and "configuration")

### Step 4: Improve Formatting

**Consistent bullet structure**:
```markdown
- Item one (use consistent capitalization)
- Item two (start all with same structure)
  - Sub-item (indented consistently)
  - Sub-item
- Item three
```

**Code blocks** (always use language identifier):
```markdown
Without language (bad):
```
python_code_here
```

With language (good):
\`\`\`python
python_code_here
\`\`\`
```

**Emphasis consistency**:
- Use `**bold**` for important concepts, not ***bold italic***
- Use `code` for technical terms: `variable_name`, `function()`, `ClassName`
- Use `> blockquotes` for tips/notes, not random formatting

**Step callouts** (if providing procedures):
```markdown
1. First step with explanation
2. Second step
   - Detail about step 2
   - Another detail
3. Final step
```

### Step 5: Refine Grammar & Language

**Common patterns to fix**:
- Remove redundant words ("very unique" → "unique")
- Fix subject-verb agreement
- Use consistent tense (prefer present or imperative for docs)
- Replace "you need to" with imperative: "Install X" not "You need to install X"
- Replace "This is X" with "X is Y": "This is a configuration file" → "Configuration file format:"

**Professionalism pass**:
- Replace "stuff", "things", "basically", "like" with precise terms
- Remove excessive exclamation marks
- Avoid contractions in formal docs (but acceptable in guides)
- Use "we" only if speaking for team/organization

### Step 6: Polish & Validate

**Consistency checks**:
- [ ] Headings follow hierarchy (no skipped levels)
- [ ] Terminology consistent throughout (check for synonyms)
- [ ] All code blocks have language identifiers
- [ ] Lists use consistent capitalization and punctuation
- [ ] Tone matches document purpose
- [ ] Links are relative and working
- [ ] No orphaned headings (heading with no content)

**Readability validation**:
- [ ] Paragraphs are 2-4 sentences max
- [ ] No paragraph exceeds 3 lines
- [ ] Complex ideas broken into bulleted lists
- [ ] Technical terms defined or linked
- [ ] Table of contents added (if document > 1000 words)

## Example: Before & After

### Example 1: Dense README

**BEFORE** (hard to scan, unclear):
```markdown
# My Project

This is a project that does some things. It has a lot of functionality and stuff 
that helps with development. You need to install dependencies first and then you 
need to run the setup. The project basically works like this: it takes input and 
produces output. There are many features and configurations you can use. You should 
read the docs for more info about how to use it.
```

**AFTER** (clear structure, scannable):
```markdown
# My Project

A development toolkit that automates common workflows and configuration tasks.

## Features

- Input processing with multiple output formats
- Extensible plugin system
- Built-in development server
- Configuration management

## Quick Start

1. Install dependencies: `npm install`
2. Run setup: `npm run setup`
3. Start development: `npm run dev`

## Configuration

[Link to config docs]

## Learn More

- [Full documentation](./docs)
- [API reference](./docs/api.md)
- [Contributing guide](./CONTRIBUTING.md)
```

### Example 2: Improving Flow & Clarity

**BEFORE**:
```markdown
## Installation

Python is required. You can download it. Make sure pip is installed. Dependencies 
are in requirements.txt. Run pip install on it. Some people also need to set 
environment variables. This is explained in the setup section below.

## Advanced Setup

[Explains environment variables]

## How to Use

[Usage instructions]
```

**AFTER**:
```markdown
## Prerequisites

- Python 3.9 or later
- pip (included with Python)

## Installation

1. Clone the repository
2. Install dependencies: `pip install -r requirements.txt`
3. Configure environment variables (see "Advanced Setup" below)

## How to Use

[Usage instructions]

## Advanced Setup

### Environment Variables

[Environment variable details]
```

### Example 3: Grammar & Language

**BEFORE**:
```markdown
This document provides information about the system which is basically responsible 
for processing different types of data formats. The system, like, does a lot of 
things and you need to sort of understand the architecture before you use it.
```

**AFTER**:
```markdown
This document explains the system architecture and data processing capabilities. 
Read this before using the system for the first time.
```

## Tips for Effective Enhancement

1. **Read aloud** — You'll catch awkward phrasing better this way
2. **Check markdown rendering** — Some formatting issues only appear when rendered
3. **Prioritize clarity over cleverness** — Boring but clear beats clever but confusing
4. **Maintain voice but improve language** — Don't change the author's intent or style, just polish it
5. **Add visual breaks** — Use headers, bullets, and whitespace to reduce cognitive load
6. **Test links and code blocks** — Ensure all references are correct and examples work
7. **Get feedback** — Ask someone unfamiliar with the project to read it and note confusion points

## Output Format

Provide the enhanced version with:
1. **Full improved markdown** — Ready to copy/paste or commit
2. **Summary of changes** — 3-5 key improvements made
3. **Optional suggestions** — If further content improvements would help

## Common Anti-Patterns to Avoid

- Wall-of-text paragraphs (break them up)
- Mixing multiple formatting styles (`**bold and _italic combined_**`)
- Orphaned headers with no content below
- Inconsistent or over-abbreviated TODOs/FIXMEs left in published docs
- Too many levels of nesting (max 3-4 heading levels)
- Links that break or point to wrong sections
