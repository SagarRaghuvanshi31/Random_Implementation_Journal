# Simple Implementation Journal for Random Choice Picker Application

## Table of Contents
1. [Objective](#objective)
2. [Machine Information](#machine-information)
3. [1. Creating the Dockerfile](#1-creating-the-dockerfile)
4. [2. Building the Docker Image](#2-building-the-docker-image)
5. [3. Running the Docker Container](#3-running-the-docker-container)
6. [4. Checking Docker Images and Processes](#4-checking-docker-images-and-processes)
7. [Conclusion](#conclusion)

---

## Objective
The objective of this implementation is to containerize the Random Choice Picker application using Docker and Nginx. The goal is to ensure the application can be easily deployed and accessed via a web browser by creating a Docker image and running it in a container, using Nginx to serve the application.

---

## Machine Information
- **Operating System**: Ubuntu 22.04 LTS
- **Docker Version**: 20.10.8
- **Nginx Version**: 1.21.3
- **CPU**: Intel Core i5-8250U
- **RAM**: 8GB

---

## 1. Creating the Dockerfile
**Objective**: Create a Dockerfile to containerize the Random Choice Picker application and serve it using Nginx.

### Steps:
- Navigated to the project directory:
    ```bash
    cd /home/sagar/Desktop/RandomChoicePicker
    ```
    - **Why**: This step ensures that you're working in the correct project directory where the application files are located.

- Created the Dockerfile using nano:
    ```bash
    nano Dockerfile
    ```
    - **Why**: The Dockerfile defines the environment and instructions to build a container that can run the Random Choice Picker app.

- Added the following content to the Dockerfile:
    ```dockerfile
    # Use Nginx as the base image
    FROM nginx:alpine

    # Copy project files to Nginx's HTML directory
    COPY . /usr/share/nginx/html

    # Expose port 80 for the Nginx server
    EXPOSE 80
    ```
    - **Why**: The Dockerfile specifies the Nginx image, copies the application files to the proper directory for serving, and exposes port 80 to make the app accessible via HTTP.

---

## 2. Building the Docker Image
**Objective**: Build the Docker image for the Random Choice Picker application.

### Steps:
- Ran the following command to build the image:
    ```bash
    docker build -t randomchoicepicker .
    ```
    - **Why**: This command creates the Docker image by following the instructions in the Dockerfile, making the application ready to run in a container.

- Verified the image creation:
    ```bash
    docker images
    ```
    - **Why**: Verifying the image ensures that the build process completed successfully and the image is available for use.

---

## 3. Running the Docker Container
**Objective**: Run the container and serve the Random Choice Picker application using Nginx.

### Steps:
- Started the container, mapping port 8080 on the host to port 80 in the container:
    ```bash
    docker run -d -p 8080:80 randomchoicepicker
    ```
    - **Why**: This command runs the container in detached mode and maps the container's internal port 80 to the host's port 8080, making the app accessible via `http://localhost:8080`.

- Accessed the application in a web browser:
    ```text
    http://localhost:8080
    ```
    - **Why**: Opening the application in a browser confirms that the container is running and serving the app correctly.

---

## 4. Checking Docker Images and Processes
**Objective**: Ensure the Docker image is created and running correctly.

### Steps:
- Checked the Docker images to verify the image is available:
    ```bash
    docker images
    ```
    - **Why**: This command shows all available Docker images, ensuring that the `randomchoicepicker` image exists after the build process.
  
- Checked the running containers to confirm that the container is running:
    ```bash
    docker ps
    ```
    - **Why**: This command lists the currently running containers, allowing you to confirm that the container is up and running.

- Stopped the container if needed:
    ```bash
    docker stop <container_id>
    ```
    - **Why**: This command stops a running container when you need to make changes or troubleshoot.

---

## Conclusion
| **Step**                         | **Outcome** |
|----------------------------------|-------------|
| **Creating the Dockerfile**      | Successfully created a Dockerfile that defines the environment and serves the app using Nginx. |
| **Building the Docker Image**    | The image was successfully built and verified. |
| **Running the Docker Container** | The container was successfully started, and the app is accessible via the browser. |
| **Checking Docker Images and Processes** | Verified that the image and container are correctly running. |

**Conclusion**: The Random Choice Picker application was successfully containerized using Docker and served using Nginx. The steps outlined ensure that the app can be easily deployed and accessed in a consistent environment. The image and container have been verified to be working as expected, and the setup is ready for future enhancements.
