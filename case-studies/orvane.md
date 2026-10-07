# Orvane staff workspace

**My contribution:** Full-stack development.

**Technology:** React, Python/FastAPI, PostgreSQL, SQLAlchemy, Alembic, Keycloak and Docker Compose.

## The workflow

The workspace connects customers and projects with solar assessments, equipment information, reviewed designs, proposals, delivery planning and installation handover. Staff work with a shared project record as the work moves through these stages.

## What I worked on

- Frontend interfaces and backend services for staff and project workflows.
- Authenticated sessions with role and project access controls.
- Revision history, private evidence files and audit records.
- API contracts connecting the interface to the underlying data and services.

## What the project demonstrates

Access depends on both the signed-in identity and the project context. Revision history and audit records make changes inspectable. These are useful foundations for explaining why a user can see a particular record or why a workflow displays a particular state.

An investigation would compare the user's expected action with their account, project membership and the API response, then use available audit evidence to understand changes. That is a proposed diagnostic path; this summary does not claim a particular production support incident.

## Status and scope

The project status dated 3 October 2026 records deployment of installation and handover workflows. Human acceptance testing and production qualification remain open, and the operational ERP connection is pending. The project is presented as pre-release work, without claims about active customers or production scale.

This public case study contains no staff records, private project files, deployment details or application source.

[Back to portfolio](../README.md)
