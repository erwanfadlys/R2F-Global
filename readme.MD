# R2F Submission Tracker Technical Documentation

## 1. Introduction

The **R2F Submission Tracker** is a dynamic business application designed to streamline the process of submitting Repair-to-Field (R2F) equipment requests. It empowers users across different localities and districts to efficiently create, manage, and collaborate on R2F equipment submissions. Key features of this application include:

- **User Localities:** Users from various regions and districts can submit R2F equipment requests tailored to their specific needs and requirements.

- **Administrator Access:** Administrators have wider access, allowing them to oversee and manage R2F submissions across multiple regions.

- **Real-time Data:** The application provides real-time visibility into the status and progress of equipment requests, facilitating informed decision-making.

- **Collaboration:** Users can seamlessly collaborate with different districts and teams, enhancing the efficiency of R2F equipment implementation.

This technical documentation aims to provide a comprehensive understanding of the app's architecture, functionality, and usage. It covers data management, approval workflows, user interfaces, integrations, application lifecycle management, user training, and special functionalities.
## Table of Contents

- [R2F Submission Tracker Technical Documentation](#r2f-submission-tracker-technical-documentation)
  - [1. Introduction](#1-introduction)
  - [Table of Contents](#table-of-contents)
  - [2. App Overview](#2-app-overview)
    - [Data Sources](#data-sources)
    - [Data Management](#data-management)
    - [Approval Workflow](#approval-workflow)
  - [User Interface](#user-interface)
    - [Color Template](#color-template)
    - [User Roles and Permissions](#user-roles-and-permissions)
    - [Dynamic Inputs](#dynamic-inputs)
  - [3. Integrations](#3-integrations)
    - [Power BI Integration (In Progress)](#power-bi-integration-in-progress)
  - [4. Application Lifecycle Management (ALM)](#4-application-lifecycle-management-alm)
    - [Environment Management](#environment-management)
    - [Version Control](#version-control)
    - [Deployment Strategies](#deployment-strategies)
    - [Solution Ownership](#solution-ownership)
  - [5. User Training](#5-user-training)
    - [Training Sessions](#training-sessions)
    - [Access Control](#access-control)
    - [Training Materials](#training-materials)
    - [Ongoing Support](#ongoing-support)

## 2. App Overview

The **R2F Submission Tracker** is a versatile business application designed to meet the unique requirements of managing Repair-to-Field (R2F) equipment submissions. Here's an overview of its key aspects:

### Data Sources

The app relies on multiple data sources, each serving a specific region, to ensure data segregation and minimize synchronization issues. These data sources include:

1. **Equipment Mapping:** Contains critical mapping information.
2. **AP Table:** Records specific to the Asia-Pacific region.
3. **MENA Table:** Records for the Middle East and North Africa.
4. **EESSA Table:** Records for Eastern Europe, South Asia, and Africa.
5. **NAL Table:** Records for North America and Latin America.
6. **LATAM Table:** Records specific to Latin America.

These tables store records for viewing and editing, ensuring that data is organized and accessible based on region.

### Data Management

The dataset for the **R2F Submission Tracker** is securely stored in SharePoint. However, due to SharePoint's policy, only datasets in Excel format can be accessed by users. To ensure data integrity and prevent contamination, consideration has been given to implementing a SharePoint user view. This view effectively hides the dataset file from the user's display, thus minimizing the risk of unintended modifications.

This approach not only aligns with SharePoint's policy but also adds an additional layer of protection to the dataset. It ensures that only authorized users with appropriate access privileges can interact with the data. This data management strategy enhances the security and reliability of the application's dataset.


### Approval Workflow

The app includes an approval workflow that routes submissions to user managers. Below is a template of the approval message in Markdown format:

```markdown
### R2F Approval Request

Dear [Manager],

Requesting approval for the following items:

- **Item 1**
   - **Description:** @{triggerBody()['text_4']}
   - **Material Number:** @{triggerBody()['text_3']}
   - **Repair Cost:** USD @{triggerBody()['text_5']}
   - **Repair Type:** @{triggerBody()['text_7']}
   - **Savings:** @{triggerBody()['text_8']}
   - **Sub PSL:** @{triggerBody()['text_9']}
   - **Material Number Count:** @{triggerBody()['text_10']}

Total for this equipment number.

Please review the information above and provide your approval.
```
## User Interface

The **R2F Submission Tracker** features a user-friendly and visually appealing user interface (UI) designed to enhance the user experience. Key aspects of the UI design are as follows:

### Color Template

The primary color template of the UI utilizes red/grey backgrounds with white fonts, occasionally incorporating black text. This design choice was made to provide a visually pleasing and intuitive interface for users. The combination of red and grey creates a modern and professional look, while white text ensures readability and clarity. The selective use of black text adds emphasis to specific elements or information.

### User Roles and Permissions

The app caters to two primary user roles: **User** and **Admin**. Each role is presented with an interface tailored to their specific responsibilities and permissions:

- **User Role:** Users in this role have restricted access to equipment data and are only able to view and update equipment entries specific to their region or locality. This restriction is enforced to ensure data is sanitized, and users can interact only with equipment records relevant to their area.
```
```
- **Admin Role:** Administrators have elevated permissions, allowing them to not only enter and manage equipment data for their own region but also for other regions. Admins have the ability to view and update equipment records across multiple localities, providing greater flexibility and control. This extended access also applies to the report page, where admins can generate reports for various regions.

### Dynamic Inputs

To further enhance the user experience, the UI incorporates dynamic input fields. The visibility and availability of certain input fields are determined by factors such as the user's role, region, or district. This dynamic approach ensures that users are presented with relevant options and information based on their specific context, streamlining the data entry process.

The user interface of the **R2F Submission Tracker** is a key component in facilitating efficient equipment submissions and management. It provides an intuitive and responsive environment for users, enhancing productivity and usability.

Please continue reading for more information on integrations, application lifecycle management, user training, and special functionalities in the following sections.

## 3. Integrations

The **R2F Submission Tracker** integrates with external tools to enhance data analysis and reporting capabilities. Here's an overview of the integrations:

### Power BI Integration (In Progress)

Integration with Power BI is currently in progress. This integration empowers users to perform in-depth data analysis and generate insightful reports based on the R2F equipment submissions. Power BI's robust visualization capabilities will enable users to gain valuable insights into equipment status, trends, and performance metrics.

The Power BI integration aims to provide the following benefits:

- **Data Analysis:** Users can perform comprehensive data analysis to identify patterns, trends, and areas for improvement in equipment submissions.

- **Visual Reporting:** Power BI's rich visualization tools will allow users to create interactive and visually appealing reports and dashboards.

- **Real-time Updates:** Users will have access to real-time data updates, ensuring that reports reflect the most current information.

## 4. Application Lifecycle Management (ALM)

The **R2F Submission Tracker** follows a structured approach to Application Lifecycle Management (ALM) to ensure the reliability and scalability of the application. Below are the key aspects of ALM implemented for this application:

### Environment Management

The application operates in multiple environments to support different stages of development, testing, and production. These environments include:

- **Development Environment:** The initial development and testing of new features take place in this environment. It allows for experimentation and validation of changes.

- **Testing Environment:** After development, changes are thoroughly tested in this environment to identify and address any issues or bugs. User acceptance testing (UAT) also occurs here.

- **Production Environment:** The live version of the application is deployed in this environment, serving end-users for day-to-day operations.

### Version Control

Version control is implemented to manage changes to the application's codebase and configurations. It allows for tracking modifications, rolling back to previous versions if necessary, and ensuring that changes are deployed in a controlled and organized manner.

### Deployment Strategies

Deployment strategies are in place to move the application between different environments seamlessly. The deployment process involves:

- **Development to Testing:** Changes developed in the development environment are deployed to the testing environment for thorough testing and validation.

- **Testing to Client Approval:** After successful testing, changes are submitted for client approval, involving stakeholders such as Ajay Abraham. Client feedback and approval are crucial steps in ensuring that the application meets business requirements.

- **Client Approval to Production:** Once client approval is obtained, changes are deployed to the production environment for end-user access.

### Solution Ownership

Ownership of the application's solution is established to ensure proper administration and management. The solution is owned by the PP_R2F_Users group **Owner**, which comprises administrators responsible for overseeing the application.

The structured ALM approach adopted by the **R2F Submission Tracker** ensures that changes are carefully managed, tested, and deployed, with client approval as an integral step. This process contributes to the overall reliability and stability of the application.

Please continue reading for more information on User Training and Special Functionalities in the following sections.

## 5. User Training

Effective user training is essential for ensuring that users can maximize the benefits of the **R2F Submission Tracker** and use it efficiently. Here are the key aspects of user training:

### Training Sessions

User training sessions are an integral part of onboarding and providing users with the knowledge and skills needed to use the application effectively. Training sessions can be scheduled based on user preferences and needs:

- **Scheduled Training:** Users have the flexibility to request scheduled training sessions. These sessions are designed to accommodate specific user groups and can be tailored to meet their requirements.

- **Live In-Person Sessions:** In addition to scheduled training, live in-person training sessions can be organized for each district or region. These sessions offer an opportunity for users to engage directly with trainers, ask questions, and receive personalized guidance.

### Access Control

Access to the application is controlled through user roles. The following roles are defined:

- **Standard Users:** Standard users have access to the application if they are members of the PP_R2F_Users group. They can view and update equipment data within their designated regions.

- **Administrators:** Administrators are responsible for overseeing the application and have elevated permissions. They are the owners of the PP_R2F_Users group and have access to equipment data across multiple regions.

### Training Materials

Comprehensive training materials, including user guides and documentation, are provided to users. These materials serve as valuable references and resources to support users in their day-to-day interactions with the application.

### Ongoing Support

For ongoing support, users can reach out to the designated support email address at [erwan.sudiman@sudiman.com](mailto:erwan.sudiman@halliburton.com) for assistance with queries, troubleshooting, and guidance.

The flexibility of scheduling training sessions, whether through scheduled sessions or live in-person training for each district can be requested.

Please continue reading for more information on Special Functionalities in the following section.
