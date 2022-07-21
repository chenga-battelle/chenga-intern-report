# Albert Cheng - Summer 2022 Intern Report

Providing overviews and documentation of the various projects I was able to help with during the summer.

## Projects/Tasks
1. [Onboarding Documentation Rework](#onboarding-documentation-rework)
    1. [Content Edits](#content-edits)
    2. [Documentation Restructing](#documentation-restructuring---proposed-solution-overview)
2. [Proper Versioning for CUBE CLI release](#bug-fix---binary-build-of-cube-cli-from-github-actions-to-set-version-properly)
3. [Add Global Admin Check in set-local-env](#feature-request---set-local-env-script-in-cube-platform-to-check-that-script-user-is-an-azure-ad-global-administrator-in-the-tenant)
4. [Adding Documentation for cube-cli-download Script](#documentation---adding-documentation-for-cube-cli-download-script)
5. [Work on Make it look more good (cube-program #145)](#documentation---make-it-look-more-good)



## Onboarding Documentation Rework



### Content Edits

#### Overview

I was able to help update and rework some of the Getting Started/Accounts and Access and Getting Started/Environment Setup content on the super-train site.

#### Linked PRs/Issues/Commits

battelle-cube/cube-program
- [#144 - content edits](https://github.com/battelle-cube/cube-program/pull/144)
- [#138 - updating supertain documentation](https://github.com/battelle-cube/cube-program/pull/138)
- a selection of commits directly to main (first on 05/23/2022)

#### Details

Detailed personal documentation during my onboarding as well as the couple other opportunities to set up a qb VDI from scratch informed the content edits I was able to make. Nothing too crazy, just updating some sections, revising some out-of-date links, and adding a couple of new sections (notably: Git LFS, Windows Remote Desktop, WSL)



### Documentation Restructuring - Proposed Solution Overview

#### Overview

Proposed a solution for workflow and structuring of all repository documenation using the cube program site. We went with a sym link/submoduling workflow instead.

#### Linked PRs/Issues/Commits

chenga-battelle
- [new-documentation repo](https://github.com/chenga-battelle/new-documentation)
    - "source" repo emulating a repository in battelle-cube with documentation that we want to push onto the cube program site

battellecube
- [hugo-tutorial repo](https://github.com/battellecube/hugo-tutorial)
    - hugo static site emulating cube program site

#### Details

Solution Overview: I'm using a Github Action in my source repo which grabs any changes made to a certain file/folder (new-documentation/documentation folder in my case) and pushes those changes into another repository. Knowing that our hugo sites already have actions in place to redeploy the site upon pushed changes, I simply pushed the changes into an appropriate folder in the hugo-tutorial/content subfolder. I tested and saw that the actions were working properly.

Proposed solution would be to have this [Github action](https://github.com/chenga-battelle/new-documentation/blob/main/.github/workflows/main.yml) in each repository in battelle-cube, along with a documentation folder to house the relevant documentation for each repository.

One drawback is that we would need to use another action (can most likely use the same one) to also grab the root repo readmes.



## Binary build of CUBE CLI from Github Actions to set version properly

### Overview

The binary build of CUBE CLI from the GitHub actions created release doesn't version properly, i.e., ```cube --version``` gives ```cube version dev-build``` instead of ```cube version <latest tag>-<latest commit>```.

### Linked PRs/Issues/Commits

battelle-cube/cube-cli
- [#215 - Tag release](https://github.com/battelle-cube/cube-cli/pull/215)
    - see this PR for a demo of the original issue.
- [#216 - not tagging release version properly](https://github.com/battelle-cube/cube-cli/pull/216)

### Details

Emulated code I saw in local-build-install script to grab output from ```git describe --tags``` and use it as an option/flag in the CMAKE command.

Note: I found out that the action/checkout action only retrieves the latest commit which would give me a bad output since the full tag history wasn't cloned. I fixed this issue by adjusting the fetch-depth option in the action flag.



## set-local-env script in CUBE platform to check that script user is an Azure AD Global Administrator in the tenant.

### Overview

Some of the commands outputted by the set-local-env script need the user to be a global administrator in the tenant. I added code to the script's pre-flight checklist that checks to see if the logged in user is a global administrator in the current tenant.

### Linked PRs/Issues/Commits

battelle-cube/cube-platform
- [#83 - added checks for global admin role](https://github.com/battelle-cube/cube-platform/pull/83)

### Details

I used the Microsoft Graph API to retrieve a list of userIDs of the global administrators in the tenant. I then used a JMES function to check if the current user's ID is a part of the list.



## adding documentation for cube-cli-download script

### Overview

I added content to our super-train site documenting the new cube-cli-download script.

### Linked PRs/Issues/Commits

battelle-cube/cube-program
[#155 - Add TODO for download script documentation](https://github.com/battelle-cube/cube-program/pull/155)

### Details



## make it look more good

### Overview

This is an open draft pull request. I removed two obsolete commits through an interactive rebase and kept the one relevant commit in the branch.

### Linked PRs/Issues/Commits

battelle-cube/cube-program
[#145 - Make it look more good](https://github.com/battelle-cube/cube-program/pull/145)

### Details

