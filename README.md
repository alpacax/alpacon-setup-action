# Alpacon Setup Action

[![GitHub marketplace](https://img.shields.io/badge/marketplace-setup--alpacon--cli-blue?logo=github)](https://github.com/marketplace/actions/setup-alpacon-cli)

Install the [Alpacon](https://alpacon.io) CLI in your GitHub Actions workflow — the first step for automating server management directly from CI/CD.

- [Official documentation](https://docs.alpacax.com/reference/actions/setup/)

## Why use this action?

- **Zero SSH keys** — Authenticate with API tokens instead of managing SSH keys across repos and servers
- **One-line setup** — A single step installs the CLI; no manual downloads or version pinning needed
- **Idempotent** — Skips installation if the CLI is already present, keeping workflows fast

## Usage

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Alpacon CLI
        uses: alpacax/alpacon-setup-action@v1

      - name: Deploy application
        uses: alpacax/alpacon-websh-action@v1
        with:
          workspace-url: ${{ secrets.ALPACON_WORKSPACE_URL }}
          api-token: ${{ secrets.ALPACON_API_TOKEN }}
          target: 'prod-server'
          script: |
            cd /opt/myapp
            git pull
            npm install
            pm2 restart app
```

## Inputs

This action requires no inputs.

## Supported runners

- `ubuntu-latest` (and other Ubuntu-based runners)

## Troubleshooting

| Problem | Cause | Fix |
|---------|-------|-----|
| `alpacon: command not found` | Installation failed or PATH issue | Check runner is Ubuntu-based; re-run the workflow |
| `apt-get` errors | Network or repository issue | Check GitHub Actions runner has internet access |
| Action passes but CLI missing | Step ordering issue | Ensure setup action runs before other Alpacon actions |

## Related actions

- [alpacon-websh-action](https://github.com/alpacax/alpacon-websh-action) — Execute shell commands on remote servers
- [alpacon-cp-action](https://github.com/alpacax/alpacon-cp-action) — Copy files to/from remote servers
- [alpacon-common-action](https://github.com/alpacax/alpacon-common-action) — Run any Alpacon CLI command

## Resources

- [GitHub Actions integration guide](https://docs.alpacax.com/integrate/github-actions/)
- [Alpacon CLI reference](https://docs.alpacax.com/reference/cli/)

## Releasing

When creating a new release, always update the `v1` major version tag:

```bash
git tag -f v1 v1.x.0
git push origin v1 --force
```

This ensures users referencing `@v1` automatically get the latest release.
