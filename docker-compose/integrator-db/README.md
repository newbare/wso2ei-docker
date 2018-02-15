# WSO2 Enterprise Integrator

## Prerequisites

  * [Docker](https://www.docker.com/get-docker) and [Docker Compose](https://docs.docker.com/compose/install/#install-compose) are required to run this deployment.

## How to Run

  1. Pull necessary images or build them using its [Dockerfile](../../dockerfiles) :
     ```
     docker pull wso2ei-integrator:6.1.1
     ```

  2. Pull MySQL Docker image :
     ```
     docker pull mysql:5.7.20
     ```

  3. Download the latest Docker resources for the product from (https://github.com/varun1231/wso2ei-docker)
     page or clone this repository <br> to your local machine and switch to latest release tag.

     > Note that the local copy of `wso2ei-docker` repository will be referred to as `[wso2ei-docker]` from this point onwards.

  4. Switch to docker-compose/integrator-db folder :
     ```
     cd [wso2ei-docker]/docker-compose/integrator-db
     ```

  5. Download [MySQL Connector/J](https://dev.mysql.com/downloads/connector/j/) JAR v5.1.45 to your local machine and copy to following locations:
     ```
     [wso2ei-docker]/docker-compose/integrator-db/integrator/lib
     ```

     > Note that SSL is by default set to false for all MySQL datasource configurations as latest connectors restrict SSL communication only for MySQL servers with verified server certificates.

  6. Before to start deployment process, add a host entry pointing to the Docker host machine IP address. <br>
     For an example if the Docker host is accessible via 127.0.0.1 on a Linux or Mac machine, add <br>
     following entry to /etc/hosts file :
     ```
     127.0.0.1 wso2ei-integrator
     ```

  7. Execute following Docker Compose command to start the deployment :
     ```
     docker-compose up
     ```

  8. Access management console via a web browser :
     ```
     For Integrator - https://wso2ei-integrator:9443/carbon
     ```
