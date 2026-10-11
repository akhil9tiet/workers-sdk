---
"miniflare": patch
---

Fix `dispatchFetch()` failing with `ECONNRESET` after a Worker ignores a streamed request body

`DispatchFetchDispatcher` reused keep-alive connections for every request, including requests with bodies. If the Worker responded without consuming a streamed request body, the connection was returned to the pool with unread body bytes pending, and the server reset it — so the next `dispatchFetch()` failed with `ECONNRESET`. Connections are now only reused for bodyless requests; requests with a body close the connection after the request, restoring the pre-`#15781` behavior for that case while keeping the ephemeral-port optimization for `GET`/`HEAD`.
