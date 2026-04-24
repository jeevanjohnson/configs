# AI Workflow

## Overview

This repository documents how I configure GitHub Copilot to support my AI-assisted development workflow. The setup prioritizes three core goals: rapid development, long-term maintainability, and continuous learning through code.

**Configuration location:** `C:\Users\jeeva\.copilot`

## Core Concepts

### Instructions

Always-on rules that govern how the model responds across all tasks.

- Applied automatically to your entire workflow
- Define coding standards and preferences
- Examples: "Always use Python," "Never use library X," "Prefer readable solutions over clever ones"

### Skills

Specialized workflows that load on-demand when a specific task requires them.

- Triggered by the model when relevant to the current task
- Think of them as callable functions the model can use
- Examples: "enhance commit messages," "improve documentation quality"

### Agents

AI entities configured with specific instructions and skills to perform tasks.

- Represents the AI model with a customized rule set (instructions) and capabilities (skills)
- Instructions define what the agent can do; the agent is the executor
- Enable multi-stage workflows with tailored constraints and behavior