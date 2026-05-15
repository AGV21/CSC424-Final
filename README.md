# CSC424 Final Exam

## Overview

This project is a containerized full-stack web application using Docker Compose. The application consists of:

- A React frontend
- A .NET backend API
- An Nginx reverse proxy

All services communicate through a shared Docker bridge network.

---

# Running the Application

From the root of the repository, run:

```bash
docker compose up --build -d
```

This command builds and starts all containers in detached mode.

To stop the application:

```bash
docker compose down
```

---

# Ports and Test URLs

The application is exposed through Nginx on port 80.

Frontend:

```text
http://localhost
```

Backend API test endpoint:

```text
http://localhost/api/ping
```

Expected backend response:

```json
{
  "status": "ok",
  "message": "pong"
}
```

---

# Docker Services

## Frontend

The frontend is a React + Vite application containerized using Docker. It provides the user interface for the application.

## Backend

The backend is a .NET API containerized using Docker. It processes API requests and exposes the `/api/ping` endpoint.

## Nginx

Nginx acts as a reverse proxy for the application.

Routing configuration:
- `/` routes traffic to the frontend container
- `/api/` routes traffic to the backend container

Only the Nginx container exposes a port to the host machine.

---

# CI/CD Pipeline

This project uses GitHub Actions for CI/CD automation.

On every push to the `main` branch, the workflow:

1. Builds Docker images
2. Pushes images to Docker Hub
3. Deploys updated containers using Docker Compose

The workflow file is located at:

```text
.github/workflows/deploy-qa.yml
```
