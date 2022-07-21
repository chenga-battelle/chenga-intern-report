# Albert Cheng Summer 2022 Intern Report

Providing overview and documentation of the various tasks I was able to help with during the summer.

## Table of Contents
1. [Onboarding Documentation Rework](#onboarding-documentation-rework)
    1. [Content Edits](#content-edits)
    2. [Documentation Restructing](#documentation-restructuring-proposed-solution-overview)
2. [Proper Versioning for CUBE CLI release](#bug-fix---binary-build-of-cube-cli-from-github-actions-to-set-version-properly)
3. [Add Global Admin Check in set-local-env](#feature-request---set-local-env-script-in-cube-platform-to-check-that-script-user-is-an-azure-ad-global-administrator-in-the-tenant)
4. [Adding Documentation for cube-cli-download Script](#documentation---adding-documentation-for-cube-cli-download-script)
5. [Work on Make it look more good (cube-program #145)](#documentation---make-it-look-more-good)



## Onboarding Documentation Rework


### Content Edits

#### Overview

I was able to help update and rework some of the Getting Started/Accounts and Access and Getting Started/Environment Setup content on the super-train site.

#### Linked PRs/Issues/Commits

- [#144 - content edits](https://github.com/battelle-cube/cube-program/pull/144)
- [#138 - updating supertain documentation](https://github.com/battelle-cube/cube-program/pull/138)
- a selection of commits directly to main (first on 05/23/2022)

#### Details

Detailed personal documentation during my onboarding as well as the couple other opportunities to set up a qb VDI from scratch informed the content edits I was able to make. Nothing too crazy, just updating some sections, revising some out-of-date links, and adding a couple of sections (notably: Git LFS, Windows Remote Desktop, WSL)



### Documentation Restructuring Proposed Solution Overview

#### Overview

Proposed a solution for workflow and structuring of all repository documenation using the cube program site. We went with a sym link/submoduling workflow instead.

#### Linked PRs/Issues/Commits

- [new-documentation repo](https://github.com/chenga-battelle/new-documentation)
    - "source" repo emulating a repository in battelle-cube with documentation that we want to push onto the cube program site
- [hugo-tutorial repo](https://github.com/battellecube/hugo-tutorial)
    - hugo static site emulating cube program site

#### Details

Solution Overview: I'm using a Github Action in my source repo which grabs any changes made to a certain file/folder (new-documentation/documentation folder in my case) and pushes those changes into another repository. Knowing that our hugo sites already have actions in place to redeploy the site upon pushed changes, I simply pushed the changes into an appropriate folder in the hugo-tutorial/content subfolder. I tested and saw that the actions were working properly.

Proposed solution would be to have this [Github action](https://github.com/chenga-battelle/new-documentation/blob/main/.github/workflows/main.yml) in each repository in battelle-cube, along with a documentation folder to house the relevant documentation for each repository.

One drawback is that we would need to use another action (can most likely use the same one) to also grab the root repo readmes.


## Bug Fix - Binary build of CUBE CLI from Github Actions to set version properly

### Overview

The binary build of CUBE CLI from the GitHub actions created release doesn't version properly, i.e., ```cube --version``` gives ```cube version dev-build``` instead of ```cube version <latest tag>-<latest commit>```.

### Linked PRs/Issues/Commits

- [#215 - Tag release](https://github.com/battelle-cube/cube-cli/pull/215)
    - see this PR for a demo of the original issue.
- [#216 - not tagging release version properly](https://github.com/battelle-cube/cube-cli/pull/216)

### Details

Emulated code I saw in local-build-install script to grab output from ```git describe --tags``` and use it as an option/flag in the CMAKE command.

Note: I found out that the action/checkout action only retrieves the latest commit which would give me a bad output since the full tag history wasn't cloned. I fixed this issue by adjusting the fetch-depth option in the action flag.


## Feature request - set-local-env script in CUBE platform to check that script user is an Azure AD Global Administrator in the tenant.

### Overview

### Linked PRs/Issues/Commits

### Details


## Documentation - adding documentation for cube-cli-download script

### Overview

### Linked PRs/Issues/Commits

### Details



## Documentation - make it look more good

### Overview

### Linked PRs/Issues/Commits

### Details

