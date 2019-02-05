# Versioning

Systelab libraries version numbers indicate the level of changes that are introduced by the release. This use of [semantic versioning](https://semver.org/) helps you understand the potential impact of updating to a new version.

Version numbers have three parts: major.minor.patch. For example, version 5.2.9 indicates major version 5, minor version 2, and patch version 9.

The version number is incremented based on the level of change included in the release.

Major releases contain significant new features, some but minimal developer assistance is expected during the update. When updating to a new major release, you may need to run update scripts, refactor code, run additional tests, and learn new APIs.

Minor releases contain new smaller features. Minor releases are fully backward-compatible; no developer assistance is expected during update, but you can optionally modify your apps and libraries to begin using new APIs, features, and capabilities that were added in the release. We update peer dependencies in minor versions by expanding the supported versions, but we do not require projects to update these dependencies.

Patch releases are low risk, bug fix releases. No developer assistance is expected during update.

# Branching model

Two types of branches will be considered, the Official branches and the Working branches.

### Official branches

Official branches will be named as Major.Minor.x, for example 5.12.x

Rules to 'Require pull request reviews before merging' should be applied to every Official branch. You can use wildcards in order to do so.

For each change:

- For a new minor change, the contributor should create a new Official branch, for example 5.13.x
- For a new major change, the contributor should create a new Official branch, for example 6.0.x
- You do not need to create a new branch for a patch change.

### Working branches

Working branches will be named as xxxxxx

## Branching procedure

In order to add changes to an Official branch:

 - Based on the rules above, decide if you have to create a new Official branch.
 - Create a new Working branch from any Official branch.
 - Commit the changes to the new Working branch.
 - Create a Pull Request from the Working branch to the Official Branch.
 - Once the Pull Request is approved it is time to merge the changes. Will be the submitter the responsible for merging.
 - Finally, the Working branch could be removed.

> Before creating the PR, be sure to update, as needed, the npm library version in the package.json file.

# Releasing

The submitter should create a new release, with the tag version vX.Y.Z and release title X.Y.Z.

Travis will publish the library to npm.
