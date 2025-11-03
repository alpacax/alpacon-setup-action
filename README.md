

# Alpacon Setup Action

This GitHub Action installs the Alpacon CLI in your workflow environment.

- Official Docs: [Alpacon CLI Guide](https://docs.alpacax.com/alpacon/cli)

## Features

- Installs Alpacon CLI automatically in your workflow
- Skips installation if CLI is already present

## Usage examples

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Setup Alpacon CLI
        uses: alpacax/alpacon-setup-action@v1

      - name: Use other Alpacon actions
        uses: alpacax/alpacon-cp-action@v1
        with:
          workspace-url: ${{ secrets.ALPACON_WORKSPACE_URL }}
          api-token: ${{ secrets.ALPACON_API_TOKEN }}
          # ... other inputs
```

## Inputs

This action requires no inputs.

## Notes

- This action only installs the Alpacon CLI
- Use this as the first step before other Alpacon actions (cp, websh, common)
- Other Alpacon actions will handle authentication automatically
- [Alpacon CLI Getting Started](https://docs.alpacax.com/alpacon/cli/getting-started)