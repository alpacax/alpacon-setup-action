# Alpacon Setup Action

This GitHub Action installs the Alpacon CLI in your workflow environment.

- Official Docs: [Alpacon CLI Guide](https://docs.alpacax.com/alpacon/cli)

## Features

- Installs Alpacon CLI automatically in your workflow
- Skips installation if CLI is already present

## Supported runners

- `ubuntu-latest` (and other Ubuntu-based runners)

## Usage examples

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Setup Alpacon CLI
        uses: alpacax/alpacon-setup-action@v1.1.0

      - name: Use other Alpacon actions
        uses: alpacax/alpacon-cp-action@v1.2.0
        with:
          workspace-url: ${{ secrets.ALPACON_WORKSPACE_URL }}
          api-token: ${{ secrets.ALPACON_API_TOKEN }}
          # ... other inputs
```

## Inputs

This action requires no inputs.

## Troubleshooting

| Problem | Cause | Fix |
|---------|-------|-----|
| `alpacon: command not found` | Installation failed or PATH issue | Check runner is Ubuntu-based; re-run the workflow |
| `apt-get` errors | Network or repository issue | Check GitHub Actions runner has internet access |
| Action passes but CLI missing | Step ordering issue | Ensure setup action runs before other Alpacon actions |

## Related actions

- [alpacon-common-action](https://github.com/alpacax/alpacon-common-action) — Run any Alpacon CLI command
- [alpacon-cp-action](https://github.com/alpacax/alpacon-cp-action) — Copy files to/from remote servers
- [alpacon-websh-action](https://github.com/alpacax/alpacon-websh-action) — Execute shell commands on remote servers

## Notes

- This action only installs the Alpacon CLI
- Use this as the first step before other Alpacon actions (cp, websh, common)
- Other Alpacon actions will handle authentication automatically
- [Alpacon CLI Getting Started](https://docs.alpacax.com/alpacon/cli/getting-started)
