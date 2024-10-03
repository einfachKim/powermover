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
- **Seamless Integration**: Compatible with all standard Dataverse tables used in Power Platform solutions.

## Solution Overview
Below is a comprehensive table outlining the components included in the solution:

| **Component Name**                                 | **Type**                  | **Purpose**                                                                                                         | **Connected Dataverse Tables**                        |
|----------------------------------------------------|--------------------------|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| Power Mover                                        | Canvas App               | Central interface for transferring multiple components at once.                                                    | Users, Canvas App, Process, Connection Reference, Environment Variable Definition |
| PowerMover \| Update Canvas App Owner              | Cloud Flow (Instant)     | Handles the ownership transfer of canvas apps with detailed error handling.                                        | Canvas App                                           |
| PowerMover \| Update Connection Reference Owner    | Cloud Flow (Instant)     | Manages ownership transition for connection references.                                                            | Connection Reference                                 |
| PowerMover \| Update Environment Variable Owner    | Cloud Flow (Instant)     | Updates ownership of environment variables.                                                                         | Environment Variable Definition                      |
| PowerMover \| Update Flow Owner                    | Cloud Flow (Instant)     | Transfers ownership of Cloud Flows while maintaining process integrity.                                             | Process (Flow)                                       |
| Power Mover \| Bulk Operation Spread Components    | Cloud Flow (Instant)     | Distributes bulk operations across child flows for parallel processing of components.                              | All Relevant Tables                                  |

## Prerequisites
- **Power Apps Premium License**: Required to use this solution since it involves accessing different Dataverse tables.
- **Environment Admin Permissions**: Necessary for managing solution transfers at an environment level.
- **Owner Permissions**: Ensure that the current owner has the appropriate permissions to delegate ownership.

## Installation Guide
1. **Import the solution** in the environment where you want to manage ownerships (recommended: DEV Environment).
2. **Activate all Cloud Flows** in the solution to ensure smooth operation.
3. **Run the Canvas App** named `Power Mover` to start using the solution.
   
> **Note**: After importing and configuring the solution, verify the connections to Dataverse and ensure that all required environment variables are properly defined.

## Configuration Details
After installation, ensure that the necessary permissions are granted to all users who need access to the solution components. Check that all flows have appropriate owners and permissions to execute.

## Usage Instructions
To transfer components:
1. Open the **Power Mover** Canvas App.
2. Select the components you want to transfer (Canvas Apps, Cloud Flows, Connection References, Environment Variables).
3. Click on the "Transfer" button and choose the new owner.
4. Monitor the status of each transfer using the app interface.

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

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing
We welcome contributions! Please read the [contributing guidelines](CONTRIBUTING.md) and submit a pull request with a clear description of your changes. Make sure to run tests and adhere to our coding standards.

## Frequently Asked Questions (FAQ)
- **Q: Can I transfer components across environments?**  
  A: No, the current version supports ownership transfers within the same environment only.
  
- **Q: What if I encounter a permission issue?**  
  A: Make sure you have the necessary roles and permissions for the Dataverse tables involved.
