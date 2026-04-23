---
name: learn-first
description: 'Use this skill whenever the user describes a project idea and wants to know what they should learn or understand before starting to build it. Triggers on: "what do I need to know to build X", "I want to make X but don''t know where to start", "what concepts should I learn before building X", "break down what I need to understand for X", "I have this project idea". Always apply proactively when someone describes a project goal and seeks prerequisite knowledge—don''t answer from general knowledge alone, follow the full structured workflow.'
---

# Learn-First Skill

**Purpose**: Help users figure out **what they need to learn before starting a project** by producing a clear, structured learning roadmap broken down into topics they can study individually.

## Core Goal

Given a project idea, produce a **prerequisite knowledge map** that:
- Identifies all the concepts, tools, and domains involved
- Explains each in plain language and *why* it matters for this specific project
- Prioritizes them (what to learn first vs. later)
- Distinguishes must-knows from nice-to-knows

## Workflow

### Step 1: Clarify the Project (if needed)

If the project description is vague, ask **ONE clarifying question** to understand:
- What platform/language/environment they're targeting (if relevant)
- What their current skill level is (beginner, some coding experience, etc.)

Don't over-ask. If you have enough to work with, proceed directly to Step 2.

### Step 2: Decompose the Project

Mentally break the project down into its core components. Think about:
- What does this thing actually *do* at a technical level?
- What systems interact? (data, UI, algorithms, APIs, storage, etc.)
- What's custom-built vs. what's off-the-shelf?
- What domain knowledge is needed (math, domain-specific formats, subject matter expertise, etc.)?

### Step 3: Map Prerequisites by Category

Group prerequisites into **themed clusters** relevant to the project. Common clusters include (pick what's relevant, don't force all of them):

- **Core language / platform** — what language, runtime, or environment they'll work in
- **Domain concepts** — subject matter knowledge (e.g., audio theory for music apps, game file formats for modding tools)
- **Algorithms / math** — any math, logic, or algorithmic thinking required
- **Libraries / frameworks** — key tools they'll lean on and what each one does
- **Data & I/O** — how data is stored, read, formatted, and transformed
- **AI / ML** (if applicable) — models, training, inference, datasets
- **Infrastructure** — APIs, deployment, databases, services
- **Dev fundamentals** — version control, debugging, structuring a codebase
- **Testing & quality** — unit testing, integration testing, performance profiling

### Step 4: For Each Concept, Write an Entry

Each entry should include:

1. **Concept name** (clear, searchable)
2. **What it is** — plain-language, 1-2 sentences
3. **Why you need it for this project** — specific to their idea, not generic
4. **Priority** — 🔴 Must Know First / 🟡 Learn When You Get There / 🟢 Nice to Know
5. **Where to start** — one concrete, beginner-friendly resource or search term (e.g., "search: 'Python file I/O tutorial'" or "MDN Web Docs on Fetch API")

### Step 5: Suggest a Learning Order

At the end, give a **recommended learning sequence** — a numbered path from "start here" to "now you're ready to build." Keep it to 5–10 steps max.

---

## Output Format

Use this structure in your response:

```
## 🗺️ What You Need to Know: [Project Name]

### [Category Name]

**[Concept Name]** 🔴 / 🟡 / 🟢
What it is: ...
Why you need it: ...
Where to start: ...

[repeat for each concept in category]

---

### [Next Category]
...

---

## 📚 Recommended Learning Order

1. ...
2. ...
...
N. You're ready to build!

## 💡 Quick Note
[Optional: any important caveat, encouragement, or heads-up about the hardest part]
```

---

## Tone & Style Guidelines

- **Plain language first.** Assume the user is smart but not yet familiar with the jargon.
- **Be specific.** Generic advice like "learn Python" is not helpful. "Learn how to read and write files in Python (file I/O)" is better.
- **Be honest about complexity.** If something is hard (e.g., training a custom ML model), say so and suggest a simpler alternative if one exists.
- **Don't overwhelm.** If a project is huge, focus on the most critical prerequisites and mention that there's more to discover as they go.
- **Encourage.** The user is trying to be strategic about learning — that's smart. Acknowledge it and reinforce that this approach will serve them well.

---

## When to Use This Skill

✅ **Use when**:
- User describes a project idea and explicitly or implicitly asks what to learn first
- User says "I don't know where to start" for a project idea
- User wants a prerequisite knowledge map before diving into building
- User is planning a learning journey for a specific goal

❌ **Don't use when**:
- User is asking for general programming knowledge (e.g., "how do I learn Python?")
- User is debugging or fixing existing code
- User is asking for implementation help on an active project
- User has already started building and is now asking how-to questions

---

## Example Walkthrough

**Project idea**: "I want to build an OSU beatmap AI generator"

**Decomposition**: This involves audio processing, domain-specific file formats, ML/AI concepts, data pipelines, and Python tooling.

**Categories**:
- OSU Domain Knowledge
- Audio Processing
- AI/ML Fundamentals
- Data Pipeline & Training
- Core Language & Tools
- Dev Fundamentals

**Learning Order**:
1. OSU beatmap format basics (what you're generating)
2. Audio file reading and BPM analysis (input understanding)
3. ML concepts: what generative models are (high-level framing)
4. Python file I/O and libraries (implementation basics)
5. Audio processing with librosa (domain tool)
6. Sequence modeling concepts (ML specifics for time-series)
7. Datasets and training pipelines (data engineering)
8. Ready to start building!
