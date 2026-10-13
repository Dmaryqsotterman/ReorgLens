# ReorgLens

> Watch a chain for reorganisations and say, in one report, exactly which blocks
> were replaced and which transactions moved.

ReorgLens reads a JSONL stream of block headers and transactions, follows the
heaviest chain, and writes a report whenever a reorg is detected. It is a small, dependency-free Go
tool built for operators who want a second opinion on what a
node actually did.

## Install

```sh
go install github.com/Dmaryqsotterman/reorglens/cmd/reorglens@latest
```

Or build from a checkout:

```sh
git clone https://github.com/Dmaryqsotterman/reorglens
cd reorglens
go build ./cmd/reorglens
```

## Usage

```sh
# analyse a recorded stream
reorglens -input samples/reorged.jsonl

# follow a file as it is appended
reorglens -input live.jsonl -follow

# machine-readable output
reorglens -input samples/reorged.jsonl -format json
```

## What a report contains

| Field | Meaning |
|---|---|
| `height` | height at which the two chains diverge |
| `depth` | how many blocks were replaced |
| `orphaned` | transactions present only on the abandoned branch |
| `adopted` | transactions present only on the new branch |
| `common` | transactions both branches share |

## Behaviour on bad input

A malformed line does not stop the run. The parser reports the line number, the
reason and skips it, then keeps going, so a truncated or hand-edited capture
still produces a usable report. Samples for each case live in `samples/`.

## License

MIT - see `LICENSE`.
