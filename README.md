# Docker Resources for WSO2 Enterprise Integrator

This repository contains following Docker resources :

- Dockerfiles to create docker images
- Docker-compose files to evaluate simple WSO2 EI deployment with MySQL Database.

Dockerfiles enables us to build generic Docker images for deploying the product in containerized environments. <br> The base Dockerfile includes the JDK and product distribution. <br>
Configurations, JDBC driver, extensions and other deployable artifacts are designed to be provided via volume mounts.

The Docker Compose files make use of the docker images of WSO2 Enterprise Integrator and MySQL.
