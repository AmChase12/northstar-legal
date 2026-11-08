# Unified legal pages — implementation plan (not live)

Prepared Nov 7, 2026. Live `northstardigi.agency` routes were **not** changed. GitHub Pages `privacy/` and `terms/` were **not** overwritten. Drafts: `drafts/privacy-policy.html` and `drafts/terms-of-service.html`.

## Goal

HTTP GET of `https://www.northstardigi.agency/privacy-policy` and `https://www.northstardigi.agency/terms-of-service` must return **unique HTML** (distinct sha256 from the marketing homepage), with unique `<title>` and `<link rel="canonical">`, **without requiring JavaScript**. That is what carriers and curl see today as the homepage.

## Content mix in the drafts

From **GitHub Pages** (keep for A2P): dual SMS consent, STOP/HELP, not-a-condition-of-purchase, **mobile opt-in never shared for third-party marketing**.

From **GHL SPA** (Nov 2 privacy / July 13 terms): AI/CRM/processors, recordings, client-vs-Northstar data control, 18+ SMS age line, STOP confirmation + rejoin.

Titles intended:

- `Privacy Policy — Northstar Digital LLC`
- `Terms of Service — Northstar Digital LLC`

Canonical tags already point at the agency URLs.

## Language that needs professional review (do not treat this as legal advice)

1. **Two public phone numbers** — GHL privacy uses (304) 484-4648; GitHub Pages and GHL terms SMS HELP use (304) 381-1611. Drafts list both. Pick one HELP number before filing with a carrier.
2. **Age 18+** — present in GHL terms, absent on GitHub Pages. Confirm it matches the 10DLC campaign.
3. **Processor vs non-sharing** — drafts say vendors may process data to deliver SMS, but opt-in is never shared for a third party's own marketing. An attorney should confirm that matches the actual Twilio/GHL/Telnyx setup.
4. **Recordings / AI** — GHL privacy discloses recordings and does not promise providers never train on data. Confirm this matches live call-recording settings.
5. **Client-vs-Northstar data control** — needed for receptionist installs; must not dilute Northstar's own SMS program disclosures.
6. **`/policies` and `/ai-policy`** — client commercial terms. Keep them off the A2P privacy/terms URLs.

This agent is not a lawyer. Do not file a 10DLC campaign on these drafts until reviewed.

## How to serve unique HTML (after approval — not now)

Today Cloudflare/GHL returns the **same** `index.html` for `/`, `/privacy-policy`, and `/terms-of-service` (identical sha256). The SPA then hydrates React routes.

Safe order:

1. Attorney/Chase review of the two draft files; freeze phone numbers and dates.
2. Place the reviewed files on the **live static host** as real files:
   - `/privacy-policy/index.html` (or `/privacy-policy.html` plus a rewrite)
   - `/terms-of-service/index.html`
3. **Exclude those two paths from the SPA fallback** (Cloudflare redirect / GHL “all routes → index.html”). Homepage `/` can stay the SPA.
4. Verify with curl (no JS):
   - `/` title still marketing
   - `/privacy-policy` title `Privacy Policy — Northstar Digital LLC` and body contains `STOP`, `HELP`, and “never shared”
   - `/terms-of-service` title `Terms of Service — Northstar Digital LLC`
   - Three different sha256 values
5. Only then replace GitHub Pages `privacy/index.html` and `terms/index.html` with the same bytes (or redirect Pages to the agency URLs). Canonicals already match.
6. Do not merge this PR as a substitute for step 3. Merging currently would only add drafts + docs unless those live files are also replaced.

Do not change DNS, GHL funnels, or Cloudflare rules until that sequence is approved.
