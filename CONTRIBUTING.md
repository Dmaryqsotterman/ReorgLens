# Contributing

Thanks for looking. A few things that make a change easy to take:

1. Open an issue first for anything larger than a bug fix, so we agree on the shape.
2. Keep the change focused - one behaviour per pull request.
3. Run `go vet ./...`, `go build ./...` and `go test ./...` before opening the PR.
4. Add a test for the behaviour you changed. The parser and the report writer both
   have table tests to copy from.
5. Run `gofmt -l .` and fix anything it reports; CI is strict about it.
5. Match the surrounding style; the codebase is deliberately small and flat.
