# cc-edge-macos-firewall-io

Cribl Edge pack for macOS Application Firewall log events.

## Installation

Import the pack's `.crbl` release asset into Cribl Edge as a pack.

## Usage

Sources attach to the pipeline by its ID, `firewall_logs`. The route in
`default/pipelines/route.yml` matches events whose `datatype` is
`macos-firewall` and sends them to the same pipeline.

## Pipelines

- `firewall_logs` sets `index` to `firewall` and `sourcetype` to
  `macos:firewall` on every event.

## Layout

- `default/pipelines/firewall_logs/conf.yml`: the pipeline.
- `default/pipelines/route.yml`: the route to that pipeline.
- `tests/fixtures/firewall_logs/`: two synthetic log lines and their
  expected output.
- `data/samples/firewall_logs.json`: the same two lines for the UI sample
  preview.

## Testing

```sh
cd tests
pnpm install --frozen-lockfile
pnpm run lint
pnpm run typecheck
pnpm run test
```

`pnpm run test` needs a reachable Cribl Edge API, configured with the
`CRIBL_HOST`, `CRIBL_PORT`, `CRIBL_USER`, and `CRIBL_PASS` environment
variables. The tarball-parity and harness meta-tests need no instance.
