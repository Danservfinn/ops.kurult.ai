# ops.kurult.ai

Public Kurultai ops board. Tracks and owners, kept by Jebe. No books, no secrets, no invented figures.

## Invariants

- No build system, no framework, no webfonts, no analytics. The committed files are the artifact.
- Jebe owns the board. He hands tracks and owners. Until he does, empty seats stay empty.
- Token usage is the one required track. Figures wait on a live source — never invent spend or token counts.
- No books / finance / Möngke numbers, no personal mail, no secrets, tokens, or `.env` in this repo.
- Nobody sends email or LinkedIn from this host. x402 is not a topic here.
- `llms.txt` lists this public host and durable public surfaces only — never gated hostnames.

## Deploy

Cloudflare Pages, direct upload of the repo root:

```sh
CLOUDFLARE_API_TOKEN=$(cat ~/.kublai/secrets/cloudflare-pages-api-token) \
  npx wrangler@latest pages deploy . --project-name ops-kurult-ai
```

Break-glass (no CLI): Cloudflare dashboard → Workers & Pages → ops-kurult-ai → Create deployment → drag this folder in.

Custom domain: attach `ops.kurult.ai` in Pages → Custom domains. Do not touch `kurult.ai` MX / mail records.

Public Pages auto-deploy after merge to `main`. Merge and domain attach wait on Danny.

Rollback: redeploy any prior deployment from the Pages dashboard (one click).

## Verify after deploy

```sh
curl -sI https://ops.kurult.ai/            # 200 text/html, server: cloudflare
curl -sI https://ops.kurult.ai/llms.txt    # 200 text/plain
dig +short kurult.ai MX                    # unchanged — mail records are never touched
```
