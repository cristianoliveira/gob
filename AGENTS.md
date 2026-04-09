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

- Prefer `gob … --json | jq …` (await, list, runs, stats, ports) so you only emit the exact fields you need (exit code, status, stdout, etc.).
- Reuse a single JSON response with different `jq` filters rather than rerunning the command with verbose prose.
- See the README “Agent-friendly automation with JSON + jq” section for copy-paste snippets.

