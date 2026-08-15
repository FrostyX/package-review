# Development

There is no code in this repository, everything is provided by
https://github.com/FrostyX/fedora-review-process-reimagined
If you have the option, clone it and run scripts directly from there.

The only reason why you might need to do any development directly within this
repository is when you need to work on our Forgejo Actions. This is how to work
with them locally.


## Secrets

Create a `.secrets` file with the following content:

```env
COPR_USERNAME=frostyx
COPR_LOGIN=...
COPR_TOKEN=...
COPR_URL=https://copr.stg.fedoraproject.org

FORGE_INSTANCE=http://localhost:5081
FORGE_NAMESPACE=...
FORGE_REPO=...
FORGE_TOKEN=...
```

## Running

I don't know how to pass event information through command-line parameters, so
we are using fake event files from `tests/data/`. Create or modify the files to
fit your use case.

We have a fake event for an opened PR:

```
act pull_request -W \
    .forgejo/workflows/build-in-copr.yml \
    -e tests/data/pr-1-open.json \
    --secret-file .secrets
```

And we also have a fake event for a force push within a PR:

```
act pull_request -W \
    .forgejo/workflows/build-in-copr.yml \
    -e tests/data/pr-1-force-push.json \
    --secret-file .secrets
```
