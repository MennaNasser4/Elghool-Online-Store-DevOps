# Elghool Online Store — DevOps Documentation

## Project Information

**Project Name:** Elghool Online Store
**Role:** DevOps / Cloud Engineer
**Project Duration:** 4 Weeks
**Start Date:** 20 June 2026
**End Date:** 17 July 2026

---

# 1. Project Overview

Elghool Online Store is an e-commerce application designed to provide users with an online shopping experience.

The project consists of multiple components:

* React Web Frontend
* React Admin Dashboard
* .NET REST API Backend
* Mobile Application
* Microsoft Azure Cloud Infrastructure
* Database and cloud storage services
* Security and configuration management
* CI/CD and deployment workflows

As a DevOps/Cloud member, my responsibility was to prepare the cloud environment, deploy the application components, manage configuration, troubleshoot deployment and infrastructure issues, and prepare the deployment workflow.

---

# 2. My Role in the Project

My main responsibilities included:

* Designing the Azure deployment structure.
* Creating and configuring Azure resources.
* Preparing the Backend Azure App Service.
* Preparing the Frontend deployment environment.
* Configuring Azure SQL Database.
* Configuring Azure Blob Storage.
* Creating and configuring Azure Key Vault.
* Managing application configuration and secrets.
* Configuring Application Insights.
* Connecting GitHub repositories with Azure deployment workflows.
* Working with GitHub Actions for CI/CD.
* Troubleshooting Azure deployment errors.
* Troubleshooting application startup errors.
* Troubleshooting Blob Storage upload issues.
* Handling Azure SQL firewall configuration.
* Monitoring application behavior through Azure logs.
* Preparing project documentation.
* Preparing screenshots and deployment evidence.

---

# 3. Project Architecture

The general deployment architecture is:

```text
                         Users
                           |
                           v
                React Web Frontend
                           |
                           v
                    .NET REST API
                           |
          +----------------+----------------+
          |                |                |
          v                v                v
     Azure SQL       Azure Blob        Application
      Database         Storage           Insights
                           |
                           |
                      Azure Key Vault
```

For the frontend, the project contains two separate React applications:

```text
                 GitHub
                   |
          +--------+--------+
          |                 |
          v                 v
   User Frontend       Admin Dashboard
          |                 |
          v                 v
   Azure Static Web    Azure Static Web
       Apps                 Apps
          \                 /
           \               /
            +------v------+
                   |
              .NET API
             alghoul-api
```

---

# 4. Technologies and Tools

## Cloud

* Microsoft Azure
* Azure App Service
* Azure Static Web Apps
* Azure SQL Database
* Azure Blob Storage
* Azure Key Vault
* Azure Application Insights
* Azure Resource Groups

## Development / Deployment

* GitHub
* GitHub Actions
* .NET
* React
* Vite
* Node.js
* npm

## Operating Systems / Administration

* Windows
* Linux
* PowerShell
## Networking

* TCP/IP
* HTTP/HTTPS
* DNS
* Ports
* Firewall rules
* Azure networking

---

# 5. Azure Resources

The project infrastructure was organized under an Azure Resource Group.

Main resources used/planned for the project include:

| Resource              | Purpose                          |
| --------------------- | -------------------------------- |
| Resource Group        | Organize project resources       |
| Azure App Service     | Host the .NET REST API           |
| Azure Static Web Apps | Host React frontend applications |
| Azure SQL Database    | Store application data           |
| Azure Blob Storage    | Store uploaded images/assets     |
| Azure Key Vault       | Secure application secrets       |
| Application Insights  | Monitoring and diagnostics       |

---

# 6. Backend Deployment

The Backend is a .NET REST API.

The backend was deployed to Azure App Service.

Example API App Service:

```text
alghoul-api
```

The API is accessed through the Azure App Service URL.

The backend provides APIs for application functionality such as:

* Authentication
* Registration
* Login
* Branches
* Categories
* Other e-commerce operations

The frontend and mobile application communicate with the backend through the REST API.

---

# 7. Azure SQL Database

Azure SQL Database was prepared to host the application's relational data.

The backend uses a database connection string to communicate with Azure SQL.

The connection string is treated as sensitive information and should not be stored in:

* GitHub repositories
* README files
* Public documentation
* Screenshots
* Source code

The recommended configuration is through Azure App Service Application Settings and/or Azure Key Vault.

---

# 8. Azure Blob Storage

Azure Blob Storage was configured for storing application files such as category/product images.

The backend communicates with Blob Storage through its storage configuration.

The configuration contains:

```text
AzureBlobStorage
    ConnectionString
    ContainerName
```

The container is used to store uploaded assets.

### Important security consideration

Storage account keys and connection strings are sensitive credentials.

They must never be uploaded to GitHub or included in public documentation.

---

# 9. Azure Key Vault

Azure Key Vault was used/planned as the secure location for sensitive configuration.

Examples of sensitive configuration include:

* Database connection string
* Blob Storage connection string
* JWT signing key
* SendGrid API key
* Other application secrets

The application configuration can be connected to Key Vault through Azure App Service configuration and managed identity / Key Vault references.

The exact secret names must match the configuration expected by the backend application or be correctly mapped through App Service settings.

---

# 10. Application Configuration

The backend requires configuration values for different services.

Examples include:

```text
DefaultConnection
AzureBlobStorage__ConnectionString
AzureBlobStorage__ContainerName
Jwt__Key
SendGrid__ApiKey
Google__ClientId
```

The double underscore (`__`) is used by .NET configuration to represent nested configuration.

For example:

```text
AzureBlobStorage__ConnectionString
```

maps to:

```text
AzureBlobStorage:ConnectionString
```

Similarly:

```text
Jwt__Key
```

maps to:

```text
Jwt:Key
```

### Security Rule

Actual values are intentionally excluded from this documentation.

No passwords, API keys, connection strings, storage keys, or other credentials should be included in the GitHub repository.

---

# 11. Frontend Deployment

The project has two separate React applications:

### User Frontend

The application used by normal customers/users.

### Admin Dashboard

The application used for administrative operations.

Each frontend should have its own deployment configuration.

The expected deployment flow is:

```text
React Source Code
        |
        v
      GitHub
        |
        v
  GitHub Actions
        |
        v
    npm install
        |
        v
    npm run build
        |
        v
       dist
        |
        v
Azure Static Web Apps
```

For a Vite React application:

```text
Build Command:
npm run build

Output Directory:
dist
```

The actual environment-variable name for the backend API URL must match the variable used by the frontend code.

---

# 12. GitHub Integration

GitHub is used as the source-control platform.

The deployment architecture is intended to connect GitHub repositories with Azure.

Example:

```text
Developer
    |
    v
GitHub Repository
    |
    v
GitHub Actions
    |
    v
Build
    |
    v
Test
    |
    v
Deploy
    |
    v
Azure
```

This allows future changes pushed to the selected branch to trigger the deployment workflow automatically.

---

# 13. CI/CD

The intended CI/CD workflow is:

```text
Code Push
   ↓
GitHub
   ↓
GitHub Actions
   ↓
Install Dependencies
   ↓
Build Application
   ↓
Run Tests
   ↓
Publish Build
   ↓
Deploy to Azure
```

For the React frontend:

```text
npm install
npm run build
```

produces:

```text
dist/
```

which is then deployed to Azure Static Web Apps.

---

# 14. Errors and Troubleshooting

## 14.1 HTTP Error 500.30 — ASP.NET Core App Failed to Start

One of the encountered backend errors was:

```text
HTTP Error 500.30 - ASP.NET Core app failed to start
```

The Azure App Service displayed:

```text
The app failed to start
The app started but then stopped
The app started but threw an exception during startup
```

### Screenshot

The error was observed on the deployed backend App Service.

**Screenshot:**

`Screenshots/500-30-ASP.NET-Core-Startup-Failure.png`

### Meaning

HTTP 500.30 indicates that the ASP.NET Core application failed during startup.

Possible causes include:

* Application startup exception
* Incorrect application configuration
* Missing environment variables
* Incorrect connection strings
* Missing secrets
* Runtime mismatch
* Incorrect deployment configuration
* Application dependency failure
* Permission/configuration problems

### Troubleshooting

The following Azure diagnostic tools were used/considered:

* App Service Log Stream
* Application logs
* Azure deployment logs
* Application Insights
* Application configuration
* Runtime configuration

The important lesson from this issue was that a successful deployment does not necessarily mean that the application has started successfully.

The deployment must be followed by an application-health check.

---

# 15. Azure Blob Storage Upload Error

Another issue occurred while uploading files to Azure Blob Storage.

The backend stack trace pointed to:

```text
AzureBlobStorageService.UploadFileAsync
```

and the Blob SDK upload operation.

The error occurred during category creation when an image was being uploaded.

The relevant flow was:

```text
Create Category
      |
      v
Upload Image
      |
      v
AzureBlobStorageService
      |
      v
Azure Blob Storage
```

### Troubleshooting Areas

The following configuration areas were checked:

* Storage account
* Blob container
* Connection string
* Container name
* Storage access
* Application configuration
* Blob upload implementation

The issue demonstrated the importance of validating both:

1. Azure Storage configuration
2. Backend application configuration

---

# 16. Azure SQL Firewall Issue

Azure SQL Database uses firewall rules to control network access.

During development, the local/public IP address needed to be allowed to access the database.

A firewall rule was added for the current IP address.

### Important limitation

A home/public IP address can change.

Therefore, an IP-based firewall rule may stop working when the internet connection receives a new public IP.

Possible production approaches include:

* Controlled networking
* Private endpoints
* Azure networking
* Appropriate firewall rules
* Secure application-to-database connectivity

---

# 17. Azure App Service 64-bit Issue

An App Service configuration error was encountered:

```text
64 Bit worker processes cannot be used for the site as the plan does not allow it
```

### Cause

The selected App Service Plan did not support the requested 64-bit worker configuration.

### Resolution

The application/runtime configuration had to be aligned with the capabilities of the selected App Service Plan.

### Lesson

Azure App Service configuration options depend on the selected App Service Plan/SKU.

Before changing runtime settings, the capabilities and limitations of the selected plan should be checked.

---

# 18. Azure Subscription / Read-only Issue

An Azure subscription status issue was also encountered where Azure reported that the subscription was disabled/read-only.

This prevented write operations such as:

* Starting applications
* Modifying resources
* Creating resources
* Updating configurations

The issue was related to the subscription state rather than the application code itself.

The subscription status needed to be checked from:

```text
Azure Portal
→ Subscriptions
→ Subscription
→ Overview
```

---

# 19. Azure Region / Policy Issue

During resource creation, Azure policy restrictions were encountered for some regions.

The error was related to resource creation being disallowed by an Azure Policy.

### Lesson

The available Azure regions are not always unrestricted.

Resource creation can depend on:

* Subscription type
* Azure Policy
* Region availability
* Resource type
* Organization restrictions

When a region is rejected, another allowed region should be selected rather than repeatedly attempting the same configuration.

---

# 20. Monitoring and Logging

Application monitoring is important after deployment.

Azure Application Insights can be used for:

* Application monitoring
* Exceptions
* Requests
* Performance
* Availability
* Diagnostics

App Service Log Stream can also be used during troubleshooting.

The recommended troubleshooting process is:

```text
User reports problem
        ↓
Check application URL
        ↓
Check App Service status
        ↓
Open Log Stream
        ↓
Check application exception
        ↓
Check Configuration
        ↓
Check Azure dependency
        ↓
Apply fix
        ↓
Restart/redeploy
        ↓
Test again
```

---

# 21. Security Practices

Security was considered throughout the deployment process.

### Secrets should not be stored in:

* GitHub source code
* Public repositories
* README files
* Documentation
* Screenshots
* ZIP files

### Sensitive values include:

* Database passwords
* SQL connection strings
* Storage account keys
* Blob connection strings
* JWT signing keys
* SendGrid API keys
* Azure credentials

Azure Key Vault is the preferred solution for centralized secret management.

---

# 22. Project Timeline

The project duration was exactly four weeks.

**Start:** 20 June 2026
**End:** 17 July 2026

## Week 1 — 20 June → 26 June

Main activities:

* Understanding project architecture
* Understanding responsibilities
* Preparing DevOps/cloud plan
* Identifying required Azure resources
* Preparing the initial Azure environment
* Preparing the Resource Group
* Reviewing backend/frontend deployment requirements
* Planning GitHub integration

---

## Week 2 — 27 June → 3 July

Main activities:

* Azure App Service preparation
* Backend deployment preparation
* Azure SQL configuration
* Azure Blob Storage preparation
* Storage container configuration
* Initial application configuration
* Testing backend connectivity
* Investigating deployment/runtime issues

---

## Week 3 — 4 July → 10 July

Main activities:

* Azure Key Vault configuration
* Application configuration and secret management
* Application Insights preparation
* Backend troubleshooting
* Blob Storage troubleshooting
* SQL firewall configuration
* Investigation of App Service configuration issues
* GitHub/GitHub Actions deployment planning

---

## Week 4 — 11 July → 17 July

Main activities:

* Frontend deployment preparation
* React/Vite build configuration
* Static Web Apps deployment planning
* GitHub integration
* CI/CD preparation
* Final testing
* Troubleshooting remaining deployment issues
* Documentation
* Screenshots
* Project status review
* Preparing final submission materials

---

# 23. Project Status

## Completed / Implemented

The following DevOps/cloud tasks were worked on:

* Azure Resource Group
* Azure backend App Service
* Azure SQL Database
* Azure Blob Storage
* Blob container configuration
* Application configuration
* Key Vault setup
* Application monitoring setup/planning
* Backend deployment
* Azure troubleshooting
* SQL firewall configuration
* GitHub integration planning
* React frontend deployment preparation
* Static Web Apps deployment preparation
* CI/CD planning
* Documentation

## In Progress / Requires Final Verification

The following items require final verification before being marked completely finished:

* Final automated CI/CD pipeline validation
* Final User Frontend Static Web App deployment
* Final Admin Dashboard Static Web App deployment
* Final end-to-end testing
* Final production configuration
* Final custom domain configuration

---

# 24. Remaining Work

The recommended remaining deployment sequence is:

```text
1. Finalize Frontend Repository
        ↓
2. Create Static Web App
        ↓
3. Connect Frontend GitHub Repository
        ↓
4. Configure React/Vite Build
        ↓
5. Deploy User Frontend
        ↓
6. Test Frontend
        ↓
7. Create Dashboard Static Web App
        ↓
8. Connect Dashboard Repository
        ↓
9. Deploy Dashboard
        ↓
10. Connect both to Backend API
        ↓
11. End-to-End Testing
        ↓
12. Configure Domain (optional)
```

---

# 25. Documentation and Evidence

The documentation should contain screenshots showing actual work and encountered errors.

Recommended structure:

```text
Screenshots/
├── 01-Azure-Resource-Group.png
├── 02-App-Service.png
├── 03-Azure-SQL.png
├── 04-Blob-Storage.png
├── 05-Blob-Container.png
├── 06-Key-Vault.png
├── 07-Application-Insights.png
├── 08-GitHub.png
├── 09-GitHub-Actions.png
├── 10-500-30-ASP.NET-Core-Startup-Failure.png
├── 11-Blob-Upload-Error.png
├── 12-SQL-Firewall.png
└── 13-Static-Web-App.png
```

Only screenshots that actually exist should be included.

---

# 26. Repository Structure

The DevOps repository can be organized as:

```text
Elghool-Online-Store-DevOps/
│
├── README.md
│
├── Documentation/
│   └── PROJECT-DOCUMENTATION.md
│
├── Screenshots/
│   ├── Azure/
│   ├── Deployment/
│   ├── Errors/
│   └── GitHub/
│
├── Azure/
│   ├── App-Service/
│   ├── SQL/
│   ├── Blob-Storage/
│   ├── Key-Vault/
│   └── Application-Insights/
│
├── CI-CD/
│   └── GitHub-Actions/
│
└── Scripts/
```

---

# 27. What Must NOT Be Uploaded

Before pushing the repository or preparing the ZIP file, verify that none of the following are included:

```text
.env
.env.local
appsettings.Production.json
connection strings
passwords
API keys
JWT secrets
Azure storage keys
Azure credentials
publish profiles
client secrets
```

If a configuration file contains real credentials, replace them with placeholders before uploading.

Example:

```text
DefaultConnection=<REDACTED>
AzureBlobStorage__ConnectionString=<REDACTED>
Jwt__Key=<REDACTED>
SendGrid__ApiKey=<REDACTED>
```

---

# 28. Final Submission ZIP

The final ZIP should contain the work available at the stopping point.

Recommended structure:

```text
Elghool-Online-Store-DevOps-Submission/
│
├── Source-Code/
│
├── Documentation/
│   └── PROJECT-DOCUMENTATION.pdf
│
├── Screenshots/
│
└── README.md
```

The ZIP must be checked carefully to make sure no credentials or secrets are included.

---

# 29. Final Project Deliverables

The final DevOps submission consists of:

### 1. GitHub Repository

A dedicated repository for the DevOps work.

### 2. README

The README should provide:

* Project overview
* Architecture
* Technologies
* DevOps responsibilities
* Azure resources
* Deployment process
* Screenshots
* Project status
* Repository information
* Documentation link

### 3. Detailed Documentation

The documentation contains:

* Project overview
* Architecture
* DevOps responsibilities
* Azure infrastructure
* Deployment process
* Configuration
* Errors
* Troubleshooting
* Security
* Timeline
* Completed work
* Remaining work
* Sources
* Screenshots

### 4. ZIP File

Contains the code at the current stopping point, documentation, and screenshots.

### 5. 3-Minute Project Video

The video should present the project as a standalone project rather than explaining code line by line.

The presentation should cover:

```text
Project idea
   ↓
Architecture
   ↓
Frontend
   ↓
Backend
   ↓
Database / Storage
   ↓
DevOps / Azure
   ↓
Deployment
   ↓
Result
```

The video should focus on:

* What the project does
* What each component does
* How the components communicate
* What was implemented
* What challenges were encountered
* How the project was built within the available four-week period

---

# 30. Conclusion

The DevOps work focused on preparing a cloud-based deployment environment for Elghool Online Store using Microsoft Azure and GitHub.

The project involved application hosting, database services, cloud storage, secret management, monitoring, troubleshooting, and CI/CD preparation.

Several real deployment and infrastructure issues were encountered during implementation, including ASP.NET Core startup failures, Blob Storage upload issues, SQL firewall restrictions, App Service plan limitations, Azure subscription restrictions, and Azure policy/region limitations.

Documenting these issues and their troubleshooting process is an important part of the project because it demonstrates not only the final deployment but also the practical DevOps problem-solving process used to reach it.

**Project Duration:** 20 June 2026 → 17 July 2026
**Total Duration:** 4 Weeks

