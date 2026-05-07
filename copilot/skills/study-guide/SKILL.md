---
name: study-guide
description: 'Generate a comprehensive study guide for any problem, topic, or concept from academic material. Trigger when you share homework, exam questions, lecture content, textbooks, or concepts you don''t understand. Produces: prerequisite map, conceptual explanation, step-by-step solution, common mistakes, and curated videos.'
argument-hint: 'Paste the problem, topic, or lecture content'
---

# Study Guide Skill

Turn any problem, topic, or lecture concept into a complete learning package that builds deep understanding.

## What This Skill Produces

1. **Prerequisite Map** — Every concept you need to already know (or quickly learn) before tackling this
2. **Concept Breakdown** — A clear, intuitive explanation of the core ideas involved
3. **Step-by-Step Solution / Deep Dive** — Walk through the problem or topic methodically
4. **Common Mistakes** — What trips people up on problems like this
5. **Video Learning** — Hand off to the `youtube-research` skill for curated videos on key concepts

## When to Use This Skill

Trigger this skill whenever you share:
- A **specific homework problem** or exam question
- A **lecture slide** or textbook excerpt
- A **concept you're struggling with** ("I don't get X", "how do I solve X", "explain this problem")
- A **topic you need to learn** ("what do I need to know for X", "help me understand X from class")
- Even if you only share a **topic name** — the skill will build a full learning guide

## Workflow

### Step 1 — Parse the Input

Identify what you gave. It could be:
- A **specific problem** (math equation, coding challenge, essay prompt)
- A **concept or topic** (eigenvectors, supply and demand, photosynthesis)
- **Raw lecture/slide content** — extract the core topic or problem
- A **vague struggle** ("I don't get recursion") — treat as a topic

If you uploaded an image of lecture slides, extract the key topic/problem from it.

If truly ambiguous, ask one clarifying question: **"What subject or course is this for?"**

---

### Step 2 — Build the Prerequisite Map

Before anything else, identify every concept needed to understand this topic or solve this problem.

**Assume very basic fundamentals are already known** (algebra, basic arithmetic, etc.). Only include prerequisites if they're directly needed for *this* problem/topic, or if the user explicitly mentioned struggling with something foundational.

Organize prerequisites into **two tiers**:

**Tier 1 — Must Know (Hard Prerequisites)**
Foundational concepts without which the problem/topic makes no sense at all.
List each with a one-sentence description of *why* it's needed here.

**Tier 2 — Helpful to Know (Soft Prerequisites)**
Concepts that deepen understanding or unlock insight, but aren't strictly blocking.

**Format:**
```
## 🧩 What You Need to Know First

### Must Know
- **[Concept]** — [Why it matters for this problem/topic]

### Helpful to Know
- **[Concept]** — [Why it deepens understanding]
```

---

### Step 3 — Conceptual Explanation

Explain the core idea(s) in plain language before any formulas or procedures. Focus on "what and why" before "how."

- Use an analogy or real-world example if possible
- Define any key terms that appear in the problem/topic
- Explain the intuition behind why the approach/concept works — not just what it is
- Keep this section accessible to someone learning for the first time

---

### Step 4 — Step-by-Step Solution or Deep Dive

**If a specific problem was given:**
- Solve it completely, one step at a time
- Annotate each step: explain *why* you're doing it, not just *what* you're doing
- Show intermediate work clearly (especially for math/science/CS)
- If multiple solution methods exist, show the most intuitive one first, then mention alternatives

**If a concept or topic was given:**
- Do a structured deep dive: definition → mechanism → examples → edge cases
- Include at least 1–2 worked examples that demonstrate the concept in action
- Progress from simple to complex
- Connect to real-world applications when relevant

---

### Step 5 — Common Mistakes & Pitfalls

List 3–5 things that commonly go wrong on problems like this one. Be **specific** — not generic advice like "be careful with signs," but actual conceptual traps people fall into.

**Format:**
```
## ⚠️ Common Mistakes

- **[Mistake]:** [What goes wrong and why — how to avoid it]
```

---

### Step 6 — To Master This Area, Also Study

After the solution, zoom out. List 3–6 related topics or problem types worth studying for full mastery.

These are *next steps* and sibling concepts — not prerequisites, but what to tackle next to build expertise.

**Format:**
```
## 📚 To Master This Area, Also Study

- **[Topic]** — [Brief reason / how it connects]
```

---

### Step 7 — Hand Off to YouTube Research Skill (Optional)

At the end of the guide, **ask the user if they want videos** to reinforce the concepts. Only proceed with the youtube-research skill if they explicitly request it.

**Transition language:**
> "Would you like me to find curated videos to reinforce these concepts? If so, I can search for the best resources on [main topic] and [key prerequisite]."

Only if they say yes, activate the `youtube-research` skill targeting:
- The main topic/problem type
- 1–2 of the most important prerequisites (if they seem likely to be gaps)

Use a focused, specific query — not the raw problem text.

---

## Output Format Summary

Present the full guide in this order:

1. `## 🧩 What You Need to Know First` (Prerequisite Map)
2. `## 💡 The Core Idea` (Conceptual Explanation)
3. `## 🔢 Step-by-Step` (Solution or Deep Dive)
4. `## ⚠️ Common Mistakes`
5. `## 📚 To Master This Area, Also Study`
6. Ask if the user wants videos (don't auto-handoff)

---

## Subject-Specific Notes

**Math / Physics / Engineering:**
- Always show full working — never skip steps
- Label variables and units clearly
- Draw ASCII diagrams for geometry or vector problems if helpful
- Show dimensional analysis for physics

**Computer Science / Programming:**
- Include pseudocode or actual code snippets
- Analyze time/space complexity if relevant
- Show example inputs/outputs for algorithms
- Trace through code execution for clarity

**Biology / Chemistry:**
- Use precise terminology but always define it
- Link mechanisms to real biological/chemical context
- Include diagrams of processes when helpful
- Connect structure to function

**History / Social Sciences / Humanities:**
- Frame concepts in terms of causes, effects, and context
- For essay-style questions, outline a strong argument structure
- Distinguish between correlation and causation
- Acknowledge multiple perspectives

**Economics:**
- Always pair theory with a concrete real-world example
- Distinguish between micro and macro contexts
- Use graphs or simple diagrams
- Connect to current events when relevant

---

## Quality Standards

✓ **Never skip the prerequisite map** — it's the most uniquely valuable part of this skill  
✓ **Solutions must be annotated** — the *why* at each step is as important as correctness  
✓ **Common mistakes are specific** — to this problem type, not generic advice  
✓ **Always ask about videos** — only activate youtube-research if user requests it  
✓ **Progress from simple to complex** — scaffold understanding step-by-step
