# Project Notes

## Build and Test

- run check with `gob run make`
- `make test` already depends on `make build`
- No need to run `make build` separately before running tests

## Release Process

- See [docs/releases.md](docs/releases.md) for the release process

## Nix

- When changing Go dependencies (`go.mod`), update the Nix flake `vendorHash`
- If the build fails, the error message contains the correct hash to use

See [docs/nix.md](docs/nix.md) for details.

## Agent guidance

- When you need to inspect jobs programmatically, append `--json` to commands like `gob await`, `list`, `runs`, `stats`, or `ports` and pipe the result through `jq`. This keeps your responses short and saves tokens because you only forward the structured values you need (exit codes, statuses, summaries, stdout, etc.).
- Reuse the same JSON response across multiple checks with different `jq` filters instead of rerunning the command with full prose output.
- Refer to the “Agent-friendly automation with JSON + jq” section in the README for examples you can copy into your workflows.

