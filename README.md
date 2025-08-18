

# Alpacon Setup Action

This GitHub Action installs and authenticates the Alpacon CLI in your AlpacaX workspace.

- Official Docs: [Alpacon CLI Guide](https://docs.alpacax.com/alpacon/cli)

## Features

- Installs and logs in to Alpacon CLI automatically in your workflow

## Usage Example (workflow)

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Setup and Login to Alpacon
        uses: sangyeong01/alpacon-setup-action@v1
        with:
          workspace-url: ${{ secrets.ALPACON_WORKSPACE_URL }}
```

## Inputs

| Name           | Description                                 | Required |
|----------------|---------------------------------------------|----------|
| workspace-url  | AlpacaX workspace URL.                      | Yes      |

## Notes

- This action only installs and logs in to the CLI. Use cp/websh actions for further steps.
- [Alpacon CLI Getting Started](https://docs.alpacax.com/alpacon/cli/getting-started)

      - name: Install Alpacon CLI
        id: setup
        uses: your-username/alpacon-setup-action@v1

      - name: Check Alpacon version
        run: alpacon version

## License
This project is licensed under the MIT License.