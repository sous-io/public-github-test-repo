---
name: example-skill
description: >-
  Replace this with the sentence that tells an agent when to load the skill.
  Say what the skill covers and name the situations that should trigger it.
---

# Example skill

This file is a placeholder written by 'sous repo init'. Replace it with a real
skill, or delete it once the example recipe has content of its own.

A skill is ordinary markdown. Everything under this recipe's 'contents' entry is
compiled into a subscribing project's agent skill directory, so what you write
here is what an agent reads there. The '.tpl.' in this file's name means it is
rendered as a LiquidJS template on the way, and the name it is written under
drops the '.tpl.'.

## What to put here

Describe the concept the skill covers, then the rules an agent should follow
when it applies. Keep it short enough to be read in full, and point at reference
files for anything long.

## Source for this Skill

This skill comes from the `e2e/example` recipe, installed by sous from a recipe
repository. It was compiled from a template, so edit the source, never this output file.

- Source Path: {{ sousTemplatePath }}
