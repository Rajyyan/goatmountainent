# goatmountainent.com on EmDash + Cloudflare

The Goat Mountain Enterprises site, rebuilt from the original Wix site in [EmDash](https://github.com/emdash-cms/emdash). It runs on Cloudflare Workers, with the `goatmountain` D1 database and the `goatmountain-media` R2 bucket.

## Pages

| Page | URL | Content |
|---|---|---|
| Home | `/` | Skyline background, logo card, "Vault Cash Provision & Financing", the notice, association logos |
| Privacy Policy | `/privacy-policy` | The existing policy text |

Edit everything in the admin at `/_emdash/admin` → Pages:
- **Home → Hero block:** logo (image), headline, notice (subheadline).
- **Home → gallery "background":** the skyline photo.
- **Home → gallery "associations":** the membership logos.
- **Home → gallery "site-icon":** not shown on the page; holds the square icon.

## Deploy

Cloudflare Workers Builds deploys every push to `main`:
- Build command: `pnpm run build`
- Deploy command: `npx wrangler deploy`

On a fresh database, open `/_emdash/admin` and run the setup wizard with **Sample content**. That loads the pages and copies the images from Wix into R2, so do it before cancelling Wix.

## Local development
```bash
pnpm install
pnpm dev     # http://localhost:4321 and /_emdash/admin
```
