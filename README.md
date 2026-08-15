# factorio-server

Docker compose stack for the Factorio game server on Dokploy.

Two services share one `factorio-data` volume:

- `factorio` - the game server, published on UDP 34197.
- `files` - dufs, a web file manager for the volume (saves, mods,
  config), served at `https://factorio.vanillauys.com` through Traefik.
  Login: `admin` / the `FILES_PASSWORD` value from the Dokploy
  Environment tab. Container port 5000.

Players connect to `factorio.vanillauys.com` (UDP 34197). The DNS
record must stay DNS-only (grey cloud): the Cloudflare proxy does not
carry game UDP traffic.

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
