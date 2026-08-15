# factorio-server

Configuration for the Factorio game server.

## Setup

Enable the pre-commit secret scan after you clone the repo:

```sh
git config core.hooksPath .githooks
```

The hook runs gitleaks on the staged changes. The devenv shell of the
parent repo (`vanillauys`) supplies the gitleaks binary.

## Secrets

Do not commit secrets. Keep secret values in 1Password. Use `.env`
files for local values - git ignores them.
