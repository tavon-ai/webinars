# Webinar: State of the Art Software Development With Coding Agents.

During a conversation at AI Week Frankfurt, someone raised doubts about the productivity gains of coding agents: “They’re not effective… They produce bad code…” As we talked, I realized that many of these concerns were based on individual experiences and didn’t reflect the recent developments and best practices in this fast-moving space. That’s exactly what I’d like to address in this session.

In this practical webinar, I’ll walk you through how I personally use modern coding agents to build my product TAVON.ai from the ground up. This isn’t a theoretical overview, nor is it meant to be comprehensive — it’s a hands-on look at how I use these tools to bootstrap a software company on my own.

## Agenda

* Claude Code et al: Modern Terminal based coding assistants. What's all that jazz?
* Software Architecture: That's what I care about. Or do I?
* Context Management aka "Use /clear"
* Spec Driven Development: What is it? Why I find it helpful.
* Guardrails: linting, building, testing - Help the assistant to help you.
* What's the Source of truth: Markdown? Code? Comments? Tests?
* Parallelization: What tasks do I parallelize? Or how many threads does my brain have?

## Intro
* Terminal-Based Coding Assistants: 
  * Terminal first
  * Tools: bash, Glob, grep, read, edit, write
* headless, ide integration
* agent sdk https://github.com/anthropics/claude-agent-sdk-demos

## Context Management
* CLAUDE.md
* Tokens / Auto-compaction
* /clear 

## How to
* ask Claude
* plan mode
* extended thinking
* @file @dir
* custom / commands

## basic workflows
* give me an overview of ...
* find me files ...
* fix [paste error code] 
* fix [paste image]
 
## advanced workflows
* research how [feature] was implemented. save as a file.
* debug ui by drawing borders
* provide more scripts
 * spec driven: ai-dev tasks / multi-phase plans

## Parallel development
* Git worktrees
* Different tasks

## Harness
* lint, build, test
* git
* run db commands manually

## Fails
* playwright
* MCPs

## Next
* Sub-Agents

## Demo
* new feature: link notes from the agent card
* new feature: only show gmail / google calendar if they are configured
* new more complex feature: more analytics on the dashboard. inlucing tests for the API


