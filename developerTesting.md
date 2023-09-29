# Developer testing requirements

Prior to submitting a PR for review and QA, a developer is required to test their code and ensure it is working properly. Below are testing checklists for each developer to follow prior to submitting their PR.

## Frontend Testing Checklist

**Functional Testing:**

- [ ] The UI changes should be as per design mockup.
- [ ] The behavior of the added/changed part/s should be as specified.
- [ ] The behavior of the related parts of the system that could be impacted by the change should be understood and tested, eg. Course home page / section page should be loaded in different account types when a change is made to the Navigation Component.
- [ ] Changes that could be used by more than one user type, should be tested by every type of them, eg. (changes in calculus-static repo, should be tested for outlier, student and VIP accounts).
- [ ] State updates in components like InstructorQuestionSet (calculus-static) are more prone to creating race-conditions. So check all scenarios, like visiting previous questions, testing in Review mode, selecting a question through question set pop up modal, etc.

**Non-Functional Testing:**

- [ ] The added changes should have their dedicated tests (unit, integration, E2E).
- [ ] Make sure that the added changes do not break any existing test.
- [ ] Make sure that any UI change introduced does not break an E2E ( Cypress ) test on dashboard and course apps as well as site-experience-monitor.
- [ ] The parts of the system that could be affected by the changes, their tests should be updated to reflect these new changes.
- [ ] Check if comments corresponding to the modified code are also updated
- [ ] Code standards and best practices should be followed.
- [ ] Follow graceful error handling (use try catch blocks) for API calls, JSON processing, etc.
- [ ] Use HOCs when consuming Auth0 and Student Data contexts (with .contextType we can’t consume more than one Context).


## Backend Testing Checklist

- [ ] [Outlier's best practices](https://github.com/outlier-org/onboarding/blob/master/codeStandards.md) are followed.
- [ ] The branch is rebased over the latest master branch.
- [ ] All the relevant meaningful tests (expected outcome & unexpected outcome) related to the latest changes are added with realistic results that are consistent with the real output.
- [ ] Understands affected areas related to changes in PR.
- [ ] PR changes are working as expected.
- [ ] If work in PR is high-impact, staging should be used to test real use-cases
- [ ] When tests include the new Date() or any date functionality. Test this with different time zones to prevent a test failing on the master branch for other developer
- [ ] All staging PRs that affect production data require a review from a developer that is not in #engineering-group-1.
