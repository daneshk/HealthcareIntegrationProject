# Healthcare Integration Project

This a sample project to demonstrate the immutable docker image creation for the MI integration project. Please refer to the [Quick start guide](https://ei.docs.wso2.com/en/latest/micro-integrator/overview/quick-start-guide/) to get more details on the usecase.

## Components of the project

- **backend services**: The backend service .jar file and Dockerfile are in the `backend` directory.
- **Dockerfile**: The Dockerfile for the MI integration project is in the `deployment/docker` directory. The Dockerfile is used to create the immutable docker image.
- **Integration project**: The integration project artifacts are in the `src/main/wso2mi` directory. This is normal structure of the integration project.
- **Docker-compose file**: The docker-compose file is in the root directory. This file is used to run the integration project docker image and the backend service in a single command.

## How to build the project

1. Clone the repository.
2. Navigate to the root directory of the project.
3. Run the following command to build the project.
    ```bash
    mvn clean install -P docker
    ```
4. The docker image(daneshk/healthcareintegrationproject:1.0.0) will be created and you can see the image by running the following command.
    ```bash
    docker images
    ```
5. In the target directory, you can see 
    - The .car file. 
    - The `extracted` directory contains the extracted content of the .car file.
    - The `tmp_docker`directory contains the artifacts and resources required to create the docker image and the `Dockefile` to create the docker image. This directory is used by the fabric8 maven plugin to create the docker image.

6. Optional step: You can push the docker image to the docker hub by running the following command.
    ```bash
    docker push daneshk/healthcareintegrationproject:1.0.0
    ```
7. Run the following command to start the integration project and the backend service.
    ```bash
    docker-compose up
    ```
8. Access the following URL to see the response from the API.
    ```bash
    curl -v http://localhost:8290/healthcare/doctor/Ophthalmologist 
    ```
9. Run the following command to stop the integration project and the backend service.
    ```bash
    docker-compose down
    ```




