# e2e-demo

This is a sous recipe repository. It publishes recipes: versioned bundles of agent skills, memories
and partials that sous installs into the projects that subscribe to them.

## Recipe Repositories Are Part of Sous

Writing a recipe, raising its version, checking a change, proposing it and releasing it all work
here exactly as they do in any other sous recipe repository. How a recipe repository works is part
of sous itself, so the sous core skills teach it, and they are the official source of truth for it.
This file does not repeat them. The agent MUST read these before changing anything here:

- `about-sous-repos`: a recipe repository as a whole; the repo manifest, namespaces, the index,
  release tags, what happens to a pull request and a merge, and proposing a change.
- `about-sous-recipes`: one recipe; its manifest, how its version is raised, its variables, its
  contents, its dependencies and its partials.
- `about-agent-skills`: how a skill is written, including the rules every new skill follows.

An agent in a project that uses sous already has these skills. An agent that cannot install sous or
use it reads them directly, as plain markdown files, online, at their latest published version:

- https://github.com/sous-io/sous-recipes/tree/main/recipes/core/sous-skills/skills

## Where This Repository Came From

`sous repo init` created this repository, modeled on `sous-io/sous-recipes`, the official recipe
repository. Its files show a complete repository in use:

- https://github.com/sous-io/sous-recipes
