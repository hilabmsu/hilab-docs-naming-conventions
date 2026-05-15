# Human Interaction Lab Naming Conventions
 
This document captures naming conventions used in the Human Interaction Lab to aid organization, consistency, and findability of lab content and resources.
 
- [GitHub](#github)
  - [Repository names](#repository-names)
  - [Branch names](#branch-names)
  - [Commit messages](#commit-messages)
  - [Pull requests](#pull-requests)
---
 
# GitHub
The following specifications establish naming naming conventions and workflow best practices for the using the HILab's GitHub accounts. These standards are platform agnostic and may be applied to nearly any general Git workflow.
 
## Repository names

Project repositories should be created by a team lead with access to the HILab's GitHub account. Project team members may then be added as collaborators on the repository. Once added they may clone a copy of the repository to workin and submit committed changes to. Once commits are submitted, the submitter should create a pull request from the GitHub site for review.

To set up repository to require pull requests before merging to main, go to the repository and navigate to Settings → Branches. Under Branch protection rules click Add rule. Enter "main" as the branch name pattern, then check Require a pull request before merging. Save the rule. Optionally you can also enable Require approvals (under the same rule) to enforce at least one reviewer signs off before merging.

General guidelines:
- Use all lowercase letters
- Use hyphenated spaces
- Use versionless phrases

The general structure of repository names is: 
- Organization centric: _organization-keyword-(general-description)\[-leadname\]_
- Project centric: _grant-subproject-(general-description)\[-leadname\]_

Some examples: 
- Organization centric:
  - `hilab-docs-naming-conventions`
  - `nirx-tools-turbo-satori`
- Project centric:
  - `ipal-prisma-results-analysis-simpson`
  - `ipal-mind-metahuman-pipeline-jayasaputra`
  - `ipal-mhchatbot-chatbot-pipeline-foran`

### Naming structure 
- `organization`: A group like a lab, vendor, department, etc. When self-referencing our lab, treat it like any other organization and identify it using its name or the short title `hilab`.
- `keyword`: A small set of predefined terms to help categorize repository types (see table below).
- `general description`: briefly captures function/purpose of this repository
- `leadname` (optional): the name of the person repsonsible for this repository (i.e., project lead, developer, author, etc.) 
- `grant`: A reference to a specific grant or body of work in the lab (e.g., iPAL, EAGER, etc.). The grant name can be used in place of the organization name.
- `subproject`: A reference to a specific component or focus area within a grant or body of work.

| keyword  | Meaning / use                            |
| -------- | ---------------------------------------- |
| analysis | Various analysis and data processing     |
| docs     | Documentation and specification files    |
| download | Scripts for downloading data             |
| model    | A computational model                    |
| tools    | General tools associated with the lab    |
| task     | JavaScript/MATLAB/Python tasks           |
 
---
 
## Branch names

In GitHub, the `main` branch is the primary stable branch. The `main` branch should not be worked in directly. Instead, sub-branches should be created for particular work, and pull requests made for review before merging changes into `main`.
 
General guidelines: 
- Use all lowercase letters
- Use hyphens to separate words
- Keep names short but descriptive
- Include a type prefix that mirrors the pull request prefix (see [Pull requests](#pull-requests)) to make the purpose immediately clear

The general structure of branch names is: 
_type/short-description_
 
Or, when the work is tied to a specific person:
_type/short-description-leadname_
 
Some examples:
- `feat/eeg-preprocessing-pipeline`
- `fix/satori-connection-timeout`
- `docs/update-naming-conventions`
- `refactor/task-loader-cleanup-simpson`

### Branch name structure 
- `type`: A prefix drawn from the same set used in commit messages and pull request titles (e.g., `feat`, `fix`, `docs`, `chore`). See [Pull requests](#pull-requests) for the full list.
- `short-description`: A brief, hyphen-separated phrase describing what the branch addresses.
- `leadname` _(optional)_: The last name of the person leading the work, included when it adds useful context (mirrors the optional `leadname` used in repository names).
> **Note:** Branch names should be deleted after their associated pull request is merged to keep the repository tidy.
 
---
 
## Commit messages
 
General guidelines:
- Use the imperative mood in the summary line (e.g., "add feature" not "added feature")
- Keep the summary line under 72 characters
- Use the same type prefix as branch names and pull request titles for consistency
- Capitalize only the first word of the summary; do not end with a period
- Optionally include a scope in parentheses to identify the affected component

The general structure of a commit message is: 
_type(scope): brief summary of what changed_
 
An optional body can follow a blank line for additional context:
 
```
feat(preprocessing): add bandpass filter to EEG pipeline
 
Applies a 1–40 Hz bandpass filter during preprocessing to reduce
noise before epoching. Filter parameters are configurable via
the task config file.
```
 
Some examples:
- `fix(satori): resolve dropped packet on reconnect`
- `docs: add branch naming guidelines to README`
- `chore: remove unused import in loader script`
- `feat(metahuman): integrate lipsync controller`

### Commit type prefixes
 
Commit messages use the same type prefixes as pull requests (see table in [Pull requests](#pull-requests)). Keeping these consistent makes it easy to trace a branch, its commits, and its eventual pull request at a glance.
 
> **Tip:** Prefer small, focused commits over large, multi-purpose ones. A commit should represent one logical change so that the history remains readable and individual commits can be reverted cleanly if needed.
 
---
 
## Pull requests
 
General guidelines: 
- Target `main` unless merging a staged feature into an integration branch
- Always request at least one reviewer before merging
- Link any related issues in the pull request description

The format of a pull request title is: 
_type(scope): summary of changes_
 
The `scope` is optional and identifies the affected component or subproject (e.g., `feat(metahuman): ...`). When omitted, the type alone is sufficient (e.g., `docs: ...`).
 
Some examples:
- `fix: allow useHref on synthetic links`
- `docs: fix typo in usePress docs`
- `feat(virtualization): add support for custom collection renderers`

### PR type prefixes
 
| Prefix     | Meaning / use                                                                         |
| ---------- | ------------------------------------------------------------------------------------- |
| `fix`      | Fixing a bug                                                                          |
| `feat`     | Adding a new feature                                                                  |
| `build`    | Updates that affect the build system or process                                       |
| `chore`    | Miscellaneous commits that do not affect code meaning (whitespace, formatting, typos in code, comment adjustments, etc.) |
| `docs`     | A change to documentation only                                                        |
| `test`     | Adding or fixing existing tests                                                       |
| `refactor` | A code change that neither fixes a bug nor adds a feature                             |
| `ci`       | Changes to the CI configuration                                                       |
| `localize` | Changes related to translations and localization                                      |
| `bump`     | Increasing the version of a dependency                                                |
| `revert`   | Undoing a previous commit                                                             |
