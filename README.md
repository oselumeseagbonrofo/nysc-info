# NYSC Batch C 2026 — Clear Guide

Single-page, verified guide for prospective corps members. Senate list → NERD clearance → registration → call-up → camp, with no rumour.

**Live:** https://oselumeseagbonrofo.github.io/nysc-info/

Compare 3 identities on the hub (header to switch, `?v=a|b|c` deep link):
- **A — Clear Guide** (`variants/variant-a.html`) — cream/forest editorial, timeline + checklist hero
- **B — Gazette** (`variants/variant-b.html`) — federal notice, black rules + Nigeria green, perforated call-up ticket
- **C — Handbook** (`variants/variant-c.html`) — kraft field manual, punched holes + rubber stamp, pocket checklist

Direct: [/variants/variant-a.html](variants/variant-a.html) · [/variants/variant-b.html](variants/variant-b.html) · [/variants/variant-c.html](variants/variant-c.html)

## What it covers

- **Registration:** Mon 7–Sun 13 Sept 2026 (7-day fixed window, NYSC notice 28 Aug 2026)
- **NERD mandatory:** signed project (you + supervisor + HOD) uploaded at an accredited centre only (₦12k–₦15k), code required on the NYSC portal — no clearance, no registration
- **Senate list:** verify before anything else, fix mismatches at Student Affairs
- **Call-up & camp:** call-up number/letter after ICT processing, 21-day orientation (Stream 1 late Oct–mid Nov TBC, Stream 2 Nov–Dec TBC)
- Interactive checklist (persisted), statement-of-result email template (CC Sylvester Efomah), documents/packing lists, FAQ

## Stack

No build. Static HTML + Tailwind CDN + vanilla JS. Opens via `file://` or any static host. `index.html` is the hub (iframe switcher keeps styles isolated); `.nojekyll` for GitHub Pages.

## Local

```bash
open index.html
# or
python3 -m http.server 8000
# then http://localhost:8000
```

## Source

`info/transcription.md` (field steps) + NYSC notice via SmartJamb 28 Aug 2026 + `nysc.gov.ng/mobtable.html` + `portal.nysc.org.ng` + NERD lookup `esmat.ned.gov.ng/ai/lookup_nerd_digital_service_centre_eco.php`. Unofficial, for clarity. Always reconfirm on `portal.nysc.org.ng` / `nysc.gov.ng`.

## Deploy

Pushed to `main`. Pages source: `main` / `/ (root)`. Any push rebuilds `https://oselumeseagbonrofo.github.io/nysc-info/` in ~30s.
