# Random Choice Picker - Docker Implementation

## Overview
This document outlines the process and results of containerizing the **Random Choice Picker** application using Docker and serving it with Nginx. The application was successfully built, run in a Docker container, and made accessible via a web browser.

---

## Objective
The goal of this project was to:
- **Containerize** the Random Choice Picker application using Docker.
- **Serve** the application using Nginx as the web server inside a Docker container.
- Make the application **accessible** from a web browser at `http://localhost:8086`.
- **Verify** the functionality by checking Docker processes and image details.

---

## What We Were Trying to Do
We aimed to achieve the following:
1. **Create a Docker image** for the Random Choice Picker application that includes Nginx for serving the application files.
2. **Run the Docker container** and expose the necessary ports (8086 on the host machine to port 80 in the container) to make the application accessible.
3. **Verify that the container is running** properly and the application is accessible in a browser.
4. **Monitor the processes** running inside the container to ensure Nginx is serving the application as expected.

---

## What We Achieved
We successfully completed the following tasks:

1. **Built a Docker image** for the Random Choice Picker application:
    - The image was created using a `Dockerfile` that uses Nginx as a base image and copies the project files to the appropriate directory for serving.
    - The image was tagged as `randomchoicepicker` and was successfully built.

2. **Ran the Docker container**:
    - The container was successfully launched using the command `docker run -d -p 8086:80 randomchoicepicker`.
    - The container was accessible via `http://localhost:8086`, and the application was visible in the web browser.

3. **Verified the running container**:
    - We used `docker ps` to ensure the container was running and the port was mapped correctly.
    - Docker top and process checks confirmed that Nginx was running inside the container, serving the application properly.

4. **Checked Docker images and processes**:
    - The image `randomchoicepicker` was present in the Docker images list.
    - The running processes inside the container were checked using `docker top`, and it was confirmed that Nginx was handling the web requests as expected.

---

## Conclusion
We have successfully containerized the **Random Choice Picker** application using Docker and Nginx. The application is accessible in a browser at `http://localhost:8086`, and the container is running as expected. This approach ensures that the application can be easily deployed in any environment with minimal configuration, providing a scalable and reproducible setup for the future.

---

## Docker Image and Running Container Verification

| **Step**                         | **Outcome** |
|----------------------------------|-------------|
| **Creating the Dockerfile**      | Successfully created the Dockerfile to containerize the application using Nginx. |
| **Building the Docker Image**    | Docker image `randomchoicepicker` was successfully created. |
| **Running the Docker Container** | Container is running and accessible at `http://localhost:8086`. |
| **Checking Docker Images and Processes** | Docker images and processes were verified, confirming the container is running Nginx properly. |

---
