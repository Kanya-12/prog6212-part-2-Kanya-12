# prog6212-part-2-Kanya-12

# RaceDay Event Management System Part2

1. *Project Description:*

- RaceDay is a full-stack event management system for the South African road running, walking, and cycling community. Event organisers create and manage events, categories, routes, and results, while participants browse events, enrol in categories, and track their own performance history.

This repository contains the Part 2 implementation for PROG6212 (Programming 2B), including the ASP.NET Core Web API, EF Core model, Swagger API, unit tests, and CI/CD workflow. The Part 1 planning documents remain in the /docs folder and are still the specification for the project foundation.

2. *User Roles*

A) *Organiser:*

- Registers and logs in as an organiser.
- Creates, edits, and deletes their own events.
- Manages categories and routes for their own events.
- Views all enrolments for their own events and can change an enrolment status.
- Captures and corrects finish times and finishing positions for their own events.
- Cannot enrol in events or edit another organiser's events.

B) *Participant:*

- Registers and logs in as a participant.
- Browses events, categories, and routes.
- Enrols in an event by choosing a category.
- Views and cancels their own enrolments.
- Views their own results and performance history.
- Cannot create, edit, or delete events, categories, routes, or results.

Both roles can view and update their own profile.

3. *Part 1 Deliverables*


## Part 1 Deliverables

| Deliverable | File |
|---|---|
| Entity Relationship Diagram | [RaceDay_ERD.pdf](https://github.com/RCNMBCampus/prog6212-part-1-Kanya-12/blob/ce7c92df92390fc9564417d4c0ef1fcf9eb84456/docs/RaceDay_ERD.pdf) |
| API Endpoint Plan | [RaceDay_API_Endpoint_Plan.pdf](https://github.com/RCNMBCampus/prog6212-part-1-Kanya-12/blob/ce7c92df92390fc9564417d4c0ef1fcf9eb84456/docs/RaceDay_API_Endpoint_Plan.pdf) |
| SQL Database Script | [RaceDay_Database.sql](https://github.com/RCNMBCampus/prog6212-part-1-Kanya-12/blob/ce7c92df92390fc9564417d4c0ef1fcf9eb84456/docs/RaceDay_Database.sql) |

The database has six entities: User, Event, Category, Route, Enrolment, and Result. Enrolment is the associative entity resolving the many-to-many relationship between Participants and Events via a chosen Category. Result has a 1:0..1 relationship with Enrolment because a result only exists once the organiser captures it.

The Part 1 workflow (.github/workflows/part1-ci.yml) checks that the /docs folder and required files exist.

## Part 1 CI screenshot:

<img width="813" height="54" alt="image" src="https://github.com/user-attachments/assets/06b55ae6-450c-409b-bdab-0b66e0aae5cb" />

## Successful build screenshot:

<img width="898" height="54" alt="image" src="https://github.com/user-attachments/assets/dcaeff56-6205-4a48-85fe-27f0fff2af01" />

## Part 1 video (unlisted):
- https://youtu.be/DlgdIhYUSgA

## Part 2

*Technologies Used:*
- ASP.NET Core 8 Web API (C#), built with Visual Studio 2022
- Entity Framework Core 8, Code-First, with SQL Server
- Server-side sessions for authentication (AddSession)
- ASP.NET Core PasswordHasher for password hashing
- Swashbuckle (Swagger UI) with XML documentation comments
- xUnit, Microsoft.AspNetCore.Mvc.Testing and the EF Core in-memory provider for tests
- GitHub Actions for CI/CD

*Project Structure*

```text
RaceDay/
├── RaceDay.sln
├── docs/                         # Part 1 planning documents
├── RaceDay.Api/                  # ASP.NET Core Web API
│   ├── Controllers/              # Auth, Profile, Events, Categories,
│   │                             # Routes, Enrolments, Results
│   ├── Data/                     # RaceDayDbContext
│   ├── Filters/                  # RequireRoleAttribute (role enforcement)
│   ├── Migrations/               # Entity Framework Core migrations
│   ├── Models/                   # AppUser, Event, Category, RaceRoute,
│   │                             # Enrolment, Result, Role
│   ├── Properties/
│   │   └── launchSettings.json
│   ├── appsettings.json
│   └── Program.cs
├── RaceDay.Contracts/            # Shared request and response DTOs
│   └── Dtos.cs
├── RaceDay.Api.Tests/            # xUnit automated tests
├── .github/
│   └── workflows/
│       ├── part1-ci.yml
│       └── part2-ci.yml
└── README.md
```

## Database Setup:
