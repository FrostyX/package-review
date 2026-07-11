# Fedora Package Review

## Devel

Create `.secrets` with:

```env
COPR_USERNAME=frostyx
COPR_LOGIN=...
COPR_TOKEN=...
COPR_URL=https://copr.stg.fedoraproject.org

FORGEJO_INSTANCE=http://localhost:5081
FORGEJO_TOKEN=...
```

Run the action locally:

```
act pull_request -W \
    .forgejo/workflows/build-in-copr.yml \
    -e tests/data/pr-1.json \
    --secret-file .secrets
```
