## Standuply Reports

Here at Outlier, we utilize a service called Standuply.
Standuply is a program that runs stand-up meetings in text format in Slack. It helps our distributed teams organize and run stand-ups no matter the distance.

These reports provide critical information and updates from engineers that helps better improve engineering's context for overall work and progress throughout the GitHub organization.

There are **two** Standuply Reports. The first takes place once per week where a selected engineer in each group gathers said group's weekly goals and inputs them into the report.

The second is a daily standup that is filled out individually by each engineer.

### Daily Standup Questions 1 & 2: 
#### PR Aprovals & Rejections

It is important to be approving and rejecting PRs throughout the week. If you have not approved or rejected PRs on your daily Standuply Report, please provide a short explanation stating the reason why in [question 4](#Look-at-your-plan-from-the-previous-standup.-Did-you-successfully-complete-it?)

`Note:` Be sure to provide a link to each PR / issue you reviewed or worked on. Each PR should be formatted to display the commit type, project name, description, repository name issue number, and link to the appropriate PR / issue on ZenHub.

*example:*

>PR-1:`<commitType>`(`<projectName>`): `<pullRequestDescription>`(`<repositoryName>` `<issueNumber>`)

### Daily Standup Questions 3 & 4:
#### Specific and Measurable Responses

When responding to the questions from Standuply it is imperative to be descriptive and avoid vague statements. **The response needs to be a measurable, durable change to the repository.**
Thinking and planning is acceptable as long as there is **actual verifiable output**.

For example:

>**What do you plan to accomplish before the next Standup?**

>“I wrote up a doc researching and comparing the different ways to fix `<issue>` and it is available in a PR/issue/slack post”

>"By EOD, the `<component>` will change to teal when :hover is triggered."

are the correct responses, not:

>**What do you plan to accomplish before the next Standup?**

>“I thought a lot about how to fix `<issue>`”

>"Will work on `<component>`."


### An example of a good Daily Standup Response:

#### How many PRs have you approved since the last standup?

- 3
  - PR-1: fix(sbt): Append additional registry URL for Sbt plugins (#8105)
  - PR-2: feat(batect): Automatically extract dependencies for files included into Batect configuration (#8091)
  - PR-3: chore(deps): lock file maintenance (#8096)

#### How many PRs have you rejected since the last standup?

- 1
  - PR-1: fix: Revert "feat: secrets" (#8069)

#### Keeping the above in mind, what do you plan to accomplish before the next Standup? Do not include reviewing PRs as part of your answer.

I will stop student progress event listeners when using the site without auth0.

#### Look at your plan from the previous standup. Did you successfully complete it?

No, however, I have recorded the main factors that have caused me not to successfully complete my previous day's plan:

- Poor time management.

  - I have scheduled my day today to allocate additional time to complete the tasks I could not finish. As well as account for any potential time to correct mistakes that may be made.

- Too many code errors.

  - I believe that the main cause of the delay that caused me not to complete my plan was poor code quality. This lead to my PRs being rejected and sent back. This resulted in increased time to completion for each PR. I will make a concerted effort to improve the quality of my code.