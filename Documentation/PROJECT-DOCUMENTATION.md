# Elghool Online Store — DevOps Documentation

**Project:** Elghool Online Store
**Role:** DevOps / Cloud Engineer
**Duration:** 4 Weeks
**Start Date:** 20 June 2026
**End Date:** 17 July 2026

**GitHub Repository:** Elghool Online Store — DevOps

---

## 1. Project Overview

Elghool Online Store is an e-commerce application consisting of:

* React Web Frontend
* React Admin Dashboard
* .NET REST API
* Mobile Application
* Azure Cloud Infrastructure
* Azure SQL Database
* Azure Blob Storage
* Azure Key Vault
* Application Insights
* GitHub / GitHub Actions

My role focused on preparing the cloud infrastructure, deploying the backend, preparing frontend deployment, managing application configuration and secrets, troubleshooting Azure issues, and preparing the CI/CD workflow.

---

## 2. DevOps Responsibilities

My main responsibilities included:

* Designing the Azure deployment architecture.
* Creating and configuring Azure resources.
* Deploying the .NET REST API using Azure App Service.
* Preparing React frontend deployment using Azure Static Web Apps.
* Configuring Azure SQL Database.
* Configuring Azure Blob Storage and containers.
* Creating and configuring Azure Key Vault.
* Managing application secrets and configuration.
* Configuring Application Insights and monitoring.
* Integrating GitHub with Azure.
* Preparing GitHub Actions CI/CD workflows.
* Troubleshooting deployment and startup issues.
* Troubleshooting Blob Storage and SQL connectivity issues.
* Configuring SQL firewall access.
* Preparing documentation and deployment evidence.

---

## 3. Project Architecture

```text
                         Users
                           |
             +-------------+-------------+
             |                           |
             v                           v
      React Web Frontend          Admin Dashboard
             |                           |
             +-------------+-------------+
                           |
                           v
                     .NET REST API
                    Azure App Service
                           |
             +-------------+-------------+
             |             |             |
             v             v             v
        Azure SQL     Azure Blob    Application
        Database       Storage       Insights
                           |
                           v
                     Azure Key Vault
```

The backend API acts as the main communication layer between the frontend/mobile applications and Azure services.

---

## 4. Technologies

### Azure

* Azure App Service
* Azure Static Web Apps
* Azure SQL Database
* Azure Blob Storage
* Azure Key Vault
* Azure Application Insights
* Azure Resource Groups

### Development & CI/CD

* GitHub
* GitHub Actions
* Git
* .NET
* React
* Vite
* Node.js
* npm
* Docker

### Administration & Networking

* Windows
* Linux
* PowerShell
* Bash
* HTTP/HTTPS
* TCP/IP
* DNS
* Firewall Rules

---

## 5. Azure Infrastructure

The project infrastructure was organized within an Azure Resource Group.

| Resource             | Purpose                    |
| -------------------- | -------------------------- |
| Resource Group       | Organize project resources |
| App Service          | Host the .NET REST API     |
| Static Web Apps      | Host React applications    |
| Azure SQL            | Application database       |
| Blob Storage         | Store images and assets    |
| Key Vault            | Secure application secrets |
| Application Insights | Monitoring and diagnostics |

---

## 6. Backend Deployment

The .NET REST API was deployed to Azure App Service.

The backend provides APIs for core e-commerce functionality, including:

* Authentication
* Registration
* Login
* Branches
* Categories
* Other application operations

The frontend and mobile application communicate with the backend through the REST API.

---

## 7. Azure SQL Database

Azure SQL Database was used as the relational database for the application.

The backend uses a database connection string to connect to Azure SQL.

Sensitive database information must not be stored in:

* GitHub repositories
* Source code
* README files
* Screenshots
* Public documentation

The recommended approach is to manage the connection string through Azure App Service configuration and Azure Key Vault.

---

## 8. Azure Blob Storage

Azure Blob Storage was configured to store uploaded application assets such as category and product images.

The backend uses:

```text
AzureBlobStorage
    ConnectionString
    ContainerName
```

The storage connection string and account keys are sensitive credentials and must never be committed to GitHub.

---

## 9. Azure Key Vault & Configuration

Azure Key Vault was used to securely manage sensitive application configuration.

Examples include:

```text
DefaultConnection
AzureBlobStorage__ConnectionString
AzureBlobStorage__ContainerName
Jwt__Key
SendGrid__ApiKey
Google__ClientId
```

In .NET configuration, double underscores represent nested configuration sections.

For example:

```text
AzureBlobStorage__ConnectionString
```

maps to:

```text
AzureBlobStorage:ConnectionString
```

Actual secret values are intentionally excluded from this documentation.

---

## 10. Frontend Deployment

The project contains two React applications:

* User Frontend
* Admin Dashboard

The expected deployment process is:

```text
GitHub Repository
       ↓
GitHub Actions
       ↓
npm install
       ↓
npm run build
       ↓
dist/
       ↓
Azure Static Web Apps
```

For the Vite React applications:

```text
Build Command:
npm run build

Output Directory:
dist
```

The frontend applications communicate with the backend through the deployed API URL.

---

## 11. GitHub & CI/CD

GitHub was used as the source-control platform and as the foundation for the deployment workflow.

The intended CI/CD process is:

```text
Code Push
   ↓
GitHub
   ↓
GitHub Actions
   ↓
Install Dependencies
   ↓
Build
   ↓
Test
   ↓
Deploy
   ↓
Azure
```

This workflow allows future code changes to be automatically built and deployed after being pushed to the configured branch.

---

## 12. Monitoring & Troubleshooting

Azure Application Insights and App Service Log Stream were used/planned for application monitoring and troubleshooting.

The general troubleshooting process was:

```text
Problem
   ↓
Check Application URL
   ↓
Check App Service Status
   ↓
Check Log Stream
   ↓
Check Configuration
   ↓
Check Azure Dependencies
   ↓
Apply Fix
   ↓
Restart / Redeploy
   ↓
Test Again
```

---

## 13. Main Issues Encountered

### HTTP 500.30 — ASP.NET Core Startup Failure

The backend encountered:

```text
HTTP Error 500.30 - ASP.NET Core app failed to start
```

Possible causes investigated included:

* Missing configuration
* Incorrect environment variables
* Missing secrets
* Runtime/deployment mismatch
* Startup exceptions
* Azure dependency issues

The issue highlighted the importance of checking application logs and configuration after deployment.

---

### Azure Blob Storage Upload Issue

An issue occurred during image upload through:

```text
AzureBlobStorageService.UploadFileAsync
```

The troubleshooting focused on:

* Storage account configuration
* Container name
* Connection string
* Application configuration
* Storage access
* Backend implementation

---

### Azure SQL Firewall

Azure SQL firewall rules were configured to allow required development access.

Because public IP addresses can change, IP-based access should be carefully managed, and production environments should use more controlled networking where appropriate.

---

### App Service Plan Limitation

An App Service configuration issue occurred because the selected plan did not support 64-bit worker processes.

This demonstrated that Azure configuration options depend on the selected App Service Plan/SKU.

---

### Azure Policy / Region Restrictions

Some Azure resource creation attempts were restricted by Azure Policy or regional availability.

The solution was to use an allowed configuration/region supported by the subscription.

---

## 14. Security Practices

Security was considered throughout the deployment process.

The following must never be committed to GitHub:

```text
.env
.env.local
Passwords
Connection Strings
API Keys
JWT Secrets
Storage Keys
Azure Credentials
Publish Profiles
Client Secrets
```

Sensitive values should be managed using Azure Key Vault and appropriate Azure application configuration.

Before pushing the repository, all configuration files should be checked for credentials.

---

## 15. Project Timeline

### Week 1 — 20 June → 26 June

* Understand project architecture
* Define DevOps responsibilities
* Prepare Azure environment
* Create Resource Group
* Review deployment requirements
* Plan GitHub integration

### Week 2 — 27 June → 3 July

* Prepare App Service
* Deploy backend
* Configure Azure SQL
* Configure Blob Storage
* Configure storage container
* Test backend connectivity

### Week 3 — 4 July → 10 July

* Configure Key Vault
* Manage application secrets
* Prepare Application Insights
* Troubleshoot backend
* Troubleshoot Blob Storage
* Configure SQL firewall
* Investigate App Service issues

### Week 4 — 11 July → 17 July

* Prepare frontend deployment
* Configure React/Vite build
* Prepare Static Web Apps
* Integrate GitHub
* Prepare CI/CD
* Perform final testing
* Document the project
* Prepare screenshots and final submission

---

## 16. Project Status

### Implemented / Worked On

* Azure Resource Group
* Backend Azure App Service
* Azure SQL Database
* Azure Blob Storage
* Blob Container
* Azure Key Vault
* Application configuration
* Application monitoring
* Backend deployment
* SQL firewall configuration
* GitHub integration
* Frontend deployment preparation
* Static Web Apps preparation
* CI/CD preparation
* Troubleshooting and documentation

### Final Verification

The following should be verified before the project is considered fully production-ready:

* Automated CI/CD pipeline
* User Frontend deployment
* Admin Dashboard deployment
* End-to-end frontend/API testing
* Production configuration
* Optional custom domain

---

## 17. Final Deployment Flow

```text
Developer
    ↓
GitHub
    ↓
GitHub Actions
    ↓
Build & Test
    ↓
Azure
    ↓
React Frontend
    ↓
.NET REST API
    ↓
Azure SQL + Blob Storage
    ↓
Key Vault + Application Insights
```

---

## 18. Documentation & Evidence

Screenshots should be included only when they represent actual project work.

Recommended evidence:

```text
Screenshots/
├── Azure/
├── Deployment/
├── Errors/
└── GitHub/
```

Examples of useful evidence:

* Azure Resource Group
* App Service
* Azure SQL
* Blob Storage
* Blob Container
* Key Vault
* Application Insights
* GitHub Repository
* GitHub Actions
* 500.30 Error
* Blob Upload Error
* SQL Firewall
* Static Web App

---

## 19. Final Submission

The final submission should contain:

```text
Elghool-Online-Store-DevOps-Submission/
│
├── Documentation/
│   └── PROJECT-DOCUMENTATION.pdf
│
├── Screenshots/
│
├── README.md
│
└── Source-Code/
```

Before creating the final ZIP, the repository and files must be checked to ensure that no credentials or secrets are included.

---

## 20. Sources & References

The following resources were used as references during the project:

1. YouTube — Azure / DevOps reference
2. YouTube — Azure App Service reference
3. YouTube — Azure deployment reference
4. Microsoft Learning GitHub
5. Microsoft Azure Developer Exercises
6. YouTube — Azure development reference
7. Microsoft Learning — AZ-204
8. YouTube — Azure reference
9. Microsoft Learn — App Service Environment
10. Microsoft Learn — .NET Core App Service Quickstart

---

## Conclusion

The DevOps work focused on preparing a cloud deployment environment for Elghool Online Store using Microsoft Azure and GitHub.

The work covered application hosting, database and storage services, secret management, monitoring, GitHub integration, CI/CD preparation, and troubleshooting.

Several real-world deployment issues were encountered, including ASP.NET Core startup failures, Blob Storage upload problems, SQL firewall restrictions, App Service plan limitations, subscription restrictions, and Azure Policy limitations.

These issues provided practical experience in diagnosing and resolving cloud deployment problems and demonstrated the importance of monitoring, secure configuration management, and systematic troubleshooting.

**Project Duration:** 20 June 2026 → 17 July 2026
**Total Duration:** 4 Weeks


