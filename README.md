# MyMarvin: Automated Jenkins CI/CD Deployment

MyMarvin is a DevOps infrastructure project that provisions a fully functional, containerized Jenkins environment using Configuration as Code (JCasC) and Job DSL.

## The Goal

The primary objective is to eliminate manual Jenkins configuration. By utilizing Docker, plugins, and YAML/Groovy scripts, this project demonstrates how to spin up a production-ready CI/CD server that automatically configures its own security, plugins, and initial jobs upon boot.

## Core Technologies

- **Docker & Docker Compose**: Containerizes the Jenkins master node for reproducible deployments.
- **Jenkins Configuration as Code (JCasC)**: Uses `my_marvin.yml` to define security realms, authorization strategies, and global settings without manual UI clicking.
- **Job DSL**: Uses `job_dsl.groovy` to programmatically define "seed jobs" that automatically generate and configure other pipelines and jobs upon startup.
- **Plugin Management**: Automatically installs required dependencies via `plugins.txt`.

## How It Works

1. The `Dockerfile` pulls the official Jenkins LTS image and installs the required plugins.
2. At boot, JCasC reads `my_marvin.yml` to set up the admin user, configure permissions, and disable the setup wizard.
3. The Job DSL script runs, dynamically creating the initial pipeline structures.
4. `docker-compose.yml` orchestrates the port mapping and volume persistence.

## Key DevOps Learnings

- **Infrastructure as Code (IaC)**: Transforming manual server setup into version-controlled text files.
- **Idempotency**: Ensuring the server can be destroyed and recreated at any time with the exact same configuration.
- **Automation**: Drastically reducing onboarding and recovery times for build servers.
