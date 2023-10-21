# Contributing to `hello-rs`

`hello-rs` is open source software. Whether you are a seasoned open source contributor or a first-time committer, we welcome and encourage you to contribute code, documentation, ideas, or problem statements to this project.

- [Contributing to `hello-rs`](#contributing-to-hello-rs)
  - [About this document](#about-this-document)
  - [Getting the code](#getting-the-code)
    - [Installing git](#installing-git)
    - [External contributors](#external-contributors)
  - [Setting up an environment](#setting-up-an-environment)
    - [Tools](#tools)
  - [Testing](#testing)
  - [Submitting a Pull Request](#submitting-a-pull-request)

## About this document

There are many ways to contribute to the ongoing development of `hello-rs`, such as by participating in discussions and issues.

The rest of this document serves as a more granular guide for contributing code changes to `hello-rs` (this repository). It is not intended as a guide for using `hello-rs`, and some pieces assume a level of familiarity with Rust development with `cargo`. Specific code snippets in this guide assume you are using macOS or Linux and are comfortable with the command line.

- **Branches:** All pull requests from community contributors should target the `main` branch (default). If the change is needed as a patch for a minor version of dbt that has already been released (or is already a release candidate), a maintainer will backport the changes in your PR to the relevant "latest" release branch (`1.0.<latest>`, `1.1.<latest>`, ...). If an issue fix applies to a release branch, that fix should be first committed to the development branch and then to the release branch (rarely release-branch fixes may not apply to `main`).
- **Releases**: Before releasing a new minor version, we prepare a series of beta release candidates to allow users to test the new version in live environments. This is an important quality assurance step, as it exposes the new code to a wide variety of complicated deployments and can surface bugs before official release. Releases are accessible via pip.

## Getting the code

### Installing git

You will need `git` in order to download and modify the `hello-rs` source code. On macOS, the best way to download git is to just install [Xcode](https://developer.apple.com/support/xcode/).

### External contributors

You can contribute to `hello-rs` by forking the `hello-rs` repository. For a detailed overview on forking, check out the [GitHub docs on forking](https://help.github.com/en/articles/fork-a-repo). In short, you will need to:

1. Fork the `hello-rs` repository
2. Clone your fork locally
3. Check out a new branch for your proposed changes
4. Push changes to your fork
5. Open a pull request against `datnguye/hello-rs` from your forked repository

## Setting up an environment

There are some tools that will be helpful to you in developing locally. While this is the list relevant for `hello-rs` development, many of these tools are used commonly across open-source Rust projects.

### Tools

In Rust, make sure you install Cargo. See [the installation guideline](https://doc.rust-lang.org/cargo/getting-started/installation.html).

## Testing

Cargo can run your tests with the `cargo test` command. Cargo looks for tests to run in two places: in each of your `src` files and any tests in `tests/`. Tests in your `src` files should be unit tests and [documentation tests](https://doc.rust-lang.org/rustdoc/write-documentation/documentation-tests.html). Tests in `tests/` should be integration-style tests. As such, you’ll need to import your crates into the files in `tests`.

Here’s an example of running `cargo test` in our [package](https://doc.rust-lang.org/cargo/appendix/glossary.html#package), which currently has no tests:

```log
$ cargo test
   Compiling hello v0.1.0 (file:///path/to/package/hello)
     Running target/test/hello-9c2b65bbb79eabce

running 0 tests

test result: ok. 0 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out
```

If our package had tests, we would see more output with the correct number of tests.

You can also run a specific test by passing a filter:

```bash
cargo test foo
```

This will run any test with `foo` in its name.

`cargo test` runs additional checks as well. It will compile any examples you’ve included to ensure they still compile. It also runs documentation tests to ensure your code samples from documentation comments compile. Please see the [testing guide](https://doc.rust-lang.org/book/ch11-00-testing.html) in the Rust documentation for a general view of writing and organizing tests. See [Cargo Targets: Tests](https://doc.rust-lang.org/cargo/reference/cargo-targets.html#tests) to learn more about different styles of tests in Cargo.

## Submitting a Pull Request

Code can be merged into the current development branch `main` by opening a pull request. A `hello-rs` maintainer will review your PR. They may suggest code revision for style or clarity, or request that you add unit or integration test(s). These are good things! We believe that, with a little bit of help, anyone can contribute high-quality code.

Automated tests run via GitHub Actions. If you're a first-time contributor, all tests (including code checks and unit tests) will require a maintainer to approve. Changes in the `hello-rs` repository trigger integration tests against Postgres. dbt Labs also provides CI environments in which to test changes to other adapters, triggered by PRs in those adapters' repositories, as well as periodic maintenance checks of each adapter in concert with the latest `hello-rs` code changes.

Once all tests are passing and your PR has been approved, a `hello-rs` maintainer will merge your changes into the active development branch. And that's it! Happy developing :tada:
