# mta-sts.stoicera.com

MTA-STS policy for stoicera.com (RFC 8461), served by GitHub Pages at
https://mta-sts.stoicera.com/.well-known/mta-sts.txt

Serves the mail-security baseline (Fundament, operations). Change procedure:

1. Before an MX change: add the new MX hosts here, keep the old ones, push.
2. Bump the `id` in the DNS TXT record `_mta-sts.stoicera.com` (format `YYYYMMDDHHMM`).
3. After the MX change has settled for one `max_age`: remove the old MX hosts, bump `id` again.
4. Move `mode: testing` → `enforce` only after TLS-RPT reports (`_smtp._tls.stoicera.com`) are clean for two weeks.
