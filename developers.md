---
layout: page
title: For developers
---

This note has some information about the way git branches are used which will be useful to all developers that
contribute. There are also some hints to try and avoid ballsing up the release process that will mainly be of interest
to maintainers.

## Git branches

The `master` branch is the public-facing stable branch. It should always be in a sensible state, ideally sitting at a
release tag.

The `develop` branch is the main line of development. Features should be merged in to this branch, and pull-requests
should be based on this branch. It's ok to fix small bugs and the like on this branch, but anything larger should happen
on ...

The `feature/*` branches are for features. Ideally they will have meaningful names!

If you're messing around with an idea, maybe an `experiment/*` branch would be appropriate.

An attempt is made to keep the branches in the repository clean, so merged feature branches will be deleted, and old,
unmerged branches that will definitely no longer be used should also be deleted.

## To start a new release

- Make sure you're working on the develop branch.
- Change the version numbers to a SNAPSHOT version in:
  - project.clj of gorilla-repl.
  - project.clj of lein-gorilla (two places).
  - dependency injection code in core namespace of lein-gorilla.

## To publish a release

- Update the version number to suitable release number, following the steps above.
- Once you're happy merge into master.
- Tag the release in git/on github.
- Make sure you're on master! (Both repos).
- `lein deploy clojars`, first gorilla-repl and then lein-gorilla, and promote.
- Switch back to develop before you forget. (Both repos).
- Update the version in start.md of gorilla-repl.org (three places).
