# GIT guidelines

## Configure your git

Based on ancestral experience and oral tradition, the following things
go a long way towards making your commits more helpful:

-   Be sure to define both the user.email and user.name in your local
    git config

    ```shell
    git config --global <var> <value>
    ```

-   Be sure to add your full name to your Github profile here.

## Pre-commit hooks

### Installation
To install the pre-commit hooks, run the following command:

```shell
pip install pre-commit
```

### Usage
When you commit code, a pre-commit hook will check your code for common mistakes. If the hook fails, the commit will be aborted. To install the pre-commit hook, run the following command:

```shell
pre-commit install
```

## Branch naming

Branches should be named after the issue they are related to and start with the number of the issue they refer to. If there is no issue, use a short description of the task. Branch names should be in lowercase and use dashes to separate words. For example:

- `1234-add-very-short-name`
- `1234-fix-unittest-account`
- `1234-i18n-translation`

## Commit message structure

Commit message has four parts: tag, module, short description and full
description. Try to follow the preferred structure for your commit
messages

```text
[TAG] module: describe your change in a short sentence (ideally < 50 chars)

Long version of the change description, including the rationale for the change,
or a summary of the feature being introduced.

Please spend a lot more time describing WHY the change is being done rather
than WHAT is being changed. This is usually easy to grasp by actually reading
the diff. WHAT should be explained only if there are technical choices
or decision involved. In that case explain WHY this decision was taken.

End the message with references, such as task or bug numbers, PR numbers, and
OPW tickets, following the suggested format:
task-123 (related to task)
Fixes #123  (close related issue on Github)
Closes #123  (close related PR on Github)
opw-123 (related to ticket)
```

## Tag and module name

Tags are used to prefix your commit. They should be one of the following

- `[FIX]` for bug fixes: mostly used in stable version but also valid if you are fixing a recent bug in development version
- `[REF]` for refactoring: when a feature is heavily rewritten
- `[ADD]` for adding new modules
- `[REM]` for removing resources: removing dead code, removing views, removing modules, ...
- `[REV]` for reverting commits: if a commit causes issues or is not wanted reverting it is done using this tag
- `[MOV]` for moving files: use git move and do not change content of moved file otherwise Git may loose track and history of the file also used when moving code from one file to another
- `[REL]` for release commits: new major or minor stable versions
- `[IMP]` for improvements: most of the changes done in development version are incremental improvements not related to another tag
- `[I18N]` for changes in translation files

After tag comes the modified module name. Use the technical name as functional name may change with time. If several modules are modified, list them or use various to tell it is cross-modules. Unless really required or easier avoid modifying code across several modules in the same commit. Understanding module history may become difficult.

## Commit message header

After tag and module name comes a meaningful commit message header. It should be self explanatory and include the reason behind the change. Do not use single words like "bugfix" or "improvements". Try to limit the header length to about 50 characters for readability.

Commit message header should make a valid sentence once concatenated with `if applied, this commit will <header>`. For example `[IMP] base: prevent to archive users linked to active partners` is correct as it makes a valid sentence `if applied, this commit will prevent users to archive...`.

# Commit message full description

In the message description specify the part of the code impacted by your changes (module name, lib, transversal object, \...) and a description of the changes.

First explain WHY you are modifying code. What is important if someone goes back to your commit in about 4 decades (or 3 days) is why you did it. It is the purpose of the change.

What you did can be found in the commit itself. If there was some technical choices involved it is a good idea to explain it also in the commit message after the why. For developers "PO team asked me to do it" is not a valid why, by the way.

Please avoid commits which simultaneously impact multiple modules. Try to split into different commits where impacted modules are different. It will be helpful if we need to revert changes in a given module separately.

Don\'t hesitate to be a bit verbose. Most people will only see your commit message and judge everything you did in your life just based on those few sentences. No pressure at all.

**You spend several hours, days or weeks working on meaningful features. Take some time to calm down and write clear and understandable commit messages.**

If you are a developer the WHY should be the purpose of the task you are working on. Full specifications make the core of the commit message. **If you are working on a task that lacks purpose and  specifications please consider making them clear before continuing.**

Finally here are some examples of correct commit messages :

``` text
[REF] models: use `parent_path` to implement parent_store

 This replaces the former modified preorder tree traversal (MPTT) with the
 fields `parent_left`/`parent_right`[...]

[FIX] account: remove frenglish

 [...]

 Closes #22793
 Fixes #22769

[FIX] website: remove unused alert div, fixes look of input-group-btn

 Bootstrap's CSS depends on the input-group-btn
 element being the first/last child of its parent.
 This was not the case because of the invisible
 and useless alert.
```

> [!TIP]
> Use the long description to explain the *why* not the *what*, the *what* can be seen in the diff

## Pull Requests

### Policy

A pull request should be created when you've checked the following checklist:

1. **Code Quality**: The code is well written, easy to read, and follows the guidelines.
2. **Tests**: The code is covered by tests and all tests pass.
3. **Documentation**: The code is documented and the documentation is up to date.
4. **Squash Commits**: The commits are squashed into a single commit with a clear message which follows the guidelines in this document. A PR should never be created with multiple commits except when there is a good reason to do so.
  Example of bad commit history
    ```shell
    [ADD] models: add new model
    [IMP] models: improve model
    [IMP] models: improve model
    [FIX] models: fix model
    ```
    Example of good commit history
    ```shell
    [ADD] models: add new model
    ```
5. **Rebase**: The branch is rebased on the latest develop branch.
6. Assign the PR to the correct reviewer(s) and add the correct labels.

When creating a pull request, make sure to follow the following guidelines:

-  **Title**: The title will be automatically filled with the commit message
- **Description**: The description should be a summary of the changes and the reason behind them. Usually the text from the commit message is enough.
- **Target branch**: The target branch should be the branch you want to merge your changes into. Usually this is the develop branch, because that branch will be merged to the master branch when a new release is made.
