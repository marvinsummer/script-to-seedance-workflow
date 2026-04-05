---
name: script-to-seedance-workflow
description: Use when turning a screenplay into角色解析、场景解析、Dreamina角色图/场景图、飞书文档沉淀、以及 Seedance 2.0/2.0fast 参考生视频提示词与测试命令
---

# Script To Seedance Workflow

## Overview

Use this skill for a full screenplay-to-visual-dev pipeline: parse the script, create structured Feishu documentation, generate Dreamina image prompts, write Seedance prompts for reference-based video generation, and run controlled multimodal video tests.

Keep the workflow document-centric. Every major artifact should be written into one Feishu doc so the user can review, revise, and reuse the whole chain later.

## When To Use

Use this skill when the user wants any of the following:

- Parse a screenplay into角色列表 and 场景列表
- Turn a script into Dreamina角色图 or 场景图
- Turn script beats into Seedance 2.0 / 2.0fast prompts
- Maintain one Feishu doc containing script analysis, prompts, generated images, and video testing notes
- Test multimodal video generation using角色图 + 场景图 + prompt

Do not use this skill for:

- Generic image generation unrelated to a screenplay
- Traditional shot-listing that does not depend on image references
- Pure script writing, rewriting, or dialogue polishing

## Workflow

### 0. Confirm Dependencies First

This skill is intended to work for new users too, so do not jump straight into parsing or generation.

Before running the workflow, confirm whether the required dependencies are already installed and authenticated.

Required tools:

- `lark-cli`
- `dreamina`
- `curl`

Required readiness:

- Feishu / Lark account access is available
- `lark-cli` can authenticate as the correct user
- `dreamina` is installed locally
- `dreamina login` has been completed

Ask for confirmation first. A good preflight check is:

1. Is `lark-cli` installed and already authenticated?
2. Is `dreamina` installed and already logged in?
3. If Dreamina video generation will be used, has the user already completed any required web-side authorization for the selected model family?

If dependencies are missing:

- pause the workflow
- help the user install or authenticate the missing dependency
- only continue after the environment is ready

If the user explicitly asks you to handle installation, do that setup work before entering the main workflow.

### 1. Parse The Script

Extract and structure:

- 角色列表
- 场景列表
- 蒙太奇/快速剪辑子场景 if they should be managed independently
- 剧本原文

Rules:

- Separate named characters, functional characters, and crowd/group roles
- Scene names must be stable and reusable later as image section titles
- If montage beats matter visually, split them into explicit sub-scenes

### 2. Create Or Continue The Feishu Doc

Prefer a single running document for the whole workflow.

Document naming rule:

- Always include screenplay title and generation time
- Time must be precise to the hour
- Recommended format:
  - `《剧本名》视觉开发工作流文档 - YYYY-MM-DD HH点`

Example:

- `《红线》视觉开发工作流文档 - 2026-04-05 23点`

Core sections:

1. 角色列表
2. 场景列表
3. 剧本原文
4. 角色图片
5. 场景图片
6. Seedance 2.0 分镜提示词
7. 视频测试记录

### 3. Pause At Confirmation Gates

Before continuing past key points, stop and let the user confirm.

Required confirmation points:

1. After script parsing
   - Confirm角色列表, 场景列表, 群像拆分
2. After role image prompts are drafted
   - Confirm style, naming, group strategy
3. After scene image prompts are drafted
   - Confirm scene-title alignment and whether scenes must be无人物
4. After Seedance prompts are drafted
   - Confirm they follow reference-based video logic rather than generic storyboard logic
5. Before any video test
   - Confirm the exact scene, the exact reference images, and the exact generation params

If the user says to proceed without pauses, that explicit instruction overrides this default.

### 4. Generate Role Images

Use Dreamina `text2image`.

Rules:

- Separate single-character prompts from group/crowd prompts
- Keep titles aligned with the role list in the Feishu doc
- For group roles, say clearly that the image is a群像角色设定图
- If the user specifies fixed style prefixes, preserve them exactly

After generation:

- Insert images into the Feishu doc under matching role headings
- Do not rely on temporary external image URLs as permanent doc assets
- Download, upload into Feishu, then delete local temporary files

### 5. Generate Scene Images

Use Dreamina `text2image`.

Rules:

- Scene image headings must match the scene list exactly
- Default scene prompts should emphasize environment, atmosphere, spatial cues, and cinematic framing
- If the user asks for scene boards without people, explicitly enforce:
  - `无人物`
  - `no people`
  - `no character`
  - `empty scene`
- Do not let role details leak into pure environment prompts unless the user explicitly wants人物入镜

After generation:

- Insert images into the Feishu doc under matching scene headings
- Delete temporary local files after upload

### 6. Write Seedance Prompts

Seedance prompts here are not traditional frame-by-frame storyboard notes.

They are reference-based video prompts meant to be used with:

- one or more角色图
- one场景图 or multiple visual references
- a textual motion / performance / camera prompt

Prompt writing rules:

- Do not over-describe character appearance if role reference images are already supplied
- Focus on:
  - camera distance and movement
  - blocking
  - action beats
  - performance tone
  - dialogue
  - pacing
  - realism / cinematic feel
- Keep prompts readable and production-oriented
- Let the model infer micro-timing unless the user explicitly wants strict durations

Read prompt patterns from [references/prompt-templates.md](references/prompt-templates.md).

### 7. Run Video Tests Carefully

Use Dreamina `multimodal2video` for reference-based tests.

Before submitting:

- Verify the exact scene image is attached
- Verify only the needed role images are attached
- Avoid passing unrelated角色图
- Confirm model/version/aspect/duration/resolution against user request

Default testing output to report:

- which references were used
- submit_id
- current gen_status
- queue state if available

Read command patterns from [references/cli-recipes.md](references/cli-recipes.md).

## Reference Selection Rules

For multimodal video tests:

- Single-character action in one environment:
  - use one场景图 + that character's role image
- Two-character interaction:
  - use one场景图 + both character images
- Crowd or group interaction:
  - use one场景图 + relevant group role image(s)

Avoid overloading the request with unnecessary references. More images are not automatically better.

## Feishu Maintenance Rules

- Keep one doc per active workflow version
- Append sections with clear titles
- Keep image section titles identical to the structured role/scene names
- If repeated trials create clutter, offer to clean the document structure
- If Feishu access is not ready yet, stop before document creation and resolve authentication first

## Cleanup Rules

Whenever local files are downloaded only to be re-uploaded:

1. Save into a temporary local directory inside the current workspace
2. Upload into Feishu
3. Delete the temporary files
4. Confirm the temporary directory no longer exists

Never leave bulk generated intermediates behind unless the user explicitly asks to keep them.

## Common Mistakes

- Starting the workflow before `lark-cli` or `dreamina` is installed
- Starting generation before Feishu auth or Dreamina login is complete
- Forgetting that some Dreamina video modes may require one-time web authorization
- Using a scene title in prompts that does not match the Feishu doc heading
- Treating a群像角色 as a single-character reference
- Writing Seedance prompts like static image prompts
- Passing the wrong角色图 into `multimodal2video`
- Embedding temporary external image links into Feishu as if they were permanent
- Forgetting to include date and hour in the Feishu doc title

## References

- Prompt templates: [references/prompt-templates.md](references/prompt-templates.md)
- Dreamina / Seedance command recipes: [references/cli-recipes.md](references/cli-recipes.md)
- Dependency and auth checklist: [references/setup-checklist.md](references/setup-checklist.md)
