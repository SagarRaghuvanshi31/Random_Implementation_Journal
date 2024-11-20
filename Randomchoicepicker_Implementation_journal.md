# Random Choice Picker Application - Docker Implementation

## Overview
This document outlines the steps I followed to containerize the Random Choice Picker application using Docker and serve it with Nginx. The application is successfully built, run in a Docker container, and accessible via a web browser.

## Table of Contents
1. [Objective](#objective)
2. [Machine Information](#machine-information)
3. [Docker Image Creation](#docker-image-creation)
4. [Running the Docker Container](#running-the-docker-container)
5. [Checking Docker Images and Processes](#checking-docker-images-and-processes)
6. [Conclusion](#conclusion)

---

## Objective
The objective of this implementation is to containerize the Random Choice Picker** application using Docker and serve it through Nginx. This approach ensures that the application can be deployed consistently in any environment and accessed via a browser.

---

## Machine Information
- **Operating System**: Ubuntu 22.04 LTS
- **Docker Version**: 27.3.1
- **Nginx Version**: nginx/1.18.0 (Ubuntu)
- **CPU**: Ryzen 5 5500U
- **RAM**: 8GB

---

## Docker Image Creation

### Steps to create the Docker image:
1. **Navigating to the project directory**:
    ```bash
    cd /home/sagar/Desktop/RandomChoicePicker
    ```
    - **Why**: This ensures that you are working in the correct project directory.

2. **Creating the Dockerfile using nano**:
    ```bash
    nano Dockerfile
    ```
    - **Why**: This allows you to define how the Docker image will be built and configured.

3. **Adding content to the Dockerfile**:
    ```dockerfile
    # Use Nginx as the base image
    FROM nginx:alpine

    # Copy the HTML, CSS, and JS files to the Nginx HTML directory

    COPY index.html /usr/share/nginx/html/

    COPY style.css /usr/share/nginx/html/

    COPY script.js /usr/share/nginx/html/

    # Expose port 80 for the Nginx server
    EXPOSE 80
    ```
    - **Why**: The Dockerfile defines the necessary instructions to build an image using Nginx and serve the application.

---

## Running the Docker Container

### Steps to run the container:
1. **Building the Docker image**:
    ```bash
    docker build -t randomchoicepicker .
    ```
    - **Why**: This builds the Docker image using the `Dockerfile` defined earlier.

2. **Running the Docker container**:
    ```bash
    docker run -d -p 8086:80 randomchoicepicker
    ```
    - **Why**: This command runs the container in detached mode, mapping port 8086 on the host to port 80 in the container, so the app is accessible at `http://localhost:8086`.

3. **Accessing the application in the browser**:
    Open the following URL in a web browser:
    ```
    http://localhost:8086
    ```
    - **Why**: This confirms the application is running correctly and accessible via the browser.

---

# Checking Docker Images and Processes

### Steps to verify the image and running container:
1. **Checking Docker images**:
    ```bash
    docker images
    ```
    - **Why**: This confirms that the `randomchoicepicker` image is available on the system.

    Output:
    ```bash
    REPOSITORY             TAG       IMAGE ID       CREATED         SIZE
    randomchoicepicker     latest    5c3a3fbb3635   35 hours ago    52.5MB
    ```

2. **Checking the running Docker container**:
    ```bash
    docker ps
    ```
    - **Why**: This lists the running containers, verifying that the container is up and running.

    Output:
    ```bash
    CONTAINER ID   IMAGE                COMMAND                  CREATED         STATUS         PORTS                                     NAMES
    051a3e8d63ee   randomchoicepicker   "/docker-entrypoint.…"   6 seconds ago   Up 6 seconds   0.0.0.0:8086->80/tcp, [::]:8086->80/tcp   hopeful_fermi
    ```

3. **Checking the container processes**:
    ```bash
    docker top 051a3e8d63ee
    ```
    - **Why**: This shows the running processes inside the container to ensure Nginx is running as expected.

    Output:
    ```bash
    UID                 PID                 PPID                C                   STIME               TTY                 TIME                CMD
    root                4420                4400                0                   10:15               ?                   00:00:00            nginx: master process nginx -g daemon off;
    systemd+            4470                4420                0                   10:15               ?                   00:00:00            nginx: worker process
    ```

4. **Checking system processes**:
    ```bash
    ps aux | grep 4420
    ```
    - **Why**: This shows whether the Nginx master process is running on the host system.

    Output:
    ```bash
    root        4420  0.0  0.0   9444  5248 ?        Ss   10:15   0:00 nginx: master process nginx -g daemon off;
    sagar       4822  0.0  0.0   9080  2432 pts/0    S+   10:17   0:00 grep --color=auto 4420
    ```

---

## Conclusion


**Conclusion**: The Random Choice Picker application has been successfully containerized using Docker and served using Nginx. The setup is working as expected, and the application is accessible via the browser. This implementation ensures easy deployment and scalability of the application in the future.
