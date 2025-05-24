# Power Mover

![Version](https://img.shields.io/badge/version-1.1-blue) ![License](https://img.shields.io/badge/license-MIT-green)

## Description
**Power Mover** is a Power Platform solution designed to streamline the management of ownership transitions for Power Platform components, including canvas apps, cloud flows, connection references, and environment variables. It is designed for handling joiner, mover, and leaver scenarios, ensuring that solutions remain operational even when the original maker is no longer involved.

### Why Use Power Mover?
- **Batch Transfers**: Transfer multiple components with a single click.
- **Error Handling**: Built-in try/catch scopes for reliable component transfer.
- **Flexible Scenarios**: Manage ownership transitions and access rights for both individual makers and collaborative projects.

## Table of Contents
1. [Description](#description)
2. [Features](#features)
3. [Solution Overview](#solution-overview)
4. [Prerequisites](#prerequisites)
5. [Installation Guide](#installation-guide)
6. [Configuration Details](#configuration-details)
7. [Usage Instructions](#usage-instructions)
8. [Demo Video](#demo-video)
9. [Use Cases](#use-cases)
10. [Version History / Changelog](#version-history--changelog)
11. [Contact Information](#contact-information)
12. [License](#license)
13. [Contributing](#contributing)
14. [Frequently Asked Questions (FAQ)](#frequently-asked-questions-faq)

## Features
Power Mover includes the following key features:

- **Ownership Transition**: Easily transfer ownership of canvas apps, cloud flows, connection references, and environment variables.
- **Share Connection References**: Share any connection reference with another user with precise access control (Read, Write, Delete, Append, AppendTo, Assign, Share).
- **Revoke Access**: Remove access rights from individual users for any connection reference.
- **Access Transparency**: See exactly which users have what kind of access to a specific connection reference.
- **Multi-Select Transfer**: Choose individual components or use the multi-select option to transfer all necessary components at once.
- **Comprehensive Error Handling**: Built-in error handling using try/catch scopes ensures reliable and predictable component transfer.
- **Seamless Integration**: Uses only standard Dataverse tables where named components are stored (apps, flows, connection references, environment variables).

## Solution Overview

Below is a comprehensive table outlining the components included in the solution:

| **Component Name**                                              | **Type**               | **Purpose**                                                                                                                      | **Connected Dataverse Tables**                                     |
|------------------------------------------------------------------|------------------------|----------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| PowerMover - Manage Ownerships                                   | Canvas App             | Central UI for managing ownership and access for all supported component types                                                  | Users, Canvas App, Process, Connection Reference, Environment Variable Definition |
| PowerMover \| List People with Access to Connection Reference    | Cloud Flow (Instant)   | Lists all users who have access to a given connection reference including access rights                                         | principalobjectaccess, systemuser                                  |
| PowerMover \| Share Connection Reference with a Person           | Cloud Flow (Instant)   | Shares a connection reference with a specific user and defined access level                                                     | connectionreference                                                 |
| PowerMover \| Revoke Access to Connection Reference for a Person | Cloud Flow (Instant)   | Revokes all access for a user from a specific connection reference                                                              | principalobjectaccess                                               |
| PowerMover \| Update Canvas App Owner                            | Cloud Flow (Instant)   | Transfers ownership of a Canvas App                                                                                             | canvasapp                                                           |
| PowerMover \| Update Connection Reference Owner                  | Cloud Flow (Instant)   | Transfers ownership of a Connection Reference                                                                                   | connectionreference                                                 |
| PowerMover \| Update Environment Variable Definition Owner       | Cloud Flow (Instant)   | Transfers ownership of an Environment Variable                                                                                  | environmentvariabledefinition                                       |
| PowerMover \| Update Flow Owner                                  | Cloud Flow (Instant)   | Transfers ownership of a Cloud Flow                                                                                              | workflow / process                                                  |

## Prerequisites
- **Power Apps Premium License**: Required to use this solution since it involves accessing different Dataverse tables.
- **Owner Permissions**: The user using the apps needs to own components they want to transfer or must be at least a system customizer or system administrator to transfer components owned by other users.

## Installation Guide
1. **Import the solution** in the environment where you want to manage ownerships (recommended: DEV Environment).
2. **Activate all Cloud Flows** in the solution to ensure smooth operation.
3. **Run the Canvas App** named `Power Mover` to start using the solution.
4. **Recommended**: Create a Dataverse View for the `systemuser` table, which is used within the Combobox for 'New Owner', and use this view in the Combobox rather than querying the entire table.

## Configuration Details
No additional configuration required. Make sure all flows have correct connections configured after import.

## Usage Instructions

### To transfer a single component:
![til](https://i.imgur.com/A7iwJcP.gif)
1. Open the **Power Mover** Canvas App.
2. Select the component you want to transfer using the pen-icon.
3. Click on the "Transfer" button and choose the new owner.
4. For Canvas Apps: Select if the current owner shall remain co-owner.
5. Monitor the status in the app interface.

### To transfer multiple components:
![til](https://i.imgur.com/cx89tFD.gif)
1. Open the **Power Mover** Canvas App.
2. Use the checkboxes to select multiple components.
3. Use the bulk checkbox to select all visible items.
4. At the bottom, click "Transfer Components" to proceed.
5. Choose the new owner and confirm.
6. Monitor the progress in the UI.

## Demo Video
Check out our [YouTube Demo Video](https://www.youtube.com/watch?v=YTRn53FgTJI) for a walkthrough.

## Use Cases

- **Project Deployment**: Transfer ownership during stage transitions (e.g. from DEV to TEST).
- **Maker Offboarding**: Reassign ownership when a maker leaves the company.
- **Internal Role Change**: Adjust ownership when a maker moves to a new department.

## Version History / Changelog

- **24.05.25** – Major feature update:
  - Introduced the ability to share connection references with specific users and multiple access levels.
  - Added flows to revoke access and to list users with current access on a reference.
- **03.10.24** – Initial release with ownership transfer for apps, flows, connection references, and environment variables.

## Contact Information
For any questions or feedback:

- **Email**: [kim@ema-sh.de](mailto:kim@ema-sh.de)
- **LinkedIn**: [Kim Buske on LinkedIn](https://www.linkedin.com/in/kim-buske/)

## License
MIT

## Contributing
Pull requests welcome. For larger changes, please open an issue first.

## Frequently Asked Questions (FAQ)

- **Q: Can I transfer components to multiple new owners?**  
  A: No, one transfer action supports assigning a single new owner at a time.

- **Q: Can I view components from multiple environments?**  
  A: No, only components from the current environment are shown.

- **Q: Why are not all users visible in the 'New Owner' dropdown?**  
  A: Use a filtered view of the `systemuser` table to improve performance. [Video explanation](https://www.youtube.com/watch?v=eKygMP7ySR8)
