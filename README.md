# mta-sts.stoicera.com

MTA-STS policy for stoicera.com (RFC 8461), served by GitHub Pages at
https://mta-sts.stoicera.com/.well-known/mta-sts.txt

Serves the mail-security baseline (Fundament, operations). Change procedure:

1. Before an MX change: add the new MX hosts here, keep the old ones, push.
2. Bump the `id` in the DNS TXT record `_mta-sts.stoicera.com` (format `YYYYMMDDHHMM`).
3. After the MX change has settled for one `max_age`: remove the old MX hosts, bump `id` again.
4. Move `mode: testing` → `enforce` only after TLS-RPT reports (`_smtp._tls.stoicera.com`) are clean for two weeks.

State 2026-10-27: `mode: enforce`, only MX `www665.your-server.de` (Hetzner Webhosting S), `max_age: 604800` (7 days).
Hostinger MX removed (Hostinger mail for stoicera.com ends 2026-10-31). Basis: Google TLS-RPT 2026-10-10 to 2026-10-26,
15 daily reports, 60 sessions, 0 failures. In enforce mode step 1 is mandatory: a new MX host must be in this file
(and the `id` bumped) at least one `max_age` before it receives mail, otherwise MTA-STS senders refuse delivery.
