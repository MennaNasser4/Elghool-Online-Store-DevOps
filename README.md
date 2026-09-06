# Elghool-Online-Store-DevOps
DevOps infrastructure, cloud deployment, CI/CD, monitoring, and Azure services for the Elghool Online Store project.

## Project Overview

**Elghool Online Store** is an e-commerce platform designed to provide a complete online shopping experience through a web frontend, RESTful backend API, and mobile application.

This repository contains the **DevOps and Cloud Infrastructure** work for the project, including cloud deployment, infrastructure configuration, storage, database connectivity, monitoring, security, and deployment-related troubleshooting.

---

## 🏗️ Project Architecture

```text
                    ┌──────────────────┐
                    │   React Frontend │
                    │      (Web)       │
                    └────────┬─────────┘
                             │
                             │ REST API
                             ▼
                    ┌──────────────────┐
                    │   .NET Web API   │
                    │  Azure App       │
                    │     Service      │
                    └───────┬──────────┘
                            │
                ┌───────────┼───────────┐
                ▼           ▼           ▼
        ┌────────────┐ ┌──────────┐ ┌───────────────┐
        │ Azure SQL  │ │   Blob   │ │ Key Vault     │
        │ Database   │ │ Storage  │ │   Secrets     │
        └────────────┘ └──────────┘ └───────────────┘
                            │
                            ▼
                    ┌──────────────────┐
                    │ Application      │
                    │ Insights         │
                    │ Monitoring       │
                    └──────────────────┘
```

---

## ☁️ Cloud & DevOps Services

| Service              | Purpose                  |
| -------------------- | ------------------------ |
| Microsoft Azure      | Cloud platform           |
| Azure App Service    | Backend API hosting      |
| Azure SQL Database   | Application database     |
| Azure Blob Storage   | Image/file storage       |
| Azure Key Vault      | Secure secret management |
| Application Insights | Application monitoring   |
| Azure Resource Group | Resource organization    |
| GitHub               | Source control           |
| GitHub Actions       | CI/CD automation         |
| Postman              | API testing              |

---

## 🚀 DevOps Responsibilities

The DevOps part of the project includes:

* Azure cloud infrastructure setup
* Resource Group configuration
* Backend deployment
* Application hosting
* Database configuration
* Blob Storage configuration
* Secure configuration and secret management
* Application monitoring
* Logging and diagnostics
* CI/CD preparation and deployment
* Troubleshooting Azure deployment issues
* Network and firewall configuration
* Cost and resource management

---

## 🔐 Security

Security considerations implemented during the project include:

* Storing sensitive configuration outside the source code
* Using Azure Key Vault for secrets
* Avoiding committing credentials and connection strings to GitHub
* Configuring Azure resource access
* Configuring SQL Server firewall rules
* Managing Blob Storage access
* Monitoring application failures and errors

> **Note:** No production secrets, credentials, API keys, or connection strings are stored in this repository.

---

## 📊 Monitoring

**Azure Application Insights** was configured for application monitoring and troubleshooting.

Monitoring was used to investigate:

* Application failures
* HTTP errors
* Exceptions
* Failed dependencies
* Application performance
* Backend runtime issues

---

## 🧪 Testing & Troubleshooting

Several deployment and infrastructure issues were encountered and investigated during the project.

Examples include:

### Azure Region Policy

Some Azure regions were rejected because of subscription-level deployment policies.

### App Service Architecture

An App Service deployment initially encountered a worker-process architecture limitation:

```text
64 Bit worker processes cannot be used for the site as the plan does not allow it.
```

The App Service configuration was adjusted according to the available plan capabilities.

### ASP.NET Core Startup Error

The deployed API encountered:

```text
HTTP Error 500.30 - ASP.NET Core app failed to start
```

Application logs and Application Insights were used to investigate the startup failure.

### Azure Blob Storage

The backend encountered an error while uploading category images to Azure Blob Storage.

The investigation included:

* Storage Account configuration
* Blob Container configuration
* Storage permissions
* Connection configuration
* Blob upload behavior
* Application logs

### Azure SQL Firewall

The backend/database team encountered an IP access issue:

```text
Your client IP address does not have access to the server.
```

The SQL Server firewall configuration was reviewed and updated to allow the required client IP address.

---

## 📅 Project Timeline

**Project Duration:** 4 Weeks

**Start Date:** 20 June 2026

**End Date:** 17 July 2026

### Week 1 — 20 June → 26 June

* Azure environment preparation
* Resource Group setup
* Initial cloud architecture
* Initial application infrastructure
* GitHub/project preparation

### Week 2 — 27 June → 3 July

* Backend hosting preparation
* Azure SQL configuration
* Blob Storage configuration
* API deployment and testing
* Initial troubleshooting

### Week 3 — 4 July → 10 July

* Application monitoring
* Application Insights
* Key Vault configuration
* Access and security configuration
* Infrastructure troubleshooting

### Week 4 — 11 July → 17 July

* Deployment troubleshooting
* Final infrastructure configuration
* Testing
* Documentation
* Review of remaining issues
* Final project preparation

> The weekly breakdown will be updated with detailed tasks and screenshots as the documentation is finalized.

---

## 📷 Screenshots

Project screenshots and deployment evidence are available in:

```text
/screenshots
```

Screenshots include:

* Azure Resource Group
* App Service
* Azure SQL
* Blob Storage
* Containers
* Application Insights
* Monitoring
* Deployment
* Troubleshooting and error messages

---

## 📁 Repository Structure

```text
Elghool-Online-Store-DevOps/
│
├── README.md
│
├── Documentation/
│   └── PROJECT-DOCUMENTATION.md
│
├── Azure/
│   ├── App-Service/
│   ├── SQL/
│   ├── Blob-Storage/
│   ├── Key-Vault/
│   └── Application-Insights/
│
├── CI-CD/
│
├── Screenshots/
│
└── Scripts/
```

---

## ✅ Project Status

| Component            | Status         |
| -------------------- | -------------- |
| Azure Infrastructure | 🟡 In Progress |
| Backend Hosting      | 🟡 In Progress |
| Azure SQL            | 🟡 In Progress |
| Blob Storage         | 🟡 In Progress |
| Key Vault            | 🟡 In Progress |
| Application Insights | ✅ Configured   |
| Monitoring           | 🟡 In Progress |
| CI/CD                | 🟡 In Progress |
| Frontend Deployment  | 🟡 In Progress |
| Domain Configuration | ⏳ Pending      |
| Final Integration    | ⏳ Pending      |

> Project status will be updated as the remaining deployment and integration tasks are completed.

---

## 🛠️ Tools & Technologies

* Microsoft Azure
* Azure Portal
* Azure App Service
* Azure SQL
* Azure Blob Storage
* Azure Key Vault
* Application Insights
* GitHub
* GitHub Actions
* Postman
* Visual Studio
* .NET
* React

---

## 📚 References

* Microsoft Azure Documentation
* Azure App Service Documentation
* Azure Blob Storage Documentation
* Azure SQL Documentation
* Azure Key Vault Documentation
* Azure Application Insights Documentation
* GitHub Documentation

---

## 👩‍💻 DevOps

**Menna Nasser**

DevOps / Cloud Infrastructure

**Project:** Elghool Online Store

**Duration:** 20 June 2026 – 17 July 2026
