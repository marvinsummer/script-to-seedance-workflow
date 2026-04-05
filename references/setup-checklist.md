# Setup Checklist

Use this checklist before starting the screenplay workflow for a new user.

## Required Tools

- `lark-cli`
- `dreamina`
- `curl`

## Required Accounts / Auth

### Feishu / Lark

Need:

- a usable Feishu account
- `lark-cli` installed
- `lark-cli` authenticated with the correct user identity

Minimum check:

```bash
lark-cli docs +create --help
```

If user auth is needed, use the appropriate `lark-cli auth login ...` flow before continuing.

### Dreamina

Need:

- `dreamina` installed
- login session already saved locally

Minimum checks:

```bash
dreamina --help
dreamina user_credit
```

If not logged in:

```bash
dreamina login
```

## Video Authorization Note

Some higher-risk video models or modes may require one-time confirmation in the Dreamina web UI before CLI submission succeeds.

Typical symptom:

- `AigcComplianceConfirmationRequired`

If that appears:

1. pause CLI testing
2. ask the user to complete the authorization in Dreamina Web
3. retry the same command after confirmation

## Recommended Preflight Questions

Ask these before executing the main workflow:

1. Is `lark-cli` installed and already authenticated?
2. Is `dreamina` installed and already logged in?
3. Should I help install or authenticate anything first?
4. If video testing is planned, has Dreamina web authorization already been completed for the chosen model?

## Rule

Do not start parsing, document creation, image generation, or video generation until these prerequisites are confirmed.
