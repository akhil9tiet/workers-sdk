---
"wrangler": patch
---

Fix `rewriteUrlInHeaderValue` rewriting `https://` URLs in response headers to `http://`

`wrangler dev`'s header URL rewrite now compares URL origins (scheme, host and port) instead of just the host when deciding which absolute URLs to rewrite. This leaves URLs whose scheme differs from the request's untouched, fixing mangled `Location`/`WWW-Authenticate` headers when running behind a TLS-terminating proxy such as a Cloudflare Tunnel.
