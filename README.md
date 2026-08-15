# Fedora Package Review

In order for a new package to be added to Fedora, the package must first
undertake a formal review. The process is known as the
[Fedora Package Review Process][review-process].

This repository provides an alternative way of proposing new packages. The ideas
are explored in the [Fedora Package Review Process reimagined][blogpost]
blogpost.


## Proposing a new package

Do you want to add a new package into the official Fedora repositories? Follow
these steps:

- Fork this repository
- Clone the forked repository
- Create a new branch. The name is up to you.
- Create a new directory with the same name as your package, e.g. `hello`
- Put your specfile into that directory, e.g. `hello/hello.spec`
- Commit everything, push, and create a PR
- Make sure CI is passing
- Wait for a review from a fellow package maintainer and their approval
- Once accepted, the package will be automatically imported to the
  [Fedora DistGit][distgit]


## Additional sources

If possible, specify the `Source` fields in your specfile as fully qualified
URLs. That can usually be done for all sources provided by the upstream
project. Such sources will be automatically downloaded during the build.

Downstream sources, such as `.patch` files, `.sig` files, etc can be placed next
to the specfile and committed to this repository. If we have `hello/hello.spec`,
then a `hello/001-fix-broken-thing.path` will be available during the build.

Some languages and ecosystems need vendored sources that are generated on the
fly. As an example, we can take the `gh` package written in Go. In such a case,
we would create `gh/gh.spec` and put a `gh/generate-sources.sh` script with the
following content next to it:

```bash
#!/bin/sh
spectool -g gh.spec
go_vendor_archive create gh.spec
```

The vendored archive will be generated before attempting to build the package.


## Multiple packages within one PR

Multiple packages can be submitted within one PR. Just create multiple
directories with specfiles, e.g. `foo/foo.spec`, `bar/bar.spec`, and
`baz/baz.spec`.

If they are all added in one commit, they will be built in parallel (not
implemented yet). If they are added in a series of commits, they will be built
one after each other. This is useful when packaging software and its
dependencies.


## Contribute

If you want to improve the Package Review Process, see
[Development](docs/development.md) and [Deployment](docs/deployment.md)
documentation.


[review-process]: https://docs.fedoraproject.org/en-US/package-maintainers/Package_Review_Process/
[blogpost]: https://frostyx.cz/posts/fedora-package-review-process-reimagined
[distgit]: https://src.fedoraproject.org/
