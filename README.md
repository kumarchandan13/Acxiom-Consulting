# AcxiomCRM — Customer Relationship Management System

AcxiomCRM is a web-based Customer Relationship Management (CRM) application built using ASP.NET Core 8 MVC. It helps organizations manage customers, leads, sales opportunities, follow-ups, activities, users, and audit records from a centralized application.

The project includes role-based access control, secure authentication, input validation, dashboard analytics, audit logging, and REST API endpoints.

## Features

### 1. Authentication and Authorization
- User registration, login, and logout.
- Secure password hashing using ASP.NET Core Identity.
- Password policy enforcement and account lockout.
- Role-based access for Admin, Manager, and Sales Executive.
- Protection against unauthorized access.
- Anti-forgery protection for state-changing forms.

### 2. Dashboard
- Display total customers, leads, and opportunities.
- Monitor open, won, and lost opportunities.
- View sales pipeline information.
- Interactive charts using Chart.js.
- Role-based dashboard statistics.

### 3. Customer Management
- Create, view, update, search, and manage customer records.
- Store customer contact and company information.
- Validate email addresses and phone numbers.
- Prevent duplicate customer records.

### 4. Lead Management
- Create and manage prospective customers.
- Track lead source, status, priority, and assignment.
- Support lead qualification and conversion workflows.

### 5. Opportunity Management
- Manage sales opportunities and pipeline stages.
- Track opportunity amount, probability, and expected closing date.
- Apply business validation rules to opportunity data.

### 6. Follow-Up and Activity Management
- Schedule and manage customer follow-ups.
- Track calls, meetings, emails, and tasks.
- Monitor pending, completed, missed, and overdue activities.

### 7. User and Role Management
- Create and manage application users.
- Assign roles and manage account status.
- Restrict administrative features to authorized users.

### 8. Audit Logging
- Record important authentication and CRM operations.
- Track user actions, record changes, and timestamps.
- Support authorized audit-log review.

### 9. Reports and REST APIs
- Generate CRM reports and sales pipeline summaries.
- Provide API endpoints for customers, leads, opportunities, and follow-ups.
- Apply input validation and authorization to protected API operations.

## Technology Stack

- **Language:** C#
- **Framework:** ASP.NET Core 8 MVC
- **Authentication:** ASP.NET Core Identity
- **ORM:** Entity Framework Core 8
- **Database:** SQLite
- **Frontend:** HTML5, CSS3, JavaScript, Bootstrap 5
- **UI Rendering:** Razor Views
- **Charts:** Chart.js
- **Architecture:** Layered MVC architecture
- **API:** RESTful Web APIs

## Project Structure

```text
AcxiomCRM/
├── Controllers/          # MVC and API controllers
│   └── Api/
├── Data/                 # Database context and seed data
├── DTOs/                 # Data transfer objects
├── Models/               # Application and CRM entities
├── Services/             # Business and audit services
├── Views/                # Razor views
├── wwwroot/
│   ├── css/              # Stylesheets
│   └── js/               # JavaScript files
├── docs/                 # API documentation and test plans
├── AcxiomCRM.csproj
├── AcxiomCRM.sln
├── Program.cs
├── appsettings.json
├── run-local.ps1
└── run-local.sh
```

## Prerequisites

Before running the application, install:

- .NET 8 SDK
- Visual Studio 2022 with the ASP.NET and web development workload, or Visual Studio Code with C# tooling
- Internet access for any frontend assets loaded through CDNs

## Installation and Setup

### Step 1: Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd AcxiomCRM
```

Replace `<YOUR_GITHUB_REPOSITORY_URL>` with your GitHub repository URL.

If you downloaded the project as a ZIP file, extract it and open a terminal in the directory containing `AcxiomCRM.csproj`.

### Step 2: Restore Dependencies

```bash
dotnet restore
```

### Step 3: Run the Application

**Windows PowerShell:**

```powershell
.\run-local.ps1
```

**Alternatively, use the .NET CLI:**

```bash
dotnet run
```

Run the command from the directory containing `AcxiomCRM.csproj`.

### Step 4: Open the Application

Open the URL printed in the terminal after the application starts.

The included Visual Studio launch profile uses:

- `https://localhost:7188`
- `http://localhost:5188`

The SQLite database file, `acxiomcrm.db`, is created automatically on first startup.

## Development Administrator Account

The current development seed configuration provides the following local evaluation account:

- **Email:** `admin@acxiomcrm.local`
- **Password:** `Admin@12345`

This account is intended only for local development and evaluation. Change the credentials before deployment and never use the sample password in production.

## Main Application Routes

| Module | Route |
|---|---|
| Login | `/Account/Login` |
| Registration | `/Account/Register` |
| Dashboard | `/Dashboard` |
| Customers | `/Customers` |
| Leads | `/Leads` |
| Opportunities | `/Opportunities` |
| Follow-Ups | `/FollowUps` |
| Activities | `/Activities` |
| User Management | `/Users` |
| Audit Log | `/Audit` |

## REST API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/login` | Authenticate a user |
| POST | `/api/auth/logout` | End the authenticated session |
| GET | `/api/customers` | Retrieve or search customers |
| GET | `/api/customers/{id}` | Retrieve a customer by ID |
| POST | `/api/customers` | Create a customer |
| PUT | `/api/customers/{id}` | Update a customer |
| DELETE | `/api/customers/{id}` | Delete or deactivate a customer, as implemented |
| GET | `/api/leads` | Retrieve leads |
| POST | `/api/leads` | Create a lead |
| GET | `/api/opportunities` | Retrieve opportunities |
| POST | `/api/opportunities` | Create an opportunity |
| GET | `/api/followups` | Retrieve follow-ups |
| POST | `/api/followups` | Create a follow-up |
| GET | `/api/reports/pipeline` | Retrieve sales pipeline report data |

Protected endpoints require appropriate authentication and authorization.

## Validation and Security

The application supports the following validation and security requirements:

- Client-side and server-side validation.
- Required-field validation.
- Email and phone number validation.
- String length validation.
- Date and numeric range validation.
- Opportunity amount and probability validation.
- Expected close date and follow-up date validation.
- Duplicate customer checks.
- ASP.NET Core Identity password hashing.
- Role-based authorization.
- Anti-forgery protection for state-changing MVC forms.
- Audit logging for important operations.
- Protection of sensitive authentication information in API responses.

## Documentation and Testing

The `docs/` directory contains project documentation, including:

- `API.md` — API endpoint notes and request examples.
- `REQUIREMENTS_TRACEABILITY.md` — Requirement-to-implementation mapping.
- `TEST_PLAN.md` — Testing plan.

Important test scenarios include authentication, role-based access, customer validation, duplicate prevention, opportunity business rules, follow-up scheduling, audit logging, dashboard charts, and API authorization.

## Database

AcxiomCRM uses SQLite for local development and initializes the database on application startup.

For production use, review the database initialization process and consider Entity Framework Core migrations, secure configuration, and a database backup strategy.

## Future Improvements

- Automated unit and integration tests.
- Email notifications and password-reset workflows.
- Advanced reporting and data export.
- Improved monitoring and error handling.
- Production database configuration.
- Enhanced API documentation and rate limiting.

## Security Notice

This project is intended as a development and evaluation baseline. Before production deployment, review the sample administrator account, secrets management, HTTPS configuration, API rate limiting, database backups, logging, and record-level authorization.

Never commit production credentials, connection-string secrets, or other sensitive information to a public repository.

## Project Objective

The objective of AcxiomCRM is to demonstrate a structured CRM application that supports the customer-sales lifecycle, from lead capture and customer management to opportunity tracking, follow-ups, reporting, and auditing.

The project emphasizes secure authentication, role-based authorization, business validation, dashboard analytics, REST API functionality, and maintainable application architecture.

---

**Project Name:** AcxiomCRM  
**Framework:** ASP.NET Core 8 MVC  
**Language:** C#  
**Database:** SQLite
