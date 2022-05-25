## v1.4

### All workflows
- Add requested permissions to avoid dependency on user/org defaults being too permissive

### Check For Updates Workflow
- Default host to https://github.com/ (you can enter **myaccount/AL-Go-PTE@main** to change template)
- Support for "just" changing branch (ex. **\@Preview**) to shift to the preview version

### CI/CD Workflow
- Support for feature branches (naming **feature/\***) - CI/CD workflow will run, but not generate artifacts nor deploy to QA

### Create Release Workflow
- Support for release branches
- Force Semver format on release tags
- Add support for creating release branches on release (naming release/\*)
- Add support for incrementing main branch after release

### Increment version number workflow
- Add support for incremental (and absolute) version number change

### Environments
- Support environmentName redirection in CI/CD and Publish To Environments workflows
- If the name in Environments or environments settings doesn't match the actual environment name,
- You can add a secret called EnvironmentName under the environment (or \<environmentname\>_ENVIRONMENTNAME globally)


## v1.3

### Issues
- Issue #90 - Environments did not work. Secrets for environments specified in settings can now be **\<environmentname\>_AUTHCONTEXT**

### CI/CD Workflow
- Give warning instead of error If no artifacts are found in **appDependencyProbingPaths**

## v1.2

### Issues
- Issue #90 - Environments did not work. Environments (even if only defined in the settings file) did not work for private repositories if you didn't have a premium subscription.

### Local scripts
- **LocalDevEnv.ps1** and ***CloudDevEnv.ps1** will now spawn a new PowerShell window as admin instead of running inside VS Code. Normally people doesn't run VS Code as administrator, and they shouldn't have to. Furthermore, I have seen a some people having problems when running these scripts inside VS Code.


## v1.1

### Settings
- New Repo Setting: **GenerateDependencyArtifact** (default **false**). When true, CI/CD pipeline generates an artifact with the external dependencies used for building the apps in this repo.
- New Repo Setting: **UpdateDependencies** (default **false**). When true, the default artifact for building the apps in this repo is not the latest available artifacts for this country, but instead the first compatible version (after calculating application dependencies). It is recommended to run Test Current, Test NextMinor and Test NextMajor in order to test your app against current and future builds.

### CI/CD Workflow
- New Artifact: BuildOutput.txt. All compiler warnings and errors are emitted to this file to make it easier to investigate compiler errors and build a better UI for build errors and test results going forward.
- TestResults artifact name to include repo version number and workflow name (for Current, NextMinor and NextMajor)
- Default dependency version in appDependencyProbingPaths setting used is now latest Release instead of LatestBuild
