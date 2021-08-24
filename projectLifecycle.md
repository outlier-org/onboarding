## Project Lifecycle

At Outlier, all projects are created as tickets through [Zenhub](https://app.zenhub.com/). However, not all tickets are "projects". There are plenty of one-offs, bug fixes, and small enhancements which need not be classified as a Project.

To be classified as a Project, a ticket must be one or both of the following:
* An Epic
* A ticket with the `high impact` label

If a ticket is classified as a Project, the following steps take place:

1. The Project is assigned to a development team or a developer by the Engineering Manager or Project Manager. 
2. Responsible developer(s) creates an estimate ([this is a good resource for generating estimations](https://jacobian.org/2021/may/25/my-estimation-technique/)) of the work involved. The creation of this estimate will usually have a deadline assigned by the Engineering Manager or Project Manager, but should usually be done as soon as is pracitcal given other work priorities.
3. Developer(s) post the estimate to the `#engineering-projects` channel using the following format:

> **Project**: *Project name linked to Zenhub URL*
> 
> **Work Start**: *Anticipated start date*
> 
> **Estimated Hours**: *Total estimated hours for completion*
> 
> **Optimal RTD**: *Date Ready To Deploy, in ideal conditions*
> 
> **RTD**: *Estimated Ready To Deploy date*
> 
> **Document**: *Link to planning document(s) (such as Google Docs, PDF, etc.) implementation options considered, reason for choice, estimation and other information, if applicable*

4. Follow the [Workflow](./gitAndGitHub.md#workflow) process to complete the Project.

5. [Documentation](./projectDocumentation.md) must be added or updated in the repository for this Project's code. If a project spans multiple repositories (e.g. `outlier-api` and `calculus-staic`), relevant documentation should be added to both. 

### Additional Notes
* Tickets marked with the label `Urgent` bypass this process and should be worked on immediately.
* All other tickets not classified as Projects are put in the backlog for developers to pick up when possible. Occasionally, a non-Project ticket will be given priority treatment if requested by Product or the Engineering Manager.
