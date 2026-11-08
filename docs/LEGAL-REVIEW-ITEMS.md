# Items that require legal / 10DLC review (not published)

Drafts stay in `drafts/` and `drafts/static-root/`. This file is a handoff list, not legal advice. Live `northstardigi.agency` routes and GitHub Pages `privacy/` / `terms/` were not changed.

## Blocked until Chase confirms

- Public / HELP phone. Drafts still list both **(304) 484-4648** and **(304) 381-1611**. Do not pick one in git.
- Last-updated date freeze after attorney review.

## SMS / A2P language already in the drafts (keep)

- Dual consent (non-marketing vs marketing SMS).
- Reply **STOP** to unsubscribe; **HELP** for help.
- Consent is not a condition of purchase.
- Message frequency varies; message and data rates may apply.
- Mobile opt-in and SMS phone numbers are **never shared, sold, or rented** for a third party’s own marketing.
- Processors may handle data only to deliver the messaging service.

## Attorney should confirm before filing 10DLC or publishing

1. One HELP/customer-care number matches the campaign and the website.
2. Age **18+** SMS line matches the registered campaign (present in GHL terms; added in drafts).
3. Processor exception vs “never shared” matches the actual Twilio / GHL / Telnyx (or other) contracts.
4. Call recording and AI/CRM disclosures match live receptionist and recording settings.
5. Client-vs-Northstar data-control language does not weaken Northstar’s own SMS program terms.
6. `/policies` and `/ai-policy` stay off the A2P privacy/terms URLs.
7. STOP confirmation + rejoin wording matches carrier examples.
8. Canonical URLs `https://www.northstardigi.agency/privacy-policy` and `.../terms-of-service` will be the files a crawler sees **without JavaScript** after static hosting (today those paths still return the SPA homepage).

Do not publish, merge as a live-route change, or alter Cloudflare / GHL fallbacks until those items are signed off.
