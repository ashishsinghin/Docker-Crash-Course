### 3. Working with Docker Images

#### **What is a Docker Image?**
A Docker image is a lightweight, standalone, and executable software package that includes everything needed to run a piece of software: code, runtime, libraries, environment variables, and configuration files.

- **Definition**: Think of a Docker image as a blueprint for creating containers. It contains all the instructions needed to set up an application environment.
- **Layers and Union File System**: 
  - **Layers**: Each instruction in a Dockerfile creates a layer in the Docker image. These layers are stacked on top of each other to form a complete image.
  - **Union File System**: Docker uses a union file system to manage these layers efficiently. It allows for reusability and minimal storage usage since layers can be shared across images.

---

#### **Creating Custom Docker Images**
To create your own Docker image, you’ll need to write a **Dockerfile**, which is a script of instructions used to build a Docker image. Let’s break down how to write and use a Dockerfile.

##### **Step-by-Step Guide to Writing a Dockerfile**
1. **Create a file named `Dockerfile`** in your project directory.
2. **Write instructions in the Dockerfile** to specify how the image should be built.

Here are some common instructions used in a Dockerfile:

- **`FROM`**: Specifies the base image to use for creating the new image. For example:
  ```Dockerfile
  FROM ubuntu:20.04
  ```
- **`RUN`**: Executes commands inside the image during the build process. For example:
  ```Dockerfile
  RUN apt-get update && apt-get install -y nginx
  ```
- **`CMD`**: Specifies the command to run when the container starts. For example:
  ```Dockerfile
  CMD ["nginx", "-g", "daemon off;"]
  ```
- **`COPY`**: Copies files or directories from your host system into the image. For example:
  ```Dockerfile
  COPY . /usr/share/nginx/html
  ```
- **`EXPOSE`**: Documents which ports the container listens on. For example:
  ```Dockerfile
  EXPOSE 80
  ```

---

#### **Building an Image**
Once your Dockerfile is ready, you can build your custom Docker image using the `docker build` command.

- **Syntax**:
  ```bash
  docker build -t my-custom-image .
  ```
  - `-t` option allows you to name the image (e.g., `my-custom-image`).
  - The `.` specifies the build context, which is the current directory.

- **Explanation of Build Context**:
  - The build context is the set of files that Docker needs to build your image. It’s defined by the directory you specify when running `docker build`.

##### **Example**: Building a Simple Nginx Image
1. **Dockerfile**:
   ```Dockerfile
   FROM nginx:latest
   COPY . /usr/share/nginx/html
   EXPOSE 80
   CMD ["nginx", "-g", "daemon off;"]
   ```
2. **Build Command**:
   ```bash
   docker build -t my-nginx-image .
   ```

---

#### **Managing Docker Images**
Once you have your images, Docker provides several commands to manage them.

1. **Listing Images**:
   ```bash
   docker images
   ```
   - This command lists all the images on your local system, showing details like repository, tag, and image ID.

2. **Removing Images**:
   ```bash
   docker rmi <image-id>
   ```
   - Use this command to delete an image by specifying its image ID. Be cautious, as removing an image will also remove all containers based on that image.

3. **Tagging Images for Versioning**:
   - You can tag your images to keep track of different versions:
     ```bash
     docker tag my-nginx-image my-nginx-image:v1.0
     ```
   - This makes it easier to manage and deploy specific versions of your application.

---

#### **Conclusion of Topic 3**
By understanding Docker images, how to create custom images using Dockerfiles, and how to manage them, you are well on your way to mastering Docker. In the next section, we’ll dive into Docker networking and how to connect containers together.

Feel free to ask for more examples or clarifications on any specific part of working with Docker images!
