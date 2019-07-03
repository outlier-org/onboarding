![Outlier.org](https://i.imgur.com/vJowpL1.png)

---

# Engineering Onboarding Guide

Hey there! You're probably reading this because you've been invited to take one of our code challenges or are working on an Outlier engineering project. Welcome!

We're looking for talented developers to help us shape the future of education. Our platform has the world's best online, university-level courses, taught by some of the most celebrated educators in the world. Our courses use the active learning method to help students visualize, understand, and enjoy learning.

Code quality is very important to us, and we hope it is to you too. In this guide we'll share our engineering process that we use to ensure that we can build quickly while keeping our projects stable and maintainable. We'll cover topics like code style, commit guidelines, project workflow, and team communication.

## Code Style

Some developers feel the need to debate code style. Other engineers will use the project's style and get stuff done. We prefer engineers who get stuff done. Consistency is important, please follow these guidelines.

We use the [JavaScript Standard Style](https://standardjs.com/) in our code. This is the style used by npm, GitHub, Zeit, MongoDB, Express, Electron, and many others. Be sure to use an automatic formatter like [standard-formatter](https://atom.io/packages/standard-formatter) for Atom and [vscode-standardjs](https://marketplace.visualstudio.com/items/chenxsan.vscode-standardjs) for Visual Studio Code.

Line length should be limited to 80 characters.

## Code Principles

* Code should be as simple, explicit, and as easy to understand as possible.
* Functional style is preferred to OOP. When possible functions should be pure and not rely on shared state or side effects.
* Avoid large frameworks; use small modules that are easy to understand.
* Modules should be structured so that they can be understood easily when skimmed. Use this order:
  * External (`package.json`) dependencies (e.g. `require('http')`)
  * Internal dependencies (e.g. `require('./api')`)
  * Constants and other setup needed before `module.exports`
  * `module.exports`: either a single function or a "catalog object" (e.g. `module.exports = { method1, method2, ... }`)
  * Use function hoisting to control the placement of your functions so that important, high-level functions are at the top of the file, and small utility functions are at the bottom.
* Use descriptive variable names. Function names should be a verb like `route()` or verb combined with a noun like `routeRequest()`.
* Keep your functions short. If your function is over 40 lines, you should have a good reason.
* Functions should not accept more than 3 arguments. Use a single options object if you need more arguments.
* Keep nesting to a minimum. Use [early returns](https://blog.timoxley.com/post/47041269194/avoid-else-return-early), single-line conditionals, and function calls.

## Git

Version control is a project's best source of documentation when done correctly. When trying to understand code it's extremely useful to use `git blame` to find both the PR and the issue associated with that change.

PRs should be small and focused. Each commit should solve a single problem and be covered by a test that exemplifies that particular feature or fix.

All PRs must be reviewed by a teammate before they are eligle to be merged into  the `master` branch. Large PRs are difficult to review. Be sure to break large PRs into smaller ones so that they can be reviewed quickly and deployed to production.

* Never commit passwords, access tokens, or other credentials into version control. If you think you absolutely have to, ask first. If you do this by accident, tell someone immediately.
* Each commit should be as small and as simple as possible.
* The project must be operational and have all tests passing after every commit.
* Use [Conventional Commits](https://www.conventionalcommits.org)
* Do not mix feature changes (added functionality) with fixes (restored functionality), refactors (no change in functionality), or style changes (only whitespace or other cosmetic changes).
* Do not modify a project's `.gitignore` to add files related to your editor or environment. Use your own [global .gitignore](https://stackoverflow.com/questions/7335420/global-git-ignore/22885996#22885996) for that instead.

## Workflow

We use Zenhub to manage our workflow. Each task is represented by an issue. As tasks near completion it moves from "Backlog" to "In Progress" to "Needs Review" to "Ready to Deploy".

* Backlog: This is where you will choose from issues to work on. Once you have selected one, move it to "In Progress"
In Progress: While you are working on an issue, it should stay in this column. Once you are finished and satisfied with your work, move it to "Needs Review"
* Needs Review: Each day you should be looking at this column for PRs to review. This column will list all issues that are complete and are waiting on review before they can be ready for deploy. Once a PR has been successfully reviewed and is ready to be deployed to production, it should be moved to "Ready To Deploy"
* Ready To Deploy: After an issue is finished and has been reviewed and approved by a teammate, it will moved to this column. After it has been deployed, it will be moved to the "Live" column.
