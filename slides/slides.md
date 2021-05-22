---
title: Creating a GitHub Action
theme: league
revealOptions:
    transition: 'slide'
---

<!-- markdownlint-disable-file no-trailing-punctuation no-inline-html -->

## Creating a GitHub Action

Xavier Alvarez

28/05/2021

<img class="plain" src="img/qr-repo.png"/>

[https://github.com/xalvarez/creating-a-github-action-workshop][1]

[1]: https://github.com/xalvarez/creating-a-github-action-workshop

---

## Agenda

* Use case
* Implementation
* Interesting resources

Note:

* Implementation: we see how far we get. Goal is that you finish the workshop understanding
how to create your own Action. We should have enough time.

---

# Use case

---

## Prevent file change

* Fail PRs containing matching files
* Use GitHub API to inspect PR

---

## Example: Prevent file change (solution)

```yml
name: Static analysis

on:
  pull_request:
    branches:
      - main

jobs:
  prevent-file-change:
    runs-on: ubuntu-latest
    steps:
      - name: Check-out git branch
        uses: actions/checkout@v2.3.4
      - name: Prevent 'example' files from being modified
        uses: xalvarez/prevent-file-change-action@v1.0.0
        with:
          githubToken: ${{ secrets.GITHUB_TOKEN }}
          pattern: .*example
```

Note:

* Assume everyone has written a workflow. Quickly go through the example.

---

# Implementation

---

## Types of Actions

* **Javascript Actions**
* Docker container Actions
* Composite run steps Actions

More info: [https://docs.github.com/en/actions/creating-actions][1]

[1]: https://docs.github.com/en/actions/creating-actions

Note:

* We have different ways to implement an Action. I decided to write a JS Action using TS.

---

## GitHub Templates

* **[https://github.com/actions/typescript-action][1]**
* [https://github.com/actions/javascript-action][2]

[1]: https://github.com/actions/typescript-action
[2]: https://github.com/actions/javascript-action

Note:

* For our use case we've got two templates which come in handy.
* Use template to create a TS Action.

---

## GitHub Actions Toolkit

[https://github.com/actions/toolkit][1]

[1]: https://github.com/actions/toolkit

Note:

Most interesting packages:

* @actions/core
* @actions/github
* @actions/cache

---

## Live Coding

Note:

Show template:

* This Action implements a sleep
* action.yml
* ESLint, Prettier, etc. configurations are already included
* Workflow to test local Action
* package.json
* main.ts and wait.ts

Implementation:

* Write action.yml: [https://docs.github.com/en/actions/creating-actions/metadata-syntax-for-github-actions][1]
* Install @actions/github


[1]: https://docs.github.com/en/actions/creating-actions/metadata-syntax-for-github-actions

---

## Before you go...

* [https://github.com/xalvarez/creating-a-github-action-workshop][1]
* [https://github.com/xalvarez/prevent-file-change-action][2]
* [https://github.com/actions][3]

[1]: https://github.com/xalvarez/creating-a-github-action-workshop
[2]: https://github.com/xalvarez/prevent-file-change-action
[3]: https://github.com/actions
