# Contributing

Thanks for helping out!

## Monorepo!

Victory is a monorepo built with [Lerna](https://lernajs.io/) and [Yarn](https://yarnpkg.com/) workspaces. All `victory-*` packages live in the `packages` directory, and each has its own `package.json`. Installing this repo with `yarn` will automatically link all interdependent `victory-*` packages. **You must use `yarn` rather than `npm` when installing and running `package.json` scripts in this project.**

## `package-scripts.js`

Victory uses [`nps`](https://github.com/kentcdodds/nps) to organize package scripts. Check `package-scripts.js` for the full list of commands.

### Requirements

- [Node.js](https://nodejs.org/) 8.10.0 or higher.
- [Yarn](https://yarnpkg.com/en/docs/install) 1.7.0 or higher.

### Setup

Clone this repo:

```console
$ git clone https://github.com/FormidableLabs/victory.git
$ cd victory
```

Use [Yarn](https://yarnpkg.com/) to install dependencies:

```console
$ yarn install
```

Run a development server and check out the demos. This command will also build and watch `lib/` and `es/` directories in all packages, so your demos will always be in sync with code changes.

```console
$ yarn start
```

running this command will serve demo pages at http://localhost:3000/ and tests at http://localhost:3001/test/client/test.html

## Checks, Tests

When running a development server, tests will be served automatically at http://localhost:3001/test/client/test.html

Tests my also be run in the terminal with:

```console
$ yarn nps test
```

If your terminal is under a proxy, you should turn off the proxy, or ChromeHeadless will not start properly.

Victory uses eslint and prettier to maintain code style consistency. Before creating a pull request, please lint and format your changes with the following commands:

```console
$ yarn nps lint
$ yarn nps format
```

## Visual Tests

Victory relies heavily on visual regression testing with [Storybook](https://storybook.js.org/) and [Chromatic](https://www.chromaticqa.com/).

Write visual tests for new features by adding them in the `stories` directory. Run storybooks and check out changes. Storybooks are served from localhost:6006/

```console
$ yarn storybook
```

[Chromatic](https://www.chromaticqa.com/) provides automated visual testing. All internal PRs will trigger a new Chromatic build, which will be displayed along with CI status. Chromatic builds for Victory may be viewed in more detail here: https://www.chromaticqa.com/builds?appId=5b4acf7c54c0490024d5980b. Chromatic requires a secret app code to run, so PRs from external contributors will not automatically trigger a Chromatic build. For this reason, changes from external contributors will be checked out and opened as separate PRs so Chromatic may be used to verify any changes. Developers with access to the secret app code may also trigger a chromatic build manually with:

```console
$ yarn chromatic
```

## Release

Before publishing any new version, please update `CHANGELOG.md` with a summary of changes and links to any PRs involved in the release.

Victory uses [Lerna](https://lernajs.io/) to automate versioning and publishing packages.

Each package must contain the following `version` script `package.json`:

```
"scripts": {
  "version": "nps build-libs && nps build-dists",
}
```

Pre version checks are run _once_ for all packages, and are defined in the root directory `package.json`

```
"preversion": "nps check"
```

The following commands will let you try a version without publishing or creating git commits:

```console
// This command bumps versions, runs checks, builds libs. No git commits will be made, and nothing will be published. `package.json` files in all packages will be altered, so be careful to clean up afterwards.
$ nps lerna-dry-run
```

To publish a package _for real_

```console
$ lerna publish
```

You will be prompted to select an appropriate version before continuing. Lerna will run preversion checks, bump versions in all packages, create git commits, build libs, and publish packages. The whole process takes about 5 minutes. Be patient!

## Contributor Covenant Code of Conduct

### Our Pledge

In the interest of fostering an open and welcoming environment, we as
contributors and maintainers pledge to making participation in our project and
our community a harassment-free experience for everyone, regardless of age, body
size, disability, ethnicity, gender identity and expression, level of
experience, nationality, personal appearance, race, religion, or sexual identity
and orientation.

### Our Standards

Examples of behavior that contributes to creating a positive environment
include:

- Using welcoming and inclusive language
- Being respectful of differing viewpoints and experiences
- Gracefully accepting constructive criticism
- Focusing on what is best for the community
- Showing empathy towards other community members

Examples of unacceptable behavior by participants include:

- The use of sexualized language or imagery and unwelcome sexual attention or
  advances
- Trolling, insulting/derogatory comments, and personal or political attacks
- Public or private harassment
- Publishing others' private information, such as a physical or electronic
  address, without explicit permission
- Other conduct which could reasonably be considered inappropriate in a
  professional setting

### Our Responsibilities

Project maintainers are responsible for clarifying the standards of acceptable
behavior and are expected to take appropriate and fair corrective action in
response to any instances of unacceptable behavior.

Project maintainers have the right and responsibility to remove, edit, or
reject comments, commits, code, wiki edits, issues, and other contributions
that are not aligned to this Code of Conduct, or to ban temporarily or
permanently any contributor for other behaviors that they deem inappropriate,
threatening, offensive, or harmful.

### Scope

This Code of Conduct applies both within project spaces and in public spaces
when an individual is representing the project or its community. Examples of
representing a project or community include using an official project e-mail
address, posting via an official social media account, or acting as an appointed
representative at an online or offline event. Representation of a project may be
further defined and clarified by project maintainers.

### Enforcement

Instances of abusive, harassing, or otherwise unacceptable behavior may be
reported by contacting the project team at coc@formidable.com. All
complaints will be reviewed and investigated and will result in a response that
is deemed necessary and appropriate to the circumstances. The project team is
obligated to maintain confidentiality with regard to the reporter of an incident.
Further details of specific enforcement policies may be posted separately.

Project maintainers who do not follow or enforce the Code of Conduct in good
faith may face temporary or permanent repercussions as determined by other
members of the project's leadership.

### Attribution

This Code of Conduct is adapted from the [Contributor Covenant][homepage],
version 1.4, available at [http://contributor-covenant.org/version/1/4][version]

[homepage]: http://contributor-covenant.org
[version]: http://contributor-covenant.org/version/1/4/
