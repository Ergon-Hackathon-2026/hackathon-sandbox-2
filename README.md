[README.md](https://github.com/user-attachments/files/26166761/README.md)
QueryVault is a Salesforce internal productivity tool designed for Admins, Developers, and QA Engineers. It provides a centralized, secure repository for storing, sharing, and validating frequently used SOQL queries, eliminating the need for hardcoding, local text files, or "sticky note" code snippets.



The application is built on a custom object: Useful\_Query\_\_c, also standardly known as Useful Query.



The application gives internal users the ability to create, read, edit, and delete query records and easily reference them at a later time.



The architecture of the QueryVault application is made in a metadata-driven design. At its core, the system utilizes Dynamic Schema Discovery via Schema.getGlobalDescribe() to populate the SObjectApiName\_\_c field, ensuring the app remains environment-agnostic by identifying all standard and custom objects within the entire Salesforce org. Therefore, there is no hardcoded limitations within the tool. When a user submits a query for validation, the Apex controller validates the input and programmatically appends a LIMIT clause. This injection ensures that the database engine only performs a syntax and accessibility check on a single row, effectively preventing long running queries from crippling servers.



Security within the application follows the Principle of Least Privilege and is enforced at multiple layers of the Salesforce stack. All Apex controllers are defined using the with sharing keyword to strictly respect the Org-Wide Defaults (OWD), which are set to Private to ensure data isolation. Access is then selectively granted through granular Permission Sets—QueryVault\_Editor for full administrative control and QueryVault\_Viewer for read-only interactions—rather than modifying broad user profiles. On the front end, the Lightning Web Components (LWC) utilize Lightning Data Service (LDS) to provide a reactive, secure, and seamless user experience. By combining these technical strategies, QueryVault provides a professional-grade tool that will allow developers to work quicker and more effectively.

