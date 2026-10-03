# notification-api

FastAPI service of the `notifier` system, owned by `team-beta`. Created from the wasp-idp Backstage template `python-service`.

This page lives in the service repository (`mkdocs.yml` + `docs/`) and Backstage renders it in the *Docs* tab through the `backstage.io/techdocs-ref: dir:.` annotation in `catalog-info.yaml`.

## Endpoints

| Method | Path | Response |
|---|---|---|
| GET | `/` | App name and a greeting |
| GET | `/healthz` | Liveness/readiness |

## Dependencies (catalog only)

- `notification-db` (database) — delivered notifications
- `notification-jobs` (queue) — subscribed to `greeting-events`
- `notification-reports` (bucket) — daily reports

These resources are catalog entries for documentation purposes; the service does not connect to any of them yet.

## Delivery

Every push to `main` runs the tests, publishes `ghcr.io/wasp-foundry/notification-api:<sha>` and bumps the tag in `apps/notification-api/overlays/development` of [`wasp-foundry/gitops`](https://github.com/wasp-foundry/gitops). Production is promoted with `gh workflow run promote.yaml --repo wasp-foundry/gitops -f app=notification-api`.
