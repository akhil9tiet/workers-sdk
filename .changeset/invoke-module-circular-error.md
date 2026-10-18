---
"@cloudflare/vite-plugin": patch
---

Fix `__VITE_INVOKE_MODULE__` returning an unparseable 500 response when a module error carries non-serializable (e.g. circular) fields: the payload is reduced to its serializable `name`/`message`/`stack`/`cause` parts so the module runner surfaces the real error instead of a JSON `SyntaxError` (cloudflare/workers-sdk#16339)
