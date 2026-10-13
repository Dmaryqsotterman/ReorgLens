# Report schema, version 1 (sketch)

A proposal for discussion. The text report is the one people read; this is the one
tools consume, and it has to stay stable once anyone depends on it.

## Shape

```json
{
  "tool": "reorglens",
  "version": 1,
  "window": { "from": 19000110, "to": 19000114 },
  "counts": { "records": 4, "invalid": 0, "outside": 19 },
  "findings": [
    { "class": "missing", "severity": "warn", "number": 19000113 }
  ],
  "result": "findings present",
  "exitCode": 1
}
```

## Rules the schema would fix

1. `version` is an integer and only ever increases. A consumer checks it and stops
   if it is newer than what it understands, rather than guessing.
2. `class` values are exactly the set `reorglens explain` prints. That command is
   the source of truth, and the schema references it instead of copying the list.
3. `exitCode` repeats what the process returned, so a report archived from CI
   carries its own verdict without anyone having to remember the run.

## Open questions

- Do findings need a stable `id`, or is `class` + `number` enough to deduplicate a
  report against the next one?
- Should `window` echo the flags as given, or the range actually analysed when the
  capture does not cover it?
- Is `counts` worth keeping, given it is derivable from `findings`? It is cheap and
  it saves a consumer from re-deriving the accounting, but it is also a second
  source of truth.
