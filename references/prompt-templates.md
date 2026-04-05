# Prompt Templates

Use these templates as starting points. Keep the user-specified style words unchanged when they provide mandatory prefixes.

## 1. Role Image Prompt

Template:

```text
[fixed style prefix if any]。[view/background requirements if any]。[角色身份]角色设定图，[年龄/气质/职业/服装/道具/情绪]。[单人 or 群像要求]。[构图和管理要求]。
```

Notes:

- For single characters, emphasize role identity and repeatability
- For group roles, explicitly say `群像角色设定图`
- If four-view output is required, put that requirement first and keep it consistent across all roles

## 2. Scene Image Prompt

Template:

```text
[fixed style prefix if any]。[场景名称]，[环境、光线、空间结构、道具痕迹、氛围]。电影叙事场景图，无人物，no people，no character，empty scene。
```

Notes:

- Keep the scene title exactly aligned with the scene list
- Do not mention appearing characters when the user wants environment-only boards
- If the user wants a scene with people later, treat that as a different prompt variant

## 3. Seedance Reference-Based Prompt

Template:

```text
[镜头类型]起镜，在 @[场景名] ，[环境状态与氛围]。@[角色A] [动作与表演]。如有互动，再写 @[角色B] [动作与表演 / 对白]。镜头在[动作节点]之间切换或推进，突出[情绪、张力、节奏]。无字幕，自由发挥分镜，要有真实电影感，动作自然，[其他风格要求]。
```

Notes:

- Assume角色图 and 场景图 are already fed as references
- Do not restate clothing and face details unless the prompt truly depends on them
- Prefer camera / action / rhythm / acting instructions over static description
- If the user wants looser timing, do not prescribe exact seconds

## 4. Multimodal Reference Selection

Use the smallest set that explains the shot:

- environment-only moment:
  - scene image only
- single-character beat:
  - scene image + one role image
- dialogue / confrontation:
  - scene image + both role images
- crowd / group beat:
  - scene image + relevant group image(s)

Too many references can dilute motion and identity.
