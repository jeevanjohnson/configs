---
name: youtube-research
description: >
  Use this skill whenever a user wants to learn about a topic through YouTube videos,
  wants video recommendations for a subject, or asks "what should I watch to understand X",
  "find me YouTube videos about X", "best videos to learn X", "help me learn X through videos",
  or any variation of wanting curated video content to deeply understand a topic.
  Also trigger when a user says "research X for me" and would benefit from video learning,
  or when they ask to "fully understand" a topic and video content would help.
  This skill performs structured research on the topic first, then finds and ranks the best
  YouTube videos that together give the user a complete, layered understanding from beginner
  to advanced.
---

# YouTube Research Skill

Helps users deeply understand any topic by researching it and finding the best YouTube videos
to watch — curated, ordered, and explained so they know exactly why to watch each one.

**For the agent:** This skill delegates research to the **Explore** subagent, uses `fetch_webpage` to verify videos,
and applies quality curation to build a learning path from beginner to advanced.

---

## Workflow

### Step 1 — Understand the topic scope

Before searching, briefly assess:
- Is this a broad domain (e.g. "machine learning") or a specific question (e.g. "how does backpropagation work")?
- What level of depth is implied? Adjust the search strategy accordingly.
- Break broad topics into logical sub-themes (foundations, mechanisms, applications, debates, etc.)

### Step 2 — Research the topic first

Build a real understanding of the topic before hunting for videos using `runSubagent` with the **Explore** agent. This is what separates a curated list from a random one.

**How to research:**
- Delegate to Explore agent with queries like: "Research [topic]: what are the core concepts, key subtopics, common misconceptions, and recent developments?"
- Ask about foundational knowledge vs. advanced nuances
- Gather context on expert perspectives and best practices in the field

Do **2–4 research queries** on the topic itself before searching YouTube.

### Step 3 — Find the best YouTube videos

Now search YouTube specifically. Use `runSubagent` with **Explore** agent to find relevant videos:

**Ask the agent to find:**
- "[Topic] explained" videos for beginner overviews
- "[Topic] deep dive" or comprehensive lecture videos
- "[Topic] tutorial" or course videos
- Specific well-known educators in the field (e.g. 3Blue1Brown for math, Kurzgesagt for science, Andrej Karpathy for AI)
- Conference talks or lectures (MIT, Stanford, etc. specific to topic)
- Visual/animated explainers on specific subtopics

**Once promising videos are found:**
- Request YouTube URLs from the Explore agent
- Verify each URL with `fetch_webpage` to confirm title, description, and relevance

**For each promising video, fetch its YouTube page** using `fetch_webpage` on the YouTube URL to verify:
- Actual title, channel name, date, and description
- Whether content matches the depth and scope needed
- Any paywalls, age restrictions, or accessibility notes

### Step 4 — Curate and rank

Select **6–10 videos** that together form a complete learning path. Apply these criteria:

**Quality signals:**
- High view count relative to upload date
- Reputable channel or recognized expert
- Description matches the actual depth needed
- Covers something unique the other videos don't

**Diversity requirements — your list MUST include:**
- At least 1 beginner/overview video
- At least 1 deep-dive or technical video  
- At least 1 visual/animated explainer if available
- At least 1 longer lecture or comprehensive walkthrough
- Mix of formats: short explainers, long lectures, interviews, demos

**Exclude:**
- Clickbait titles with no substance
- Outdated content on fast-moving topics (flag if unavoidable)
- Redundant videos covering the same ground

### Step 5 — Present the results

Present the videos in a **recommended watch order** (not just a ranked list). Group into phases if helpful:

**Format for each video:**
```
## [Phase Name] (optional grouping)

### [N]. [Video Title]
**Channel:** [Channel Name]  
**Link:** [Full YouTube URL]  
**Length:** [duration if known]  
**Why watch this:** [2–3 sentences explaining what this covers, why it's good, and what the viewer will get from it]  
**Best for:** [Beginner / Intermediate / Advanced]
```

**After the list, include:**
- A "Suggested Watch Order" with a brief narrative explaining the progression
- A "If you only watch one" recommendation with a sentence explaining why
- Any key concepts to look up alongside the videos (books, papers, docs)

---

## Tool Usage & Limitations

**Available tools:**
- `runSubagent` with **Explore** agent for topic research and background gathering
- `fetch_webpage` to verify YouTube URLs and fetch video descriptions/metadata
- Direct knowledge to propose well-known educators and channels

**Limitations:**
- I don't have direct search API access, so I rely on:
  - Your knowledge of good channels and educators
  - Known experts in each field (e.g., 3Blue1Brown for math, Kurzgesagt for science)
  - Searching by specific educator names or channel recommendations
- Always verify URLs with `fetch_webpage` before including them

---

## Quality Standards

- Never fabricate video URLs. Use only URLs you've verified with `fetch_webpage` or that you know with high confidence
- Always include the actual YouTube link (https://www.youtube.com/watch?v=...)
- If a channel is paywalled or the video is behind a subscription, note it
- Prefer timeless content over trending content unless the topic is current events
- For technical topics, don't over-index on beginner content just because it's popular
- When uncertain about a video, say so rather than guessing about its content

---

## Example Trigger Phrases

- "What YouTube videos should I watch to understand quantum computing?"
- "Find me the best videos to learn Rust programming"
- "I want to deeply understand the French Revolution — what should I watch?"
- "Research blockchain for me and give me the best videos"
- "Help me learn about stoic philosophy through YouTube"
