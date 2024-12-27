### 2. Getting Started with Docker

#### **Understanding Docker CLI**
The Docker Command Line Interface (CLI) is a tool used to interact with Docker. With Docker CLI, you can run commands to manage containers, images, networks, and volumes.

- **Purpose**: The CLI serves as a bridge between you and the Docker engine.
- **Basic Commands**: Docker provides a wide range of commands, but let’s start with a few key ones:
  - `docker version` - Displays the Docker version installed.
  - `docker info` - Provides system-wide information about Docker.
  - `docker help` - Lists available Docker commands.

#### **First Steps: Running Your First Container**
To experience Docker in action, let’s run a simple container.

- **Step 1**: Open your terminal (or PowerShell on Windows).
- **Step 2**: Run the following command:
  ```bash
  docker run hello-world
  ```
- **What’s Happening?**
  - Docker searches for the **hello-world** image locally. If it doesn’t find it, it pulls the image from **Docker Hub** and runs a container based on that image.
  - The container prints a message to confirm that Docker is running correctly.

- **Explanation**: This command illustrates the basic workflow of pulling an image and creating a container.

#### **Pulling Images from Docker Hub**
Docker Hub is a public repository that hosts thousands of pre-built Docker images for various applications and systems.

- **Searching for an Image**:
  ```bash
  docker search nginx
  ```
  This command searches Docker Hub for images related to "nginx."

- **Pulling an Image**:
  ```bash
  docker pull nginx
  ```
  This command pulls the **nginx** image from Docker Hub onto your local system.

- **Tip**: When you pull an image, you’re essentially downloading it for use in future containers.

#### **Basic Docker Commands**
Once you’ve run your first container and pulled images, it’s time to explore some basic commands for container management:

1. **`docker run`**:
   - Used to create and start a new container from an image.
   - Example:
     ```bash
     docker run -d -p 80:80 nginx
     ```
     This command runs an **nginx** container in detached mode (`-d`) and maps port 80 of your machine to port 80 in the container (`-p 80:80`).

2. **`docker ps`**:
   - Lists all running containers.
   - Example:
     ```bash
     docker ps
     ```

3. **`docker stop`**:
   - Stops a running container.
   - Example:
     ```bash
     docker stop <container-id>
     ```

4. **`docker rm`**:
   - Removes a stopped container.
   - Example:
     ```bash
     docker rm <container-id>
     ```

#### **Practical Examples of Each Command**
Let’s put these commands into practice:

1. **Running a Container**:
   ```bash
   docker run -d --name webserver -p 8080:80 nginx
   ```
   This command:
   - Runs an **nginx** container in detached mode.
   - Names the container **webserver**.
   - Maps port 8080 on your machine to port 80 inside the container.

2. **Listing Containers**:
   ```bash
   docker ps
   ```
   You’ll see a list of running containers along with their details like container ID, names, and ports.

3. **Stopping and Removing a Container**:
   ```bash
   docker stop webserver
   docker rm webserver
   ```

4. **Listing and Removing Images**:
   ```bash
   docker images
   docker rmi nginx
   ```

#### **Conclusion of Topic 2**
By the end of this section, you should have a clear understanding of the Docker CLI and be able to run, stop, and manage containers effectively. This foundational knowledge is crucial for moving on to more advanced Docker features.

If you want to dive deeper into a specific command or concept, let me know, and I can provide additional details!
