Before approving a PR, QA should verify if the following checklist items are completed:

- Read the original ticket and understand the requirements.
- The scenarios mentioned in `Notes to QA` are not exhaustive. The cases missed by the engineer are QAed.
- For PRs with feature flag, smoke test the site `without` the flag.
- If changes are made for one user type, smoke test the site as other types of users:
  - Changes made for a student account should be tested as an admin and VIP.
  - Changes made for a GGU user account should be tested as a GGU student, an active GGU student, a regular student, a regular student with un-submitted prospect record.
- If changes are made in `Quizzes`, make sure to test `Exams` thoroughly and vice versa. Smoke test of Guesswork and AL should be fine.
- Check if changes in course site (calculus-static) have equivalent changes in student dashboard (student-dashboard-static).
- Check if changes in admin dashboard (admin-static) have equivalent feature on partners dashboard (partners-static).
