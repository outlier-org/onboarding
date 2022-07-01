# Refactoring

Idea for creating this documentation arose from a discussion on our #engineering channel about [refactoring](https://outlierslack.slack.com/archives/CLRAJQV1T/p1655829762289799)


### Table of Contents
1. Definition
2. Why should we refactor?
3. When should we refactor?
4. Types of refactoring
5. When should I not refactor?
6. Two Hats


## 1. Definition

Refactoring could be defined as a "change internal structure of software to make it easier to understand and cheaper to modify without changing observable behavior"

In terms of actions, the task of refactoring could be described as a process to "apply small behavior-preserving steps and make a big change by stringing together a sequence of these steps"


## 2. Why should we refactor?

### 2.1 Refactoring Improves the Design of Software

- People generally change code to achieve short term goals
- There tends to be less focus on architecture during that time
- So, the code loses structure slowly but certainly overtime
- Regular refactoring is a way to keep structure of code and make the design robust

[Here](https://github.com/outlier-org/admin-static/pull/1696) is an example of how this principle can be applied.
The context of this PR is that a section of code started out quite small so as to not warrant a separate component.

Here, after some time, it made sense to create a separate component instead of adding on to the previous state. Hence this PR.


### 2.2 Refactoring Makes Software Easier to Understand

- When working on a problem, we're not thinking of future readability of the code
- We spend more time reading code than writing code, so it's quite important to make it easier for others to read the function
- Refactoring makes it easy to read code (for future)

In this example [PR](https://github.com/outlier-org/admin-static/pull/1655), the constants were moved to a separate dedicated location, which simplified the codebase and, with introduction of proper names, made codebase easier to understand.


### 2.3 Refactoring Helps Find Bugs

- Refactoring helps us understand code
- It helps to clarify our assumptions which is a really good thing to have done before working on a codebase
- If bugs are present, refactoring brings them to spotlight

This [PR](https://github.com/outlier-org/calculus-static/pull/5828) was created to fix a bug that was discovered when `SectionListExerciseItem` component was being refactored.


### 2.4 Refactoring Helps Program Faster

- Poor design in codebase will mean that the development pace slows down with time
- With good design of the software, development pace can be maintained or even increased with re-use of components
- Refactoring, in addition to the definitions, is a mechanism to move poor design to good design
- If this is successful, we can go on to make the development easier and make the code stay in active development faster for longer

Take for example a [PR](https://github.com/outlier-org/calculus-static/pull/4880) that refactored a component into two new components. This separation made development in other areas like exam retakes a lot easier.


## 3. When should we refactor?

Sometimes we tend to follow DRY principles too strictly when working in refactoring.
We try to eliminate any duplication of logic and vigorously clean them out.
However, that might not always be the best idea, since these two sections of code could diverge as quickly as they appeared.


*The Rule of Three:*

The first time you do something, you just do it. The second time you do something similar, you wince at the duplication, but you do the duplicate thing anyway. The third time you do something similar, you refactor.
For those who like baseball: Three strikes, then you refactor.


## 4. Types of Refactoring

### 4.1 Preparatory Refactoring: Making It Easier to Add a Feature

- If the code were structured a bit different, the feature would be easier to implement
- Refactor first, then implement the feature
- https://twitter.com/KentBeck/status/250733358307500032

Listed below are the different PRs created while working on [Change column order and add sorting functionality](https://github.com/outlier-org/admin-static/issues/1129)

1. [feat(SubmissionTable): update sorting button for submission time](https://github.com/outlier-org/admin-static/pull/1184)
2. [refactor(WritingGradeCenter): save unsorted list of submissions in context](https://github.com/outlier-org/admin-static/pull/1192)
3. [refactor(StudentSubmission): remove unnecessary deadline parameter](https://github.com/outlier-org/admin-static/pull/1197)
4. [refactor(WritingGradeCenter): move assignment deadline calculation to utils](https://github.com/outlier-org/admin-static/pull/1201)
5. [refactor(WritingGradeCenter): extract function for cohortDetails](https://github.com/outlier-org/admin-static/pull/1204)
6. [refactor(WritingGradeCenter): move cohortDetails info out of cohort-milestones](https://github.com/outlier-org/admin-static/pull/1208)
7. [refactor(WritingGradeCenter): simplify logic for sorting submissions](https://github.com/outlier-org/admin-static/pull/1199)
8. [feat(WritingGradeCenter): add "Time Left" column in submissions table](https://github.com/outlier-org/admin-static/pull/1207)
9. [refactor(WritingGradeCenter): calculate timeLeft before ordering submissions](https://github.com/outlier-org/admin-static/pull/1218)
10. [refactor(WritingGradeCenter): create separate component for submission headers](https://github.com/outlier-org/admin-static/pull/1219)
11. [refactor(WritingGradeCenter): move LoadingSpinner inside SubmissionTable](https://github.com/outlier-org/admin-static/pull/1234)
12. [feat(SubmissionTable): add assignment sorting by studentId](https://github.com/outlier-org/admin-static/pull/1215)
13. [feat(WritingGradeCenter): add sorting to all columns in submission table](https://github.com/outlier-org/admin-static/pull/1223)

As you can see a lot of the PRs are refactor PRs.

The refactor PRs generally focus on making it easier to add an upcoming feature, while preserving current functionality.

Once these refactor PRs are done, the feat PR is a relatively small change.

This also has a lot less chance to letting some bug slip through since smaller PRs can be reviewed much more rigorously.


### 4.2 Comprehension Refactoring: Making Code Easier to Understand

- Before adding a feature, we need to understand fully how the code behaves.
- Refactor code to make it more understandable
- We can implement the feature once we understand how the code works

[Allow students who didn't complete assignment to view prompt](https://github.com/outlier-org/calculus-static/issues/5638)

1. [refactor(AssignmentPage): move feedback to review page component](https://github.com/outlier-org/calculus-static/pull/5689)
2. [refactor(AssignmentPage): move submission page to new component](https://github.com/outlier-org/calculus-static/pull/5695)
3. [feat: show review page if past lock date](https://github.com/outlier-org/calculus-static/pull/5699)

The three refactor PRs above simplified the code and made it easier for the engineer to understand and make modifications to code.


### 4.3 Litter-Pickup Refactoring

- I understand how the code works but realize that it's doing it badly
- It's not exactly necessary to refactor
- If it takes small effort, do it right away
- If it takes longer to fix it, make a note and fix it later
- Work on the feature instead

This [PR](https://github.com/outlier-org/admin-static/pull/1234) is an example of why refactoring is necessary when we see something wrong in the codebase.

We could just fix the issue given that the solution doesn't take much time.
Otherwise creating a separate ticket is advised.


### 4.4 Planned Refactoring

- Set aside a time to refactor a piece of code
- Not related to any features
- Need to simplify code that's been giving trouble to the team regularly

This is an example [PR](https://github.com/outlier-org/calculus-static/issues/2306) for which certain amount of time was dedicated to solely improve a particular piece of code.


### 4.5 Long-Term Refactoring

- Some refactoring work can take a team weeks to complete
- Instead of dedicated/planned refactoring, gradually work on simplifying the code one small chunk at a time.

This [project] (https://github.com/outlier-org/calculus-static/issues/5077) serves as an example for one of those times when significant amount of time is needed to get the work done. In such instances, the collaboration of many people is needed to improve the code a small step at a time.


## 5. When Should I Not Refactor?

- If code is messy but it works and it doesn't need to be modified, it doesn't need to be refactored. You can treat it as a library.
  - For e.g. [wiris](https://github.com/outlier-org/calculus-static/blob/master/public/quizzes/resources/mathtype.js) [scripts](https://github.com/outlier-org/calculus-static/blob/master/public/quizzes/resources/quizzes.js) in calculus-static
- If it is small enough that it could be rewritten without much effort.
  - For e.g. components like [CompletedMarker](https://github.com/outlier-org/calculus-static/blob/master/src/Components/CompletedMarker/CompletedMarker.jsx) in calculus-static



## 6. Two Hats

This is a method for working on any feature, not just refactoring

- While working on any feature, divide the time between two distinct activities: adding functionality and refactoring.
- We should only focus on one thing at a time.
- When adding functionality, don't think about the structure of the code.
- When refactoring, don't change any functionality in the code.
- https://twitter.com/KentBeck/status/1111050408007360512

Again a good example of this approach would be the one discussed under "Preparatory Refactoring"

Here, the PRs are separated clearly such that the feature PRs are really small and just change the functionality, not the structure of the code.

Similarly, the refactor PRs make it easy to have an eventual feat PR which is small and dedicated to fix the required issue.


## The End
