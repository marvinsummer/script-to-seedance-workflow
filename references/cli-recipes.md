# CLI Recipes

## Dreamina Role / Scene Image Generation

Basic pattern:

```bash
dreamina text2image \
  --model_version=4.0 \
  --ratio=16:9 \
  --resolution_type=2k \
  --poll=2 \
  --prompt="..."
```

Adjust ratio and prompt structure to match the user's request.

## Seedance Multimodal Video Test

Use `multimodal2video` when the user wants reference-based generation from role and scene images.

Basic pattern:

```bash
dreamina multimodal2video \
  --image ./scene.png \
  --image ./role-a.png \
  --image ./role-b.png \
  --prompt="..." \
  --model_version=seedance2.0 \
  --ratio=16:9 \
  --duration=15 \
  --video_resolution=720p \
  --poll=3
```

## Model Choice

- `seedance2.0`
  - quality-first
- `seedance2.0fast`
  - faster iteration

## Pre-Submit Checklist

Before each test:

1. Verify the scene image filename matches the intended scene
2. Verify each role image belongs to the intended role
3. Remove any unrelated role references
4. Re-check model / ratio / duration / resolution
5. Confirm whether the user wants a one-off test or a production attempt

## Typical Report Back

After submit, report:

- scene used
- role images used
- model_version
- ratio
- duration
- submit_id
- gen_status
- queue state when available
