# Deployment

This repository needs to live either on a Forgejo instance (such as
https://codeberg.org or https://forge.fedoraproject.org) or GitHub. We need
support for our actions in `.forgejo/workflows/`.

On Forgejo, go to your project Settings > Units > Overview and make sure
"Enable integrated CI/CD pipelines with Forgejo Actions" is enabled. Then go to
Settings > Actions > Secrets and define these:

```
COPR_USERNAME
COPR_LOGIN
COPR_TOKEN
COPR_URL
FORGE_INSTANCE
FORGE_NAMESPACE
FORGE_REPO
FORGE_TOKEN
```
