# Security & data handling

## What Ratatoskr talks to

| Destination | When | What is sent |
|---|---|---|
| `dns.google` or `cloudflare-dns.com` | Every check | DNS names being looked up (domain, subdomains, selectors, reverse lookups) |
| `rdap.org` (and the registry it redirects to) | If **Registrar / expiry** is on | The registrable domain |
| The target website | If **Connection timing** is on | Five plain HTTPS requests for `/favicon.ico`, from your IP |
| `api.globalping.io` | Only if regional tests run | Target hostname, extra targets, your location list, and your token if you set one |
| `ratatoskr.json` on GitHub | On open, offline copies only | A plain request; no credentials or cookies |

There is no Ratatoskr server, telemetry or analytics. Nothing is uploaded except the lookups above.

## What third parties can see

- **DNS resolvers** see which names you look up.
- **Globalping** probes are run by volunteers. A probe operator sees the target being tested, and results can be fetched by anyone with the measurement ID. Don't send confidential targets there.
- **Targets** of regional tests see traffic from probe IPs, not yours. The browser timing test comes from your own IP, like a normal visit.

## Privacy guard

- Private and reserved ranges (10/8, 172.16/12, 192.168/16, 100.64/10, loopback, link-local, IPv6 ULA…) are never sent to any outside service, including reverse lookups.
- Your blocklist (IPs, CIDR ranges, hostnames + subdomains) is enforced for DNS, RDAP, Globalping and browser timing.
- Raw IPs are kept away from Globalping by default.
- Everything withheld is listed in Findings and the Query log.

## What stays in the browser

Domain list, options, privacy blocklist, regional locations, the optional Globalping token, and speed history are kept in this browser's local storage, unencrypted. In some browsers, other HTML files opened from disk can read storage of `file://` pages. Use **Clear / reset** on shared computers, or use the hosted version.

## Handling of returned data

- All DNS and probe text is HTML-escaped before display; raw probe output is never rendered.
- CSV exports neutralise spreadsheet formula injection (`=`, `+`, `-`, `@`).
- Results from volunteer probes and public resolvers are indicative, not proof. Confirm critical measurements from more than one probe.

## Reporting

Please report security issues privately to the repository owner rather than in a public issue.
