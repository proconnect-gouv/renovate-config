# renovate-config

👷 Our shared renovate config

## Usage

In a repository's `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["local>proconnect-gouv/renovate-config"]
}
```

### Scalingo

Apps hosted on Scalingo also extend `scalingo`, which keeps the `postgres`
and `redis` Docker images within the versions Scalingo offers:

```json
{
  "extends": [
    "local>proconnect-gouv/renovate-config",
    "local>proconnect-gouv/renovate-config:scalingo"
  ]
}
```

When Scalingo ships a new version, raise its `allowedVersions` in
`scalingo.json`. The available versions are listed for
[PostgreSQL](https://doc.scalingo.com/databases/postgresql/about/overview#available-versions)
and [Redis](https://doc.scalingo.com/databases/redis/start#available-versions).

It also keeps the `@sentry/*` SDKs below v11: v11 requires Sentry self-hosted
26.4.2+, and our instance runs 24.8.0. Raise the cap when the instance is
upgraded (see the SDK
[migration guides](https://docs.sentry.io/platforms/javascript/migration/)).

## Development

Validate the presets:

```sh
bun install
bun run validate
```
