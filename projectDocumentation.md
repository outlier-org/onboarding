## Project Documentation

In order to preserve knowledge of integrated systems and the purpose of code, as well as provide newcomers an accurate representation of a project's function, all Projects must be documented accordingly in their repository using markdown. It is imperative that a project altering functionality also updates the documentation in order to prevent stale or incorrect information. Therefore, when working on a [Project](./projectLifecycle.md), it is not officially `Ready to Deploy` until documentation is added or updated accordingly:
* Markdown is created or updated in the Project repository's README file. If the documentation is substantial, an additional file or files can be created and must be linked from `README.md`. 
* Relevant process diagrams (in image or PDF format) are added to a `/docs` folder in the repository and linked from the relevant `.md` file. These diagrams can be snapshots from the original Figma mockup, or a flow diagram created by the developer to illustrate the process.
* Documentation should be succinct but not omit important details. 
* If the current Project merely alters or augments current functionality but documentation does not exist for it yet, it is the responsibility of the developer to create that documentation during their project work.
* It is the **responsibility of the PR reviewer** to ensure that proper documentation has been created/updated as part of the review process. A PR should not pass review if documentation has not been applied properly.
* The creation of documentation should be factored into the estimate provided during the [Project Lifecycle](./projectLifecycle.md).