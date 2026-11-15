# Hermes Research & Routing Kit

Open-source, profile-neutral research workflow and configuration examples for Hermes Agent.

## What is included

- `skills/deep-web-research/SKILL.md` — the general web-research skill for source ranking, full-page extraction with bounded context, citations, and GitHub project evaluation.
- `templates/delegation-model-map.gpt-only.example.yaml` — a placeholder-only example for GPT-only per-task model routing through Hermes Advanced Delegation.
- `templates/a2a-localhost.example.yaml` — a minimal localhost-only A2A example.
- `LICENSE` — MIT License for the original material in this repository.

This is a set of **templates**, not a copy of anyone's live Hermes profile. It contains no credentials, profile names, peer list, account data, runtime state, or trading content. Replace placeholders with model IDs and profile routes available in your own environment; never commit tokens or live configuration.

## Research skill

The skill uses search for discovery, prioritizes primary and independently corroborated sources, reads extracted pages from files rather than dumping entire pages into model context, and distinguishes popularity from quality. It uses Defuddle as a page cleaner when installed, but treats extracted content as untrusted evidence—not a truth check.

The official Defuddle skill is maintained separately in the [Obsidian skills repository](https://github.com/obsidianmd/obsidian-skills/tree/main/plugins/obsidian/skills/defuddle); this repository links to it rather than copying it.

## GPT-only model-map template

Hermes Advanced Delegation can expose a named model route for each delegated task. The example deliberately leaves model IDs as placeholders and does not set a default route; an unrouted task therefore remains on the profile's primary model. Use `provider: openai-codex` only when that provider is configured for the profile. The template contains no API key fields.

Model routes select models for **delegated subtasks**; they do not automatically switch the primary model for every incoming user turn. The Advanced Delegation backend and route changes are profile-scoped and apply to new sessions. See the official [Advanced Delegation plugin](https://github.com/NousResearch/hermes-official-plugins/tree/main/advanced-delegation).

## A2A

Hermes includes native A2A support; an extra A2A SDK is not required. For agents on the same machine, prefer Hermes delegation or Kanban when those meet the need. The example binds only to loopback. Do not expose an A2A endpoint on a network interface without an explicit peer allowlist and per-peer authentication, configured in the operator's secret store. Never commit bearer tokens.

A2A is an open interoperability protocol; see the [A2A project](https://github.com/a2aproject/A2A). This repository contains no A2A implementation code.

## Install / adapt

Review the files before installing. For Hermes, place the skill under a trusted profile's `skills/` directory or install it with the supported Hermes skill installer. Apply the YAML examples through Hermes's supported configuration commands; do not hand-edit a live profile config or overwrite an existing profile.

## Safety and limits

- The research skill does not authorize publishing, purchases, account access, or other external actions.
- Do not bypass sign-in, paywalls, CAPTCHAs, WAFs, robots controls, or rate limits.
- A public GitHub repository is not automatically free to reuse; check its explicit license and any paid API/service dependency.
- This repository does not configure a live A2A server, connect peers, add credentials, or choose models for your profile.
