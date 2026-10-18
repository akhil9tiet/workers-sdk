---
"@cloudflare/vite-plugin": patch
---

Fix an opaque `SyntaxError` in dev mode when a module error carries non-serializable fields (e.g. a circular reference): the invoke handler now reduces such errors to their serializable parts (`name`, `message`, `stack`, `cause`) so the worker receives the original error instead of an unparseable body.
