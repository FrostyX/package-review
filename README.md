# Fedora Package Review

## Devel

Create `.secrets` with:

```env
COPR_USERNAME=frostyx
COPR_LOGIN=...
COPR_TOKEN=...
COPR_URL=https://copr.stg.fedoraproject.org

FORGE_INSTANCE=http://localhost:5081
FORGE_TOKEN=...
```

Run the action locally:

```
act pull_request -W \
    .forgejo/workflows/build-in-copr.yml \
    -e tests/data/pr-1-open.json \
    --secret-file .secrets

act pull_request -W \
    .forgejo/workflows/build-in-copr.yml \
    -e tests/data/pr-1-force-push.json \
    --secret-file .secrets
```
