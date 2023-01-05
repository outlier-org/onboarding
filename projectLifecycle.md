## Project Lifecycle

At Outlier, all projects are created as tickets through [Zenhub](https://app.zenhub.com/). However, not all tickets are "projects". There are plenty of one-offs, bug fixes, and small enhancements which need not be classified as a Project.

To be classified as a Project, a ticket must be one or more of the following:
* An Epic
* A ticket with the `high impact` label
* A ticket created by the Product team and assigned to Engineering

If a ticket is classified as a Project, the following steps take place:

1. The Project is assigned to a development team or a developer by the Engineering Manager or Project Manager. 
2. Assigned developer(s) creates an estimate ([this is a good resource for generating estimations](https://jacobian.org/2021/may/25/my-estimation-technique/)) of the work involved. The creation of this estimate will usually have a deadline assigned by the Engineering Manager or Project Manager, but should usually be done as soon as is pracitcal given other work priorities.
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
> **Document**: *Link to [planning document(s)](./projectLifecycle.md#planning-document) (such as Google Docs, PDF, etc.) implementation options considered, reason for choice, estimation and other information, if applicable*

4. Follow the [Workflow](./gitAndGitHub.md#workflow) process to complete the Project.

5. [Documentation](./projectDocumentation.md) must be added or updated in the repository for this Project's code. If a project spans multiple repositories (e.g. `outlier-api` and `calculus-staic`), relevant documentation should be added to both. 

Note:
 - The total estimated hours for completion of a project should not be greater than 80 hours.
 - If a project is estimated to take longer, the project should be broken down into smaller sub-projects.

### Updating Project Thread
This is an important part of working on a project. Once you make a project post in #engineering-projects, never edit it. Any updates to the hours and RTD should be posted in the project’s thread. Copy the original post, make your modifications in that and paste it as reply to the same thread. Also include an explanation for the update.

The project thread not only contains updates to hours and RTD, but also things that happened that were meaningful to the project. For example, any change in requirement, any blocker that is resolved, and so on. Make sure that a project thread is never empty.

### Planning Document
In order to facilitate proper forethought and planning in a project, a planning document should contain the following, at a minimum:
* Introduction which identifies the problem/task to be solved, along with relevant context.
* Presentation of at least three engineering approaches to solve the problem/task.
* After the presentation of each approach, the pros and cons of each approach should be listed so the approaches can be compared.
* A summary in which the chosen approach is identified, along with a logical explanation for its selection.
* Any other relevant information explaining the estimate or project details.

### Additional Notes
* Tickets marked with the label `Urgent` bypass this process and should be worked on immediately.
* All other tickets not classified as Projects are put in the backlog for developers to pick up when possible. Occasionally, a non-Project ticket will be given priority treatment if requested by Product or the Engineering Manager.
