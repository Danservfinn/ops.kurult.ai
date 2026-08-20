# ops.kurult.ai

Public Kurultai ops board. Tracks and owners, kept by Jebe. No books, no secrets, no invented figures.

## Invariants

- No build system, no framework, no webfonts, no analytics. The committed files are the artifact.
- Jebe owns the board copy. Front end stands the tracks he hands; empty or unknown stays empty or unknown.
- Token usage stays visible with empty figures when no public-safe source exists — never invent spend or counts.
- No books / finance figures, no personal mail, no secrets, API tokens, agent UUIDs, or `.env` in this repo.
- Nobody sends email or LinkedIn from this host. x402 is not a topic here.
- One ops repo and one Pages project (`ops-kurult-ai`). Do not invent new project names.
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

## Related Pages projects

Already named in their READMEs — do not invent new ones: `ops-kurult-ai`, `roster-kurult-ai`, `gtm-kurult-ai`, `kurultai-apex`.

## Verify after deploy

```sh
curl -sI https://ops.kurult.ai/            # 200 text/html, server: cloudflare
curl -sI https://ops.kurult.ai/llms.txt    # 200 text/plain
dig +short kurult.ai MX                    # unchanged — mail records are never touched
```
