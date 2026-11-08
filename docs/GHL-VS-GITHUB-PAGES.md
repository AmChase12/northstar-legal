# GHL SPA vs GitHub Pages legal content

Compared Nov 7, 2026. Live routes were not changed. PR #1 stays open (public-safe Cursor rules only).

## Two documents, one canonical URL

| Surface | URL that actually serves HTML | Canonical tag / intended URL |
|---|---|---|
| GHL Vite SPA (Cloudflare) | `https://www.northstardigi.agency/privacy-policy` and `/terms-of-service` return the **homepage** `index.html` until JavaScript hydrates | Homepage canonical is `https://www.northstardigi.agency/` |
| GitHub Pages | `https://amchase12.github.io/northstar-legal/privacy/` and `/terms/` return unique static HTML | Those files still point canonical at `www.northstardigi.agency/privacy-policy` and `/terms-of-service` |

Carriers, curl, and non-JS checkers therefore see marketing HTML at the registered agency URLs. After JS, a browser can show GHL React pages `XD` (privacy) and `qD` (terms) from `/assets/index-ynHxTRw0.js`.

This is SPA fallback plus two different legal texts. It is not a GitHub Pages outage.

## Privacy

| | GHL SPA (hydrated) | GitHub Pages `privacy/` |
|---|---|---|
| Dated | Version 1 · November 2, 2026 | September 16, 2026 |
| Phone | (304) 484-4648 | (304) 381-1611 |
| SMS / A2P | “Calls, Texts, and Consent” is general (clients responsible for lists). **No STOP/HELP, no “we do not share mobile opt-in data” clause, no A2P.** | Dedicated SMS section: two consent boxes, STOP/HELP, not a condition of purchase, **mobile opt-in never shared with third parties** |
| Scope | Website, CRM, AI, GHL, recordings, payments | Website + SMS program for Northstar Digital LLC |

## Terms / SMS program

| | GHL SPA (hydrated) | GitHub Pages `terms/` |
|---|---|---|
| Dated | July 13, 2026 | September 16, 2026 |
| Program name | Northstar Digital SMS Notifications | Same |
| STOP / HELP / rates / carriers | Present | Present |
| Age 18+ | Present | Absent |
| Customer care | HELP, (304) 381-1611, `business@northstardigitalmarketing.info` | HELP, same email, (304) 381-1611 |
| Contact on privacy | GHL privacy uses 484-4648; GHL terms still use 381-1611 | 381-1611 throughout |

Form checkboxes on the GHL homepage already describe optional non-marketing and marketing SMS with STOP/HELP. That copy is **not** in the GHL privacy page body.

## Recommended source of truth

Use **one carrier-facing HTML document per URL**, served without JavaScript, at `www.northstardigi.agency/privacy-policy` and `/terms-of-service`.

Preferred content mix (do not apply until approved):

1. Keep GitHub Pages SMS/A2P clauses (non-sharing of mobile opt-in, STOP/HELP, dual consent) — that is what 10DLC reviewers look for.
2. Fold in GHL’s November 2 privacy sections that GitHub Pages lack (AI/CRM processors, recordings, client-vs-Northstar data control) **without** dropping the SMS non-sharing sentence.
3. Pick one public phone number (484-4648 vs 381-1611) and one “last updated” date.
4. Prerender those pages on the live host (or Cloudflare/GHL static files). Update GitHub Pages canonicals only after the agency URLs return that same HTML.
5. Keep `/policies` and `/ai-policy` as GHL-only client documents; do not treat them as the A2P privacy/terms URLs.

Do not redirect traffic, merge this PR as a substitute for prerendering, or change DNS until that source of truth is chosen.
