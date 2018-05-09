# Developing and Releasing a Project

Eventually, we need to make changes to projects and release those changes. We have some strategies for keeping things
organized in git to assist in that endeavor.

## Branches

Our primary branch (the "trunk") for our projects is `master`, new features in a project should be developed on branches
that are forked from `master`. Generally, these branches track 1:1 to a Jira ticket.

> ### Naming
>
> In general, when you create a new branch, you should prefix the branch name with the Jira ticket ID, followed
> by a succinct description, e.g. `RC-30-update-composition-fields`. This ties the Jira ticket to the commits on the
> branch, and by extension, the PR for the branch. It also makes writing the changelog easier by identifying which
> Jira tickets comprise a changeset.
>
> Leaving out the description (e.g. a branch named `RC-30`) means that anyone else
> interested in the branch needs to go to jira and find the ticket just to find out what the changes on the branch have
> to do with. Conversely, leaving out the Jira ticket (e.g. `update-composition-fields`) means that none of our
> Bamboo, Jira, or Github branch integrations will work,
> as well as making it harder to track the changes made for a specific ticket.

When you are done developing a new feature, a PR (pull request) should be submitted from your branch back to `master`.
More on PRs and code review [here](/code-review/README.md).

For larger changes that extend beyond the scope of a single branch, it is acceptable to have a main "feature branch" off
of `master` to which PRs are submitted from smaller branches. Once the larger changes are complete, a PR from the
feature branch can be submitted to `master`.

## Releasing

When the changes to the `master` branch are ready for release, a "release branch" will be forked off of `master` using
[semantic versioning](https://semver.org/), e.g. `v1.0.0`. This release branch can then be promoted through the
deployment environments and tested at each stage, with changes being made if necessary. Changes on a release branch
can be merged back to `master` if needed.

## Live Fixes (Hotfix)

A release branch can be deployed to production for some time before a bug is discovered that needs fixing.
It can also be the case that a bug is discovered on `master` that also needs fixing in a released branch;
but, too many changes have occurred on `master` between when the release branch was deployed and now, or new
features exist in `master` that are not ready for deployment. When this is the case, a "hotfix branch" can be
forked from the release branch, the necessary changes made, and then the hotfix branch can be merged via PR
back to the release branch. If the bug changes were made on `master`, `git cherry-pick` can be used to apply those
changes to the hotfix branch.

## Branch Visualization

Using this strategy, here is an example git log:

``` text
* a1e1f5c (v1.0.0-hotfix, v1.0.0) punctuation hotfix
* 717e9cf Release 1.0.0
| * 6d3cf17 (v1.0.1) Release 1.0.1
| | * fcc7234 (H-2-feature) Step 4
| |/
| * c88b8f4 (HEAD -> master, H-1-feature) Step 3
| * 91bd123 Another step
|/
* 2196b4c Step 1
* c85b9e5 First!
```
