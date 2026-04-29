# Docker Lab: Containerizing a Three-Tier Application
**INET 4031 - Introductions to Systems**

This lab introduces Docker and Docker Compose by having you containerize a
real, multi-service application. You will package three components: Apache,
Flask, and MariaDB. These will be packaged into separate containers and wired together so they function as a complete application.

The application code and scaffolding are provided. Your job is to complete the Dockerfiles, verify the stack runs correctly, and document your work below.

> **Directions and explanations for this lab are on the repository Wiki.**
> Refer to the Wiki pages for step-by-step instructions.

---

*The sections below are for you to fill out. Replace each placeholder with your own content before submitting. Having a detailed README is the best practice for showing your work in future GitHub repositories.*

---

# Project Overview
The app works as a ticketing system website. Users can submit, view and complete ticket requests in a convinent format. This app solves the problem of not having a dedicated  system for track work issues. The app stores tickets in a database and presents them in a compact webpage. The “Docker Lab – Ticketing System” webpage is the main page for viewing existing tickets and creating new tickets, but this can also be done from the command line.

<!-- Briefly describe what this application does in your own words.
     What problem does it solve? What does a user interact with? -->

# Prerequisites
The VM used to run the application was run using an Ubuntu 64‑bit OS with at  2 GB of RAM and 2 CPU cores. Docker and Docker Compose must be installed and working. This application used Docker version 28.1.1 and Docker Compose version v2.35.1. The app also needs the components used inside the containers: Apache, MariaDB, and Flask, which will be installed automatically when their Docker images are built. This uses Apache2 version Apache/2.4.41. 

<!-- List what needs to be installed or configured on the VM before this lab
     will work. Include Docker, Docker Compose, and anything else required. -->

# Getting Started
For someone new, begin by cloning the repository and moving to the project directory. Create your own environment file: cp .env.example .env

With a working .env file, fill in the information to include appropriate environment variables.

The stack is run through one command: docker compose up --build

The images will be built, starting all three services, and bring the application online.

<!-- Explain how a new teammate would bring this stack up from a fresh clone.
     Walk through every command they need to run, in order. -->

# Configuration
The .env file stores database credentials used by both MariaDB and Flask in order to function. Of which, the most important are DB_ROOT_PASSWORD, DB_NAME, DB_USER, and DB_PASSWORD. These variables are not included in the repository. For every new instance of the application, a new .env file must be made with its own password values before bringing the stack up.

<!-- Explain the .env file: what it is, what variables it contains,
     and what a teammate needs to provide that is not in this repository. -->

# Verification
To verify the stack functions a manual check is provided: check the db and app containers healthy status using docker compose ps. The web container should show as running. Next, verify that the frontend webpage loads by visiting http://<YOUR‑SPECIFIC‑IP>:80 and confirming that the dashboard displays a green “healthy” indicator. Finally, confirm the Apache  the health endpointby through this command: curl http://localhost:80/health
The API should be returning ticket data from the database. 

A "check-lab.sh" script has been provided for automatic verification of the app. The script will work to verify the health of the container, the connection to Apache, the health endpoint of Flask, the API functionality, the Data Persistence and Netowrking. A fully functioning application will finish a passing run, showing all tests marked as PASS with no failures.

<!-- Describe how to confirm the stack is running correctly.
     Reference the check script and what a passing run looks like. -->

# LAB 13 UPDATE
The application doesn't run on Docker Compose. The application now runs using Kubernetes. Yaml files for the three-tiers have been added. A file named "create-secret" was created to replace ".env" for database credentials.

To deploy the app, issue the following command: kubectl apply -f k8s/
Ensure you are in the correct directory before trying to deploy.

The application will be found at PORT 30080. The browser URL to access the application will depend on the IP of your machine.

This is an example URL: http://<YOUR-MACHINE-IP>:30080


Having a visual to understand what we're doing/changing overall could make this easier to understand. Understanding how the code works was a challenge.

