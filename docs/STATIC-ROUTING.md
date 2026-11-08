# Static routing for agency legal URLs (not applied)

Live check (Nov 7, 2026): `GET /`, `GET /privacy-policy`, and `GET /terms-of-service` on `www.northstardigi.agency` return the **same** marketing `index.html` (identical sha256). JavaScript then hydrates React routes.

Phone numbers in drafts are **not** chosen. Flag both for Chase:

- (304) 484-4648 — GHL privacy / site call link
- (304) 381-1611 — GitHub Pages and GHL terms HELP line

Do not publish until those are confirmed and the documents are approved.

## Target

After approval, curl **without JavaScript** must show:

| URL | Unique file | Must contain |
|---|---|---|
| `/privacy-policy` or `/privacy-policy/` | `privacy-policy/index.html` | `STOP`, `HELP`, mobile opt-in **never shared** for third-party marketing |
| `/terms-of-service` or `/terms-of-service/` | `terms-of-service/index.html` | program name, STOP/HELP, not a condition of purchase |
| `/` | existing SPA `index.html` | marketing homepage |

Three different sha256 values. Unique `<title>` and `<link rel="canonical">`.

Folder layout to upload (copies of `drafts/*.html` after phone freeze):

```
privacy-policy/index.html
terms-of-service/index.html
```

Those files already exist as `drafts/privacy-policy.html` and `drafts/terms-of-service.html`. Layout copies: `drafts/static-root/`.

## Cloudflare / GHL change (later)

Today every path falls back to the SPA `index.html`. After the two directories exist on the static host:

1. Add an exception so `/privacy-policy*` and `/terms-of-service*` are **not** rewritten to `/index.html`.
2. Prefer: file exists → serve it; else SPA fallback for `/call`, `/policies`, `/ai-policy`.
3. If GHL only allows “website pages,” create two pages whose **custom HTML** is the draft body (not the React app) at those slugs.

Do not add a blanket redirect from GitHub Pages until the agency URLs return the same HTML.

## Not in this PR

No DNS, no Cloudflare rule, no GHL page publish, no replace of GitHub Pages `privacy/` or `terms/`.
