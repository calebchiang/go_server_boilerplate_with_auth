# Go Server Boilerplate with Authentication

A reusable **Go backend starter template** with authentication, JWT middleware, PostgreSQL integration, and a structured API architecture.

This repository is designed to provide a starting point for new Go backend projects so common infrastructure like authentication, routing, database setup, and middleware does not need to be rebuilt from scratch.

## Features

* **User Authentication** — Ready-to-use authentication routes and controllers
* **JWT Authentication** — Token-based authentication for protected API routes
* **Authentication Middleware** — Middleware for validating JWTs before allowing access to protected resources
* **PostgreSQL Integration** — Database connection configured using PostgreSQL
* **GORM** — ORM support for database models and queries
* **Gin Router** — Fast HTTP routing and REST API handling
* **Environment Variables** — Configuration through `.env` files
* **Structured Architecture** — Separates routes, controllers, middleware, models, and database logic
* **Reusable Template** — Can be used as the starting point for new Go APIs and backend services

## Tech Stack

* **Go**
* **Gin** — HTTP framework and API routing
* **PostgreSQL** — Relational database
* **GORM** — ORM and database interaction
* **JWT** — Authentication and authorization
* **godotenv** — Environment variable management

The template currently uses Gin, PostgreSQL/GORM, `golang-jwt`, and `godotenv`.

## Project Structure

```text
go_server_boilerplate_with_auth/
├── controllers/     # Request handlers and application logic
├── database/        # Database connection and configuration
├── middleware/      # Authentication and JWT middleware
├── models/          # Database models
├── routes/          # API route definitions
├── main.go          # Application entry point
├── go.mod           # Go dependencies
├── go.sum
└── .gitignore
```

The repository follows a separated controller, database, middleware, model, and routing structure.

## Authentication

JWT authentication is built into the template.

The general authentication flow is:

```text
Client
   │
   ▼
Authentication Route
   │
   ▼
User Controller
   │
   ▼
Database
   │
   ▼
JWT Generated
   │
   ▼
Client stores token
   │
   ▼
Authenticated Request
   │
   ▼
JWT Middleware
   │
   ▼
Protected Route
```

The included middleware can be used to protect routes that should only be accessible to authenticated users. The repository contains a dedicated `jwt.go` middleware implementation.

## Getting Started

Because this repository is configured as a **GitHub template**, you can select **Use this template** on GitHub to create a new repository based on it.

Alternatively, clone it directly:

```bash
git clone https://github.com/calebchiang/go_server_boilerplate_with_auth.git
cd go_server_boilerplate_with_auth
```

Install the Go dependencies:

```bash
go mod download
```

## Environment Variables

Create a `.env` file in the root of the project and configure the environment variables required by your database and authentication setup.

Example:

```env
DATABASE_URL=postgresql://user:password@localhost:5432/database
JWT_SECRET=your-secret-key
PORT=8080
```

Do not commit production credentials or secrets to source control.

## Run the Server

Start the development server with:

```bash
go run main.go
```

Or build the project first:

```bash
go build
```

Then run the generated executable.

## Adding Protected Routes

The authentication middleware can be applied to routes that require a valid JWT.

For example, a typical API might contain:

```text
POST   /auth/register
POST   /auth/login

GET    /api/profile
GET    /api/users
POST   /api/resource
```

Public authentication routes can be accessed normally, while protected API routes can be placed behind the JWT middleware.

## Extending the Template

To build a new API using this boilerplate:

1. Add your database models inside `models/`
2. Create request handlers inside `controllers/`
3. Define endpoints inside `routes/`
4. Protect private endpoints using the authentication middleware
5. Add database migrations or additional services as needed

This keeps new features separated from the core server infrastructure and makes the project easier to maintain as it grows.

## Use Cases

This template can be used as the foundation for:

* Mobile app backends
* REST APIs
* SaaS applications
* Web application backends
* Internal services
* Authentication-based APIs
* MVPs and side projects

## Purpose

The goal of this repository is to remove repetitive backend setup when starting a new Go project.

Instead of rebuilding authentication, JWT validation, database configuration, routing, and project structure for every application, this template provides those pieces as a reusable starting point.

## Repository

`github.com/calebchiang/go_server_boilerplate_with_auth`
