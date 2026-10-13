# Live follow: design note (sketch)

`-follow` keeps reading a file as it grows. The questions below decide what it may
promise a caller.

## Open questions

- What happens to a partially written last line: buffer it, skip it, or fail?
- Do we re-emit the whole report on every change, or only the new findings?
- Should a reorg that is later reversed be reported once or twice?
