# Jenkins CI/CD Pipeline with Docker

A simple Node.js application deployed using a Jenkins CI/CD pipeline and Docker.

This project demonstrates how Jenkins can automatically build, test, containerize, and deploy a Node.js application whenever changes are pushed to the GitHub repository.

---

## 📌 Project Overview

This project implements a basic CI/CD pipeline using:

- Node.js
- Express.js
- Git
- GitHub
- Jenkins
- Docker

The application is packaged into a Docker image and deployed as a Docker container through Jenkins.

The pipeline performs the following operations:

1. Checkout source code from GitHub
2. Install Node.js dependencies
3. Run application tests
4. Build a Docker image
5. Stop the previous application container
6. Remove the old container
7. Start a new container with the latest Docker image

---

## 🏗️ Architecture

```text
                Developer
                    |
                    | git push
                    ↓
              GitHub Repository
                    |
                    | SCM Polling
                    ↓
                 Jenkins
                    |
          ┌─────────┴─────────┐
          ↓                   ↓
     Checkout Code       Install npm packages
          |                   |
          └─────────┬─────────┘
                    ↓
                Run Tests
                    |
                    ↓
              Docker Build
                    |
                    ↓
          Docker Image Created
                    |
                    ↓
        Stop Existing Container
                    |
                    ↓
          Remove Old Container
                    |
                    ↓
          Start New Container
                    |
                    ↓
             Node.js App
                    |
                    ↓
            http://localhost:3000
