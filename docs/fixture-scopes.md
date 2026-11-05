# Fixture scopes

`karva` accepts the four pytest scopes — `function`, `module`, `package`, `session` — in any
case. The value is trimmed and lower-cased before matching, so a plugin that hands back
`"Session"` is not rejected during discovery.

An unknown value fails with:

```
Invalid fixture scope `worker`; expected one of function, module, package, session
```

Dynamic scopes (`def scope(fixture_name, config): ...`) are still called with `config=None`;
carrying the collected config through is tracked separately.
