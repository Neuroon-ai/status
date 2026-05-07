# Setup steps (manual — one-time)

After pushing this repo to `Neuroon-ai/status`, complete the following steps in order. Each takes ~1 minute.

## 1. Create the GH_PAT secret

Without `GH_PAT`, the Upptime workflows cannot commit history files or open incident issues.

1. https://github.com/settings/personal-access-tokens/new — create a **fine-grained** token.
2. Resource owner: `Neuroon-ai`.
3. Repository access: **Only select repositories** → `Neuroon-ai/status`.
4. Repository permissions:
   - **Actions**: Read and write
   - **Contents**: Read and write
   - **Issues**: Read and write
   - **Pages**: Read and write
   - **Pull requests**: Read and write
   - **Workflows**: Read and write
   - **Metadata**: Read-only (auto)
5. Expiration: 1 year.
6. Generate, copy the token (one-time display).
7. https://github.com/Neuroon-ai/status/settings/secrets/actions → **New repository secret**:
   - Name: `GH_PAT`
   - Value: paste the token

## 2. Enable GitHub Pages

1. https://github.com/Neuroon-ai/status/settings/pages
2. **Source**: GitHub Actions
3. **Custom domain**: `status.neuroon.ai`
4. **Enforce HTTPS**: tick once the cert provisions (after DNS).

## 3. Configure DNS (`status.neuroon.ai` → GitHub Pages)

Today `status.neuroon.ai` does **not** resolve. We need a `CNAME` pointing to the GitHub Pages host.

In your DNS provider for `neuroon.ai`:

| Type | Name | Value | TTL |
|---|---|---|---|
| `CNAME` | `status` | `neuroon-ai.github.io` | 300 |

> If your DNS provider doesn't support CNAME on a subdomain (most do), use 4 `A` records pointing to:
> `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`.

GitHub will auto-provision a Let's Encrypt cert (~10 min after the CNAME propagates).

## 4. Trigger the first run

The first uptime workflow runs automatically on the next 5-minute mark, but you can trigger it manually:

1. https://github.com/Neuroon-ai/status/actions/workflows/uptime.yml → **Run workflow**.
2. Then https://github.com/Neuroon-ai/status/actions/workflows/setup.yml → **Run workflow** (only the first time, to bootstrap the static site).
3. Wait ~3 min. Visit https://status.neuroon.ai. Should render with the 5 components.

## 5. (Optional) Email notifications

To get email when a component goes down, add SMTP credentials and uncomment the `notifications` block in `.upptimerc.yml`:

- `NOTIFY_USER`: SMTP user (e.g. `status@neuroon.ai`)
- `NOTIFY_PASS`: SMTP password / app password

## 6. (Optional) Watch this repo

Click the **Watch** button at the top of the repo → **Custom** → **Issues**. You'll get an email every time an incident issue is created.
