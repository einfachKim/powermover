# Power Mover

![Version](https://img.shields.io/badge/version-1.0-blue) ![License](https://img.shields.io/badge/license-MIT-green)

## Description
**Power Mover** is a Power Platform solution designed to streamline the management of ownership transitions for Power Platform components, including canvas apps, cloud flows, connection references, and environment variables. It is designed for handling joiner, mover, and leaver scenarios, ensuring that solutions remain operational even when the original maker is no longer involved.

### Why Use Power Mover?
- **Batch Transfers**: Transfer multiple components with a single click.
- **Error Handling**: Built-in try/catch scopes for reliable component transfer.
- **Flexible Scenarios**: Manage ownership transitions for both individual makers and collaborative projects.

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
- **Multi-Select Transfer**: Choose individual components or use the multi-select option to transfer all necessary components at once.
- **Comprehensive Error Handling**: Built-in error handling using try/catch scopes ensures reliable and predictable component transfer.
- **Seamless Integration**: Uses only standard Dataverse tables where named components (apps, flows, connection references and environment variables) are stored.

## Solution Overview
Below is a comprehensive table outlining the components included in the solution:

| **Component Name**                                 | **Type**                  | **Purpose**                                                                                                         | **Connected Dataverse Tables**                        |
|----------------------------------------------------|--------------------------|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| Power Mover                                        | Canvas App               | Central interface for transferring multiple components at once.                                                    | Users, Canvas App, Process, Connection Reference, Environment Variable Definition |
| PowerMover \| Update Canvas App Owner              | Cloud Flow (Instant)     | Handles the ownership transfer of canvas apps with error handling.                                                 | Canvas App                                           |
| PowerMover \| Update Connection Reference Owner    | Cloud Flow (Instant)     | Manages ownership transition for connection referencewith error handling.                                          | Connection Reference                                 |
| PowerMover \| Update Environment Variable Owner    | Cloud Flow (Instant)     | Updates ownership of environment variables with error handling.                                                    | Environment Variable Definition                      |
| PowerMover \| Update Flow Owner                    | Cloud Flow (Instant)     | Transfers ownership of Cloud Flows with error handling.                                                            | Process (Flow)                                       |
| Power Mover \| Bulk Operation Spread Components    | Cloud Flow (Instant)     | Serves as parent flow for the bulk transfer and receives the collection ‘colTransferComponents’ as JSON and triggers the child flow above depending on the component type.                              | No direct connection. Triggers child flows.                                  |

## Prerequisites
- **Power Apps Premium License**: Required to use this solution since it involves accessing different Dataverse tables.
- **Owner Permissions**: The user using the apps needs to own components he wants to transfer or must be at least system customizer or system administrator to transfer components owned by other users.

## Installation Guide
1. **Import the solution** in the environment where you want to manage ownerships (recommended: DEV Environment).
2. **Activate all Cloud Flows** in the solution to ensure smooth operation.
3. **Run the Canvas App** named `Power Mover` to start using the solution.


## Usage Instructions
To transfer a single component:
1. Open the **Power Mover** Canvas App.
2. Select the component you want to transfer using the pen-icon (Canvas Apps, Cloud Flows, Connection References, Environment Variables).
3. Click on the "Transfer" button and choose the new owner.
4. For Power Apps Canvas Apps: Select if the current owner shall be co-owner after the transfer
5. Monitor the status of the selected component in the app interface.
6. Expected Result: Owner of the component has changed


To transfer a multiple component:
1. Open the **Power Mover** Canvas App.
2. Use the checkboxes to select multiple components that you want to transfer (Canvas Apps, Cloud Flows, Connection References, Environment Variables).
3. Use the bulk select checkbox at the left top of each table to select all components currently shown in the table
4. At the bottom of the table you can empty the basket with components, see the total items count of components or click "Transfer Components" to move on transferring all selected components.
5. For Power Apps Canvas Apps: Select if the current owner shall be co-owner after the transfer
6. Click on the "Transfer" button and choose the new owner.
7. Monitor the status of each transfer using the app interface.
8. Expected Result: Owner of all components that you have selected has changed

## Demo Video
For a detailed walkthrough of the solution and a demo of the transfer process, check out our [YouTube Demo Video](https://www.youtube.com/watch?v=YOUR_VIDEO_LINK).

## Use Cases
- **Project Deployment**:  
  Several makers work together on a solution. For the transition to the TEST and PROD environment, the solution should be transferred to one of the makers or a service account in the DEV environment. This ensures that a single owner is designated for future maintenance and deployment activities.
  
- **Maker Offboarding**:  
  A maker leaves the company and is the owner of a solution in the DEV environment (TEST and PROD are owned by the service principal). The solution must be transferred to a colleague who will own the solution in the future, ensuring no disruptions in ownership and operation.
  
- **Maker Moves to Another Department**:  
  A maker is transferred to another department and is no longer involved in the development of certain solutions. To reflect the organizational change, the ownership of all solutions they developed is transitioned to a colleague within the same team or to a new owner in the current department.

## Version History / Changelog
- **03.10.24** - Release of the first version to transfer apps, flows, connection references, and environment variables.

## Contact Information
For any questions, feedback, or issues, feel free to reach out:

- **Email**: [kim@ema-sh.de](mailto:kim@ema-sh.de)
- **LinkedIn**: [Kim Buske on LinkedIn](https://www.linkedin.com/in/kim-buske/)

## Frequently Asked Questions (FAQ)
- **Q: Can I select multiple componentes and then transfer these components to multiple owners?**  
  A: No, the current version supports ownership transfers to one new owner for one or mulitple components.
  
- **Q: Can I see components of multiple environments?  
  A: No, the current version only displays all components from the current environment (where the solution is installed)
