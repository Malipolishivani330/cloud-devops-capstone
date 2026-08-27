# 🚀 Cloud & DevOps Capstone Project

A production-style Cloud and DevOps project demonstrating containerization, Continuous Integration and Continuous Deployment (CI/CD), automated testing, troubleshooting, and cloud deployment.

The application is built using **Python and Flask**, containerized using **Docker**, validated through **GitHub Actions**, and deployed as a live web service on **Render**.

---

## 🌐 Live Application

🔗 **Live Website:** https://cloud-devops-capstone.onrender.com

🔗 **GitHub Repository:** https://github.com/Malipolishivani330/cloud-devops-capstone

---

# 📌 Project Overview

This project demonstrates an end-to-end DevOps workflow.

A developer makes changes to the application and pushes the code to GitHub. The GitHub Actions CI/CD pipeline automatically validates the application by building a Docker image, running a container, checking application availability, verifying container status, and reviewing logs.

After successful validation, the application is deployed to Render and becomes accessible through a public URL.

### Complete Flow

```text
Developer
    │
    │ git push
    ▼
GitHub Repository
    │
    ▼
GitHub Actions CI/CD
    │
    ├── Checkout Code
    ├── Build Docker Image
    ├── Run Docker Container
    ├── Wait for Application
    ├── Verify Application
    ├── Check Container Status
    └── Check Container Logs
    │
    ▼
Docker Container
    │
    ▼
Render Cloud Platform
    │
    ▼
Live Flask Application
🏗️ Architecture Diagram

The architecture follows this workflow:

Developer writes the Flask application.
Source code is pushed to GitHub.
GitHub Actions automatically triggers the CI/CD pipeline.
Docker builds a container image using the Dockerfile.
The container is started and the application is tested.
Application health and container status are verified.
Render deploys and runs the application.
Users access the application through the public Render URL.
🛠️ Technology Stack
Technology	Purpose
Python	Backend programming language
Flask	Web application framework
HTML	Application frontend
Docker	Application containerization
Docker Compose	Local container orchestration
Git	Version control
GitHub	Source code repository
GitHub Actions	CI/CD automation
Render	Cloud deployment platform
📂 Project Structure
cloud-devops-capstone/
│
├── app/
│   ├── app.py
│   ├── requirements.txt
│   └── templates/
│       └── index.html
│
├── .github/
│   └── workflows/
│       └── ci-cd.yml
│
├── Dockerfile
├── docker-compose.yml
├── .dockerignore
├── architecture-diagram.png
└── README.md
🐍 Application

The application is a lightweight Flask web application.

The Flask application provides a simple web interface confirming that the application is running successfully.

The application demonstrates how a Python application can be packaged into a Docker container and deployed using a cloud platform.

🐳 Docker Containerization

Docker is used to package the application and its dependencies into a portable container.

This ensures that the application can run consistently across different environments.

Build Docker Image
Command:-
docker build -t cloud-devops-capstone .
Run Docker Container
Command:- docker run -d -p 5000:5000 --name cloud-devops-app cloud-devops-capstone
Check Running Containers
Command:-docker ps
View Container Logs
Command:- docker logs cloud-devops-app
Stop the Container
Command:- docker stop cloud-devops-app
Check Services
Command:- docker compose ps
View Logs
Command:- docker compose logs
Stop Services
Command:- docker compose down
🔄 CI/CD Pipeline

The project uses GitHub Actions to automate application validation.

The workflow is triggered when code is pushed to the configured branch.

Pipeline Steps
1. Checkout Code

The GitHub Actions runner downloads the latest source code.

Checkout Code
2. Build Docker Image

The Dockerfile is used to create a container image.

Build Docker Image

This step validates whether:

The Dockerfile syntax is correct.
Required files are available.
Python dependencies can be installed.
The application can be packaged successfully.
3. Run Docker Container

The newly created Docker image is started as a container.

Run Docker Container

This verifies that the container can start successfully.

4. Wait for Application

The pipeline waits for the application to become available.

Wait for Application

This prevents verification from running before the application is ready.

5. Verify Application

The CI/CD pipeline checks whether the application responds successfully.

A successful response confirms that the Flask application is running.

Verify Application
6. Check Container Status

The pipeline verifies that the Docker container is still running.

Check Container Status

This helps detect situations where a container starts but immediately exits.

7. Check Container Logs

Application logs are inspected to help identify runtime errors.

Check Container Logs

Logs are important for troubleshooting issues such as:

Python errors
Missing dependencies
Incorrect ports
Application startup failures
Docker configuration problems
🔁 CI/CD Workflow
Code Change
     │
     ▼
Git Push
     │
     ▼
GitHub Repository
     │
     ▼
GitHub Actions Triggered
     │
     ▼
Checkout Source Code
     │
     ▼
Build Docker Image
     │
     ▼
Run Docker Container
     │
     ▼
Wait for Application
     │
     ▼
Verify Application
     │
     ├── Success ─────► Continue
     │
     └── Failure ─────► Check Logs & Fix Issue
                          │
                          ▼
                       Git Push
                          │
                          └────► Pipeline Runs Again
☁️ Cloud Deployment

The application is deployed using Render.

Render connects to the GitHub repository and deploys the application as a web service.

Deployment Flow
GitHub Repository
       │
       ▼
Render
       │
       ▼
Detect Dockerfile
       │
       ▼
Build Application
       │
       ▼
Create Container
       │
       ▼
Start Flask Application
       │
       ▼
Public URL Generated
Live Deployment

🌐 https://cloud-devops-capstone.onrender.com

🔍 Troubleshooting Guide

This section documents common DevOps problems and the troubleshooting approach.

A strong DevOps engineer does not immediately restart or rebuild everything. The first step is to identify where the failure is occurring.

The general troubleshooting approach used is:

Identify Problem
       │
       ▼
Collect Information
       │
       ▼
Check Logs
       │
       ▼
Identify Root Cause
       │
       ▼
Apply Fix
       │
       ▼
Test Again
       │
       ▼
Verify Solution
❌ Problem 1: Docker Container Stops Immediately
Check Container Status
docker ps -a

If the container shows:

Exited

check the logs.

docker logs <container-name>
Possible Causes
Python application error
Missing dependency
Incorrect command
Incorrect environment configuration
Application crashes during startup
Troubleshooting Approach
Container Exited
      │
      ▼
Check docker logs
      │
      ▼
Find application error
      │
      ▼
Fix Dockerfile or application
      │
      ▼
Rebuild image
      │
      ▼
Run container again
❌ Problem 2: Application Is Running But Website Does Not Open

First check the container:

docker ps

Then verify port mapping.

Example:

docker run -p 5000:5000 cloud-devops-capstone

Check whether the Flask application is listening on the expected port.

Troubleshooting Steps
Website Not Accessible
        │
        ▼
Check Container Status
        │
        ▼
Check Port Mapping
        │
        ▼
Check Application Logs
        │
        ▼
Verify Application Port
        │
        ▼
Test Again
❌ Problem 3: Docker Build Fails

Run:

docker build -t cloud-devops-capstone .

Check the error message carefully.

Common Causes
Incorrect Dockerfile instructions
Wrong file paths
Missing requirements.txt
Python dependency installation failure
Incorrect base image
Troubleshooting
docker build --no-cache -t cloud-devops-capstone .

The --no-cache option forces Docker to rebuild the image without using old cached layers.

❌ Problem 4: GitHub Actions Pipeline Fails

Go to:

GitHub Repository
      ↓
Actions
      ↓
Select Failed Workflow
      ↓
Open Failed Job
      ↓
Check Failed Step
      ↓
Read Error Logs

Do not assume the entire pipeline is broken.

Identify the exact failed stage:

Checkout?
Docker Build?
Container Start?
Application Verification?

Fix only the root cause and push the updated code.

git add .
git commit -m "Fix CI/CD pipeline issue"
git push

GitHub Actions will run the workflow again.

❌ Problem 5: Application Health Check Fails

Check if the application is running:

docker ps

Check logs:

docker logs <container-name>

Test the application locally:

http://localhost:5000

If the container is running but the application is unavailable, investigate:

Application startup command
Flask host configuration
Port configuration
Timing issues during startup
❌ Problem 6: Application Starts Slowly

Sometimes the verification step can fail because the application is not ready yet.

The CI/CD workflow should include a waiting step before testing.

Example workflow logic:

Start Container
      │
      ▼
Wait for Application
      │
      ▼
Verify Application

This prevents false failures caused by checking the application too early.

❌ Problem 7: Changes Are Not Reflected After Deployment

Check the following:

Step 1: Verify Git Status
git status
Step 2: Check Commit
git log --oneline
Step 3: Push Latest Changes
git push
Step 4: Check GitHub Actions

Verify that the latest workflow was triggered.

Step 5: Check Render Deployment Logs

Confirm that Render deployed the latest commit.

📊 Monitoring and Log Analysis

Logs are essential for diagnosing application problems.

Docker Logs
docker logs <container-name>
Follow Live Logs
docker logs -f <container-name>
Container Resource Usage
docker stats

This helps monitor:

CPU usage
Memory usage
Network activity
🧠 Problem-Solving Methodology

The project follows a structured troubleshooting methodology.

Step 1: Understand the Problem

Example:

Application is not accessible.

Do not immediately rebuild everything.

Step 2: Identify the Layer

Determine where the problem exists.

Application Layer
      ↓
Docker Layer
      ↓
CI/CD Layer
      ↓
Cloud Deployment Layer
      ↓
Network / Port Layer
Step 3: Collect Evidence

Use:

docker ps
docker logs <container-name>
docker inspect <container-name>
docker compose ps
docker compose logs

For CI/CD:

GitHub Actions Logs

For deployment:

Render Deployment Logs
Step 4: Find the Root Cause

Example:

Problem:
Application is not opening.

Incorrect assumption:
"The server is down."

Actual investigation:
Container status → Running
Logs → Application started
Port → Incorrect configuration

Root Cause:
Port mismatch.
Step 5: Fix and Verify

After applying a fix:

Fix
 ↓
Rebuild
 ↓
Run
 ↓
Test
 ↓
Check Logs
 ↓
Confirm Application

A problem is not considered solved until it is verified.

🔐 DevOps Best Practices Demonstrated

This project demonstrates several DevOps practices:

Infrastructure automation through configuration files
Application containerization
Reproducible environments
Automated CI/CD validation
Automated Docker image builds
Application verification
Container health checking
Log-based troubleshooting
Cloud deployment
Source code version control
Continuous feedback through CI/CD pipelines
Remove the Container
Command:- docker rm cloud-devops-app
⚙️ Docker Compose

Docker Compose simplifies the process of building and running the application.

Start Application
Command:- docker compose up --build
Run in Background
Command:- docker compose up -d --build
