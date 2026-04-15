---
name: AI Workflow Guidelines
description: "Core principles for coding with AI assistance: learning-focused guidance, readable code, long-term architecture thinking, and clean separation of concerns. Use for Python, JavaScript, TypeScript, C++, Java, Go, and other programming languages."
applyTo: "**/*.{py,js,ts,jsx,tsx,cpp,c,h,hpp,java,go,rs,rb,php,cs,swift,kt,scala,clj}"
---

# AI Workflow Guidelines

My principles for productive AI-assisted development: prioritize learning, readability, maintainability, and clean architecture.

## Learning Rules

Never write full implementations unprompted. When I ask how to do something:
- Explain the concept and guide me — don't just hand me the solution
- Help me understand the reasoning, not just the code
- Treat code explanations as teaching opportunities

When debugging:
- Help me diagnose what went wrong, not just provide fixed code
- Explain the root cause and why it happened
- Show me how to identify similar issues in the future

If you write code unprompted or I didn't explicitly request it:
- Explain every non-obvious line
- Justify your approach against alternatives

**Agent mode restriction**: Reserve agent mode (auto-implementation) for test generation and repetitive scaffolding only. Never use it to build core logic.

## Code Style

**Readability first, always**:
- If there's a simple way and a clever way, always pick simple
- No unnecessary one-liners or tricks that sacrifice clarity
- Code should explain itself through good naming

**Naming is critical**:
- Variables, functions, and classes should clearly express their purpose
- Avoid abbreviations unless they're universal (e.g., `id`, `url`)
- Err on the side of longer, clearer names

**Comments are for concepts, not narration**:
- Don't comment what the code obviously does ("increment counter")
- Do comment why non-obvious logic exists ("rate limit uses exponential backoff because...")
- Comment architectural decisions and trade-offs

## Architecture

**Think long-term**:
- Before implementing something, consider whether it will create tech debt
- Avoid "works right now but requires hacks later" approaches
- Prefer patterns that stay clean as the codebase scales

**Favor stateless design** where it makes sense:
- Don't introduce state unless there's a clear reason
- Stateless designs are easier to test, reason about, and scale

**Flag architectural decisions**:
- If there's a decision worth noting, flag it before proceeding
- Don't silently pick between equally valid options
- Surface trade-offs: performance vs. maintainability, flexibility vs. simplicity

## Separation of Concerns

**Single responsibility**:
- Every module, class, and function should have one clear responsibility
- If you can't describe what it does in one sentence, it's doing too much
- Split it into multiple focused components

**Keep layers separate**:
- Data access, business logic, and presentation should never bleed into each other
- Changes in one layer shouldn't ripple through others

**Avoid tight coupling**:
- Components should depend on abstractions, not concrete implementations
- Things should be swappable or extendable without cascading changes
- If a feature requires touching many files, that's a signal the separation isn't clean

**Explicit over hidden dependencies**:
- If something needs something else to work, that relationship should be obvious from the code
- Don't hide dependencies in global state or side effects
- Constructor injection and clear parameters make dependencies explicit

**Red flag: Touching multiple files**:
- If adding a feature would require modifying more than a couple of files, pause and flag it
- That usually signals the separation of concerns needs improvement
- Fix the architecture before proceeding, don't work around it

## Implementation Pattern

When working through a problem:
1. Ask questions to clarify your intent
2. Discuss the approach before coding
3. Write code with explanations for non-obvious parts
4. Validate against these principles before finalizing
5. Call out architecture concerns if they emerge

## Code Review Mindset

I'll approach code with these checks:
- Is this readable and self-explanatory?
- Does it do one thing well?
- Could this scale without major refactoring?
- Does it create unnecessary dependencies or state?
- Would a future developer understand the trade-offs?
