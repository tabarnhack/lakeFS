---
layout: default
title: Contributing
description: lakeFS community welcomes your contribution. To make the process as seamless as possible, we recommend you read this contribution guide.
nav_order: 55
has_children: false
---

# Contributing to lakeFS

Thank you for your interest in contributing to our project. Whether it's a bug report, new feature, correction, or additional documentation, we greatly value feedback and contributions from our community.

Please read through this document before submitting any issues or pull requests to ensure we have all the necessary information to effectively respond to your bug report or contribution.

Don't know where to start? Reach out on the #dev channel on [our Slack](https://lakefs.io/slack) and we will help you get started. We also recommend this [free series](https://app.egghead.io/playlists/how-to-contribute-to-an-open-source-project-on-github){:target="_blank"} about contributing to OSS projects.
{: .note .note-info }

## Getting Started

Before you get started, we ask that you:

* Check out the [code of conduct](https://github.com/treeverse/lakeFS/blob/master/CODE_OF_CONDUCT.md).
* Sign the [lakeFS CLA](https://cla-assistant.io/treeverse/lakeFS) when making your first pull request (individual / corporate)
* Submit any security issues directly to [security@treeverse.io](mailto:security@treeverse.io).
* Contributions should have an associated [GitHub issue](https://github.com/treeverse/lakeFS/issues/). 
* Before making major contributions, please reach out to us on the #dev channel on [Slack](https://lakefs.io/slack).
  We will make sure no one else is working on the same feature. 

## Setting up an Environment

*This section was tested on macOS and Linux (Fedora 32, Ubuntu 20.04) - Your mileage may vary*


Our [Go release workflow](https://github.com/treeverse/lakeFS/blob/master/.github/workflows/goreleaser.yaml) holds the Go and Node.js versions we currently use under _go-version_ and _node-version_ compatibly.  The Java workflows use [Maven 3.8.1](https://github.com/actions/virtual-environments/blob/main/images/linux/Ubuntu2004-README.md) (but any recent version of Maven should work).

1. Install the required dependencies for your OS:
   1. [Git](https://git-scm.com/downloads)
   1. [GNU make](https://www.gnu.org/software/make/) (probably best to install from your OS package manager such as apt or brew)
   1. [Docker](https://docs.docker.com/get-docker/)
   1. [Go](https://golang.org/doc/install)
   1. [Node.js & npm](https://www.npmjs.com/get-npm)
   1. [Maven](https://maven.apache.org/) to build and test Spark client codes.
   1. *Optional* - [PostgreSQL 11](https://www.postgresql.org/docs/11/tutorial-install.html) (useful for running and debugging locally)

1. Install statik:

   ```shell
   go get github.com/rakyll/statik
   ```

   Make sure `(go env GOPATH)/bin` is in your `$PATH` (or at least, that the `statik` binary is).

1. Clone the repository from https://github.com/treeverse/lakeFS (gives you read-only access to the repository. To contribute, see the next section).
1. Build the project:

   ```shell
   make build
   ```

1. Make sure tests are passing:

   ```shell
   make test
   ```

## Before creating a pull request

1. Review this document in full
1. Make sure there's an open issue on GitHub that this pull request addresses, and that it isn't labeled `x/wontfix`
1. Fork the [lakeFS repository](https://github.com/treeverse/lakeFS)
1. If you're adding new functionality, create a new branch named `feature/<DESCRIPTIVE NAME>`
1. If you're fixing a bug, create a new branch named `fix/<DESCRIPTIVE NAME>-<ISSUE NUMBER>`

## Testing your change

Once you've made the necessary changes to the code, make sure tests pass:

```shell
make test
```

Check linting rules are passing:

```shell
make checks-validator
```

lakeFS uses [go fmt](https://golang.org/cmd/gofmt/) as a style guide for Go code.

## Submitting a pull request

Open a GitHub pull request with your change. The PR description should include a brief explanation of your change.
You should also mention the related GitHub issue. If the issue should be automatically closed after the merge, please [link it to the PR](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword).

After submitting your pull request, [GitHub Actions](https://github.com/treeverse/lakeFS/actions) will automatically run tests on your changes and make sure that your updated code builds and runs on Go 1.16.2.

Check back shortly after submitting your pull request to make sure that your code passes these checks. If any of the checks come back with a red X, then do your best to address the errors.

A developer from our team will review your pull request, and may request some changes to it. After the request is approved, it will be merged to our main branch.

## Documentation

Documentation of features and changes in behaviour should be included in the pull-request.
You can create separate pull requests for documentation changes only.
Documentation site customizations should be performed in accordance with the [Just The Docs Customization](https://pmarsceill.github.io/just-the-docs/docs/customization/) guide, which is applied during the site creation process.

### CHANGELOG.md

Any user-facing change should be included in the `CHANGELOG.md` file, under the "Unreleased" section at the top.
When we publish a new version of lakeFS, we will move this to the relevant version section.
The changelog entry should contain a concise description of the feature or fix, along with the GitHub issue number.
