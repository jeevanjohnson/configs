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

Helps users deeply understand any topic by researching it and finding the best videos
to watch via Invidious — curated, ordered, and explained so they know exactly why to watch each one.

**For the agent:** This skill delegates research to the **Explore** subagent, uses `fetch_webpage` to search Invidious
and verify videos, and applies quality curation to build a learning path from beginner to advanced.

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

Search videos via **Invidious** (privacy-focused YouTube frontend) using `fetch_webpage`:

**Search Invidious directly for:**
- `https://inv.nadeko.net/search?q=[topic]+explained`
- `https://inv.nadeko.net/search?q=[topic]+tutorial`
- `https://inv.nadeko.net/search?q=[topic]+deep+dive`
- `https://inv.nadeko.net/search?q=[educator+name]` (for known experts)
- `https://inv.nadeko.net/search?q=[topic]+lecture`

**Example searches:**
- `https://inv.nadeko.net/search?q=big+O+notation`
- `https://inv.nadeko.net/search?q=Master+Theorem+algorithm`
- `https://inv.nadeko.net/search?q=algorithm+complexity+analysis`

**For each promising video, fetch its Invidious page** using `fetch_webpage` on the Invidious URL (format: `https://inv.nadeko.net/watch?v=[VIDEO_ID]`) to verify:
- Actual title, channel name, view count, and description
- Upload date and relevance to learning goals
- No login walls or accessibility issues (Invidious is login-free)

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
- `runSubagent` with **Explore** agent for topic research and background knowledge
- `fetch_webpage` to search Invidious and verify video URLs/metadata
- Direct knowledge to propose well-known educators and channels

**Search method:**
- Use `fetch_webpage` with Invidious search URLs: `https://inv.nadeko.net/search?q=[QUERY]`
- Invidious provides YouTube content without login walls
- Parse search results to extract video URLs in format: `https://inv.nadeko.net/watch?v=[ID]`
- Fetch individual video pages to confirm titles, descriptions, view counts, and dates

**Advantages:**
- No authentication required
- Privacy-focused (no tracking)
- Full access to YouTube video metadata
- Can search by topic, educator name, or video type
- Works reliably via `fetch_webpage`

---

## Quality Standards

- Never fabricate video URLs. Use only URLs you've verified with `fetch_webpage` from Invidious search results
- Always include the actual Invidious link (https://inv.nadeko.net/watch?v=...)
- Verify video metadata: title, channel, view count, upload date before recommending
- If a video requires YouTube Premium or has accessibility issues, note it
- Prefer timeless content over trending content unless the topic is current events
- For technical topics, value high view counts and reputable channels (Abdul Bari, MIT OpenCourseWare, NeetCode, etc.)
- When uncertain about a video, say so rather than guessing about its content
- **Invidious advantage:** All searches and verification happen without login, making this completely accessible

---

## Example Trigger Phrases

- "What videos should I watch to understand quantum computing?"
- "Find me the best videos to learn Rust programming"
- "I want to deeply understand the French Revolution — what should I watch?"
- "Research blockchain for me and find the best educational videos"
- "Help me learn about stoic philosophy through video"
- "Curate the best videos for studying algorithm complexity"
