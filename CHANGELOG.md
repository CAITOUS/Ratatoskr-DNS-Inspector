# Changelog

## 1.1.0 — 2026-11-04

Nordic theme, light and dark modes, accessibility.

- New look shared across the CAITO tool suite: an airy Nordic palette with its own accent and icon (also the browser tab icon)
- **Light / dark toggle** in the header. It follows your device until you choose, then remembers your choice across all the tools
- Inter font (SIL Open Font License) is now built into the file, so the app makes no font requests and looks the same everywhere
- Accessibility: every control has a label, all text meets WCAG AA contrast in both modes, and keyboard focus is clearly visible
- The old theme button is replaced by the shared toggle, and the squirrel emoji by the new icon.

## 1.0.0 — 2026-11-03

First public release.

- SPF, DKIM and DMARC checks with a 100-point grade, prioritised findings, fixes and suggested records
- SPF include-tree expansion with lookup and void-lookup counting, sender detection and platform cross-checks
- DKIM discovery across ~60 common selectors plus custom selectors; key size, test mode, revoked and dangling-CNAME detection
- DMARC tag validation, `pct` handling (pct=0 = monitoring only), subdomain/inherited policies, external report authorisation
- Mail transport: MX health and provider, null MX, MTA-STS, TLS-RPT, BIMI, Microsoft 365 client records, SaaS verification footprint
- Hosting: DNS provider, SOA, DNSSEC, CAA, RDAP registration/expiry/lock, proxy/CDN/WAF detection, subdomain sweep, origin exposure, internal IPs in public DNS
- Speed: browser HTTPS timing with history; regional ping/HTTPS tests via Globalping with saved default locations and history
- Batch checks with summary table and CSV export; Markdown, JSON, zone-text and print exports
- Privacy guard: blocklist for IPs/ranges/hosts; private ranges never leave the browser; CSV formula-injection protection
- Explain mode: toggleable hover tooltips for settings, metrics and findings
- Clear / reset, light/dark theme, version check against a public `ratatoskr.json`
