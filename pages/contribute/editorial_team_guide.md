---
title: Editorial team guide
summary: Guidelines for editors managing contributions and pull requests.
---

## Working with the repository

### General workflow

* Work on feature branches, not directly on `main`
* Open pull requests for review before merging to `main`
* Small fixes (typos) can be committed directly to `main`

### Technical documentation

For information on file structure, sidebar navigation, and markdown file naming, see the [technical documentation](technical_documentation#website-file-structure).

### GitHub checks

Pull requests trigger automated checks:
* Website build validation
* Tool/resource table validation

PRs cannot be merged if checks fail. Click the failed check for details.

## Managing issues and pull requests

### Issues

* Monitor [open issues](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/issues) regularly
* Apply relevant labels
* Assign at least one editor to each issue
* Discuss with contributors via issue comments
* Link PRs to related issues

### Pull requests

* Editors responsible for changed files are automatically assigned
* All PRs must be assigned to at least one editor
* Review using GitHub's [review features](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests)
* Verify tags for pages, tools and resources
* The final approving editor should merge the PR
* Link PRs to issues using `closes #issue_number`, `fixes #issue_number`, or `resolves #issue_number`

Learn more: [Linking pull requests to issues](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue)

