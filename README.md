# script-to-seedance-workflow

A Codex skill for turning a screenplay into a structured visual development workflow with Feishu, Dreamina, and Seedance.

## What this skill does

This skill helps transform a screenplay into:

- a structured character list
- a structured scene list
- a Feishu workflow document
- Dreamina role-image prompts
- Dreamina scene-image prompts
- Seedance reference-based video prompts
- controlled multimodal video test steps

## Included files

- `SKILL.md`: the main skill definition
- `references/prompt-templates.md`: prompt templates for roles, scenes, and Seedance
- `references/cli-recipes.md`: Dreamina and Seedance CLI command patterns
- `references/setup-checklist.md`: setup and authentication checklist
- `agents/openai.yaml`: agent metadata

## Requirements

Before using this skill, make sure the following tools are available:

- `lark-cli`
- `dreamina`
- `curl`

You should also confirm:

- `lark-cli` is installed and authenticated
- `dreamina` is installed and logged in
- any required web-side authorization for video generation is already completed

## Workflow overview

1. Confirm dependencies and authentication
2. Parse the screenplay into characters and scenes
3. Create or continue one Feishu workflow document
4. Draft and confirm role-image prompts
5. Draft and confirm scene-image prompts
6. Write Seedance reference-based video prompts
7. Run controlled multimodal video tests

## Notes

This repository contains the skill definition and supporting references only.
Users should review and adapt prompts, tool setup, and workflow details for their own environment and project needs.
