# Outlier 101

## Terms, Acronyms, and Definitions

- **Cohort**: A group of students taking a course that starts at a particular time
- **Success team**: The team that works closely with students to ensure they complete courses successfully
- **Partnership Cohort**: Cohorts started as part of partnership with other universities or institutions. Refer relationship table in Airtable, where relationshipType is partnership.
- **VIP**: Account type that have access to all exercises but no assessments access (Exam, Quiz, Assignment)
- **VIPGRADEDCONTENT**: The same as VIP accounts but with access to assessments
- **Auditors**: Account type that have access to all exercises but without exam access
- **AL**: Active learning
- **MCQ**: Multiple choice question
- **BE**: Backend
- **FE**: Frontend
- **Epic**: A project that contains one or more zenhub tickets tailored at implementing a certain feature.
- **Feature Flag**: a way to prevent from showing unfinished works, so they will only be displayed when using a flag in the url, and remove the flag when we want to make the work live.
- **CTA**: Call To Action (Related to Converflow)
- **AC**: Active Campaign
- **AIF**: Academic Integrity Form
- **OLRF**: Online Learning Readiness Form
- **TOS**: Terms Of Service
- **PP**: Privacy Policy
- **AT**: Airtable
- **FP**: Florida Ploy
- **BQ**: Big Query
- **PG**: PostgreSQL
- **AD**: Admin Dashboard
- **PD**: Partnership Dashboard
- **WGC**: Writing Grade Center
- **GCS**: Google Cloud Storage
- **LMS**: Learning Management System - our course website like https://dashboard.outlier.org/, https://calculus.outlier.org/

## Tools and Platforms Used

- **Airtable**: Online database used to store student data, among other things. Replicates to a cloud-based instance of PostgreSQL for read queries
- **DatoCMS**: Content management service used to manage content on its platforms
- **MathType**: An Editor embedded in calculus-static app to allow students to enter mathematical symbols, equations, terms etc.
- **Proctorio**: Service and browser plugin used to proctor students during exams.
- **Segment**: Collects student data, then formats and sends it on to a huge range of integrated tools (ActiveCampaign, Amplitude and BigQuery etc) for analytics, marketing, and data warehousing. Rather than setting up API separately for each resource, we simply integrate once with Segment, and then connect to the tools of our choice.
- **Kaltura**: Video hosting platform
- **Active Campaign (AC)**: an Emailing CRM which is used to send emails to students based on automations and events triggered 
- **Yellowdig**: A community based forum used by students to collaborate with instructors and other students 
- **Redis**: A high speed in-memory cache server used to store active student progress and other frequently-used data 
- **Typeform**: A web based platform used to create registration, AIF and OLRF forms, without needing to write a single line of code for the forms.
- **Fullstory**: Third party tool to record students sessions, so that we can use it to reproduce bugs by walking through the steps students have gone through when a bug occurs.
- **GCS (Google Cloud Storage)**: Object storage that’s capable of storing files containing JSON objects as well as static files. In our system we use GCS for storing old progress objects for students who have finished their cohorts so that their data doesn’t need to be frequently accessed or updated. We use it as well for storing text files (i.e pdf, docx, etc.) for students assignments submissions.
- **Shopify**: The store where students can purchase courses/cohort tokens used to enroll

## Tools/Platforms No Longer Actively Used

- **Drupal**: Content management System used prior to DatoCMS
- **Examity**: Exam proctoring service used prior to Proctorio
- **Wistia**: Video cloud platform where our lecture videos were hosted, replaced by Kaltura.
