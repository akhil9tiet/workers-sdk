---
"wrangler": patch
---

Retry bodyless CORS preflight (`OPTIONS`) requests in `wrangler dev` when they hit a dropped internal connection, the same way `GET`/`HEAD` requests are already retried. Fixes cloudflare/workers-sdk#16216.
