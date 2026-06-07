---
name: agent-builder
description: >-
  Guides design and implementation of new agentic systems (workflows, multi-agent
  orchestration, tool use). Use when the user asks to build a new agentic system
  or review/audit an existing one. Do not use for incremental changes, bug fixes,
  or refactors to an existing system unless the user explicitly asks to redesign,
  rearchitect, or replace it.
---

# Agent Builder

Agentic systems consist of one or more agents working together toward a common goal. Common workflow patterns:

1. **Prompt Chaining** — A task is decomposed into a sequence of steps, where each LLM call processes the output of the previous one. Ideal when the task can be cleanly decomposed into fixed subtasks.
2. **Parallelization** — A task is classified and directed into specialized, independent follow-up tasks. Ideal when there are distinct categories better handled separately and classification can be done accurately (LLM or traditional classifier). Use when you know the categories upfront and need separation of concerns.
3. **Router** — Inputs are sent to multiple LLMs or handlers and outputs are aggregated programmatically. Effective when a task can be divided into subtasks and parallelized for speed, or when multiple perspectives are necessary. Two variations:
  - **Sectioning** — A task is broken into independent subtasks running in parallel
  - **Voting** — A task is passed multiple times through different handlers to get diverse outputs
4. **Orchestrator–Worker** — A central LLM dynamically breaks down tasks, delegates them to workers, and synthesizes their results. Well-suited for complex tasks where subtasks are unpredictable and undefined at the start.
5. **Evaluator–Optimizer** — One LLM generates an initial response while another provides evaluation and feedback, in a loop. Works well when there are clear evaluation rules.

**Parallelization vs Router:** Parallelization classifies then fans out to specialized handlers. Router aggregates multiple LLM perspectives or parallel branches (sectioning or voting) without necessarily requiring upfront classification.

Workflows and agents are often confused but are distinct. A **workflow** orchestrates LLMs and tools through predefined code paths (prescriptive system or DAG). An **agent** dynamically directs its own processes and tool usage.

## When to use

- User asks to **build**, **design**, or **architect** a new agentic system from scratch
- User asks to **review**, **audit**, or **evaluate** an existing agentic system (architecture, workflow choice, agent boundaries)
- User describes a greenfield task and wants help choosing workflow type (chaining, parallelization, router, orchestrator–worker, evaluator–optimizer)

## When not to use

- Incremental changes: bug fixes, adding a tool, tuning prompts, small feature work on an existing system
- Refactors or rewrites of an existing system **unless** the user explicitly asks to redesign, rearchitect, replace, or "start over"
- General coding tasks that happen to involve an LLM but are not about system design

If scope is ambiguous, ask: "Are you building/reviewing the system architecture, or changing something specific in the existing setup?"

## How to use

1. **Clarify intent** — new build vs review vs (explicit) redesign
2. **Gather constraints** — task type, evaluation criteria, step predictability, latency/cost, tool needs
3. **Recommend workflow type** using the taxonomy above; state why alternatives were rejected
4. **For reviews** — map the current system to a workflow type, note gaps, suggest targeted improvements; do not propose full rewrites unless asked
5. **For new builds** — propose architecture, agent boundaries, and implementation order before coding

## Examples

**Use this skill**

- "Help me design a multi-agent system for research and summarization"
- "Review our current agent architecture and suggest improvements"
- "Should we use orchestrator–worker or prompt chaining for this task?"

**Do not use this skill**

- "Fix the retry logic in our existing agent" → handle as normal code change
- "Add a new MCP tool to the agent" → incremental change unless user asks for redesign