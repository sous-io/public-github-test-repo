# e2e-demo

A sous recipe repository. It publishes **recipes**, grouped into
**namespaces**, that other projects subscribe to.

## Layout

```
sous.repo.yaml                 what this repository publishes
sous.index.json                 the published catalog, written by sous
recipes/e2e/example/
  sous.recipe.yaml               one recipe: its version, contents and variables
  skills/                        the files that recipe contributes
```

## The three files

**`sous.repo.yaml`** declares the namespaces this repository
publishes and lists every recipe folder in it. It is hand-written, and it is the
first thing sous reads.

**`sous.recipe.yaml`** describes one recipe: which namespace it
belongs to, what version it is at, what it depends on, which of its files a
subscriber receives, and which variables it needs answered. It is hand-written
too, and its `version` field is the source of truth for versions.

**`sous.index.json`** is the catalog: every recipe, every published version,
and a content hash for each one. It is written by `sous repo release` and
committed. Do not edit it by hand.

## Adding a recipe

1. Copy `recipes/e2e/example` to a new folder under `recipes/`.
2. Edit its `sous.recipe.yaml`: set the namespace, the name, the
   version and the contents.
3. Add the new folder's path to the `recipes` list in
   `sous.repo.yaml`.
4. Open a pull request. The workflow in `.github/workflows/sous-release.yml`
   checks that everything is consistent before it can be merged.

## Publishing

Commit your recipe changes, then run `sous repo release`. It shows you what it
would publish and asks once, then raises the version of every recipe whose files
changed since the tag that last published it, regenerates `sous.index.json`,
commits both, and cuts an annotated tag for each version. Add `--push` to push
the commit and the tags, or push them yourself.

Useful ways to narrow or steer it:

```bash
sous repo release --dry-run                    # show the plan and stop
sous repo release --namespace e2e            # only this namespace
sous repo release --recipe e2e/example   # only this recipe
sous repo release --bump minor                 # a minor step instead of a patch
sous repo release --include-unchanged          # release everything in scope anyway
```

On a branch other than `main`, a release bumps and commits but cuts no tags:
tags are cut on the default branch, by the workflow in
`.github/workflows/sous-release.yml` after the merge. Pass `--tag` to cut them
anyway. Tags are shaped `namespace/recipe@version`, and a version is published
when its tag exists.

To propose a change to a repository you do not maintain, commit it and run
`sous repo submit`, which validates everything first and then opens a
pull request through your repository host's own command line tool.

## Contributing

Improvements are welcome, including new recipes. Contribution instructions in this repository are
written for agents: `CONTRIBUTING.md` says why, and `CLAUDE.md` is where an agent without the sous
core skills starts.

## Using it

In any project that has a sous config:

```bash
sous repo add <the URL of this repository>
sous subscribe e2e/example
sous build
```

Adding a repository is what trusts it, so read a repository before you add it.

## Working on it

`sous repo link` points a project at a working copy of this repository instead
of at a published version, so you can edit a recipe and rebuild without
releasing anything:

```bash
sous repo link e2e-demo /path/to/this/checkout
```

Builds say loudly when a repository is linked. Run `sous repo unlink e2e-demo`
to go back to published versions.

## License

This repository has no license yet. Until it has one, others may read it but not reuse it; add a
`LICENSE` file before publishing.
