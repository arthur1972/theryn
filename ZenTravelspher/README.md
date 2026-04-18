# ZenTravelspher

Local development:

1. Copy `.env.example` to `.env` and fill in secrets (do NOT commit `.env`).
2. npm install
3. npm start

Tests:

- npm test  (runs mocha tests)

Lint:

- npm run lint
- npm run format

Notes:
- Server exposes /api/ai/completion and /api/ai/chat endpoints (server-side proxy to OpenAI).
- Add your OpenAI key to .env as OPENAI_API_KEY.

Landing pages generation:
- Run `npm run generate:landings` (requires OPENAI_API_KEY) to auto-generate dist/landings/*.html for pre-defined cities.

Booking & affiliate flows:
- The server exposes POST /api/booking/suggest to analyze chat messages and return a booking suggestion with an affiliate link.
- Redirects to affiliate providers use /go/:provider?to=<encoded_url>&subid=<id> and are logged under data/affiliate_clicks.jsonl.

Deployment:
- A placeholder .github/workflows/deploy.yml was added. Configure secrets (VERCEL_TOKEN, SSH_PRIVATE_KEY, or HOST credentials) and update the deploy steps for your hosting provider.

Configure GitHub Actions secrets (recommended):
- In your repository: Settings → Secrets → Actions
  - VERCEL_TOKEN: token for Vercel (if deploying there)
  - SSH_PRIVATE_KEY and SSH_HOST: for rsync/ssh deploys
  - NODE_AUTH_TOKEN: if using private npm packages
  - OPENAI_API_KEY: (only if you plan to call OpenAI from CI; prefer production key stored in host env)

Notes:
- Do NOT commit .env with secrets. Use the repository secrets or your host provider's secret store.
- After configuring secrets, customize .github/workflows/deploy.yml with the specific deploy steps for your target platform.

## Environment variables

A new `.env.example` file has been added to the repository. Copy it to `.env` and fill in the required secrets before running locally. NEVER commit your `.env` file or any secrets to source control.

Required variables (brief):

- EXPEDIA_AFFILIATE_ID: Expedia affiliate ID used for affiliate wrapping.
- PARTNERIZE_AFFILIATE_ID: Partnerize affiliate ID used by the Partnerize adapter.
- PARTNERIZE_API_KEY: Partnerize API key for API calls (if using live mode).
- OPENAI_API_KEY: OpenAI API key used by the server-side AI proxy endpoints.
- ADMIN_PASSWORD: Local admin password (development use only).
- AFFILIATE_ALLOWLIST: Optional comma-separated domains allowed for affiliate wrapping.
- PROVIDER_MODE: Set to `mock` (local/dev) or `live` (production adapters).

Local setup:

1. Copy `.env.example` to `.env` and fill your secrets.
2. Install dependencies: `npm install`.
3. Start the server: `npm start`.

Deployment notes:

- Use your hosting platform's secret store (Vercel/Heroku/AWS Secrets Manager) to provide these environment variables in production. Do NOT store production secrets in the repository.
- If any keys were exposed during testing, rotate them immediately.
- Restart the server after changing environment variables.

AI engine / landings generation:

- The AI Affiliate Engine POC uses the server-side AI endpoints. Ensure `OPENAI_API_KEY` is present and the server is running before running the pipeline: `node services/ai_affiliate_engine/pipeline.js`.

