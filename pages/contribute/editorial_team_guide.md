---
title: Editorial team guide
summary: Guidelines for editors managing contributions and pull requests.
---

## Working with the repository

### General workflow

* Work on feature branches, not directly on `main`
* Open pull requests for review before merging to `main`
* Small fixes (typos) can be committed directly to `main`

### File structure

* Content pages are in [`pages/`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/tree/main/pages) directory
* Sidebar navigation is in [`_data/sidebars/`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/tree/main/_data/sidebars)
* Contributors metadata is in [`_data/CONTRIBUTORS.yml`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/blob/master/_data/CONTRIBUTORS.yml)

### Markdown file naming

* Use lowercase with underscores instead of spaces
* Ensure unique filenames across the entire site
* File `example.md` renders at `https://elixir-europe-training.github.io/ELIXIR-Training-SPLASH/example`

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

### Sidebar navigation

Edit the relevant `.yml` file in [`_data/sidebars/`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/tree/main/_data/sidebars):

```yaml
- title: Level_1_title
  url: /page_name
  subitems:
    - title: Level_2_title
      url: /subpage_name
```

**Attributes:**
* `title`: Display text in sidebar
* `url`: Internal page path (e.g., `/example`)  
* `external_url`: Use for external links instead of `url`
* `subitems`: Create hierarchy levels



### Page ID

To find out what the `page_id` of an Training SPLASH page is, please check its metadata attribute `page_id` at the top of the markdown file or the [list of page IDs](website_overview).

