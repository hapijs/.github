# Maintenance
This document outlines basic procedures for maintenance of issues, PRs, and releases.

## Issues and Pull Requests
Issues and pull requests are at the core of hapi's approach to documentation and messaging to the broader community.  They are rigorously labeled, associated with releases, and assigned to collaborators responsible for their resolution.  Official discussions, release notes, announcements, and community support all generally take the form of issues.  Finally, the source of truth for our changelogs are also managed through issues.

### Labels
Labels are standardized through [organization defaults](https://docs.github.com/en/github/setting-up-and-managing-organizations-and-teams/managing-default-labels-for-repositories-in-your-organization).  Here are some notable ones:
 - `support` - requests for clarification or help.
 - `bug` - reports of unintended behavior.
 - `security` - indication of security implications.
 - `feature` - requests for new functionality.
 - `release notes` - documentation of changes in major releases, sometimes accompanied by a migration guide.
 - `documentation` - non-code related changes to the README, API docs, or similar.
 - `dependency` - changes to dependencies.
 - `breaking changes` - indication of a breaking change in behavior, principally for major releases.
 - `help wanted` - signals that it's welcome for any community member to offer a PR or otherwise help to resolve the issue.

Every issue and pull request should have at least one label attributed to it.  The labels for an issue may change over time.  When a pull request addresses a particular issue, it will often have the same labels as that issue.

### The Connection to Releases
We associate PRs and issues to released versions of our modules in order to leave a paper trail for users that includes code, documentation, and discussion.  It can also be interpreted programmatically to e.g. display automatically generated changelogs on the website as can be seen [here for boom](https://hapi.dev/module/boom/changelog/).

#### Milestones
When a PR is merged or issue is closed, it should be associated with a [milestone](https://github.com/hapijs/hapi/milestones) for the version of the module in which the corresponding work will be released.  All merged PRs should be associated with a milestone, and all issues resolved by a merged PR or a commit should have a milestone.  Milestones are named by the full semver version of the release, e.g. `2.1.0`, `0.1.1`, `9.0.0`.  When the version is published, that milestone should be closed.  There should never be zero open milestones for a given module: when one milestone is closed, a new one is created for the next patch version.  For example, once `2.1.0` is released then the milestone for that version will be closed and a new milestone for `2.1.1` will be created.

This organization of issues into milestones is central to generating the module changelogs found on [hapi.dev](https://hapi.dev), and to creating transparency around what is contained in each release.

#### Release Notes
It is encouraged to create an issue with release notes for major changes, especially for modules that are intended to be used externally to the organization (e.g. hapi, bell, nes) versus hapi core (e.g. pez, topo, shot).  The [hapijs/hapi](https://github.com/hapijs/hapi) repository should have release notes for every major version of the framework.  [This](https://github.com/hapijs/hapi/issues/4017) is a great example of typical release note format and ideal level of detail.

### Assignees
The collaborator responsible for final review and merge of pull requests should mark themselves as the "assignee."  This leaves an at-a-glance paper trail primarily for convenience ("who understands the changes made in #365?"), and is in recognition of that person's involvement/contribution.  When a collaborator closes an issue that they were responsible for resolving (e.g. answered a user's support question), they may also mark themselves as the assignee.

### Closing
> _This list is not meant to indicate anything about the numerous other cases that may occur, it is meant only to offer some guidelines._

 - Support issues without any response should remain open for two weeks then may be closed.
 - If a support issue doesn't contain a sufficient reproduction it may be closed immediately with a comment.
 - Any effort at resolving a support issue makes it eligible for being closed.  It's useful to point folks to the hapi hour slack for further support.  It is welcome for discussion to continue on the closed issue.
 - Any issue that doesn't follow the relevant issue template may be closed immediately, optionally with a comment indicating to re-file the issue following the template.
 - Feature requests that will not be satisfied may be closed with comment.
 - Bugs should remain open until resolved.
 - Release notes should be staged prior to publish and closed upon publish.
 - PRs that will not be accepted may be closed with a comment.  If a PR is replaced, the new PR should be referenced in a comment.

## Releases
A release consists of 1. publishing a module to npm following [semver](https://semver.org/), and 2. an annotated tag in GitHub marking the release.  The hapi organization takes the integrity of releases very seriously.  For this reason only a small subset of maintainers have publish access, typically constrained to members of the TSC.  We additionally require publishers to utilize 2FA on both GitHub and most importantly on npm.

### Guide
When a new version of a module is ready to be published, _the releaser_ adheres to the following release process:

 - The releaser ensures the main branch of the repository has passing tests in GitHub Actions.
 - Clones the repository locally if they haven't already.
 - Navigates to the repository on their machine locally.
 - Ensures they've checked-out the main branch and `git pull`.
 - Ensures there are no changes made locally using `git status`.  There should be no modifications or untracked files.
 - Updates `version` in package.json with a new commit marked by an annotated tag using `npm version major|minor|patch`, depending on whether the version contains breaking changes, new features, or only fixes per [semver](https://semver.org/).
 - Pushes the new commit and the new tag using `git push && git push --tags`.
 - When the releaser is ready to publish to npm they run `npm publish`.  They will be utilizing 2FA so will need to have their one-time password at hand.  If the releaser happens to be publishing an older LTS version then the published version should not be tagged on npm as "latest", so a tag needs to be specified explicitly: `npm publish --tag=lts`.
 - Closes the [milestone](https://github.com/hapijs/hapi/milestones) for the released version in GitHub, and creates a new milestone for the next patch version.
 - Optionally upgrades the tag to a release in GitHub, including a summary of the changes.  One may do this by navigating to the tag found [here](https://github.com/hapijs/hapi/tags) then clicking the "Edit tag" button.  Upon save the tag should become a GitHub release.
