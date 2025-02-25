### **6. Docker Compose**

Docker Compose is a powerful tool that simplifies the management of multi-container applications. It allows you to define and orchestrate your containerized services using a simple YAML configuration file.

---

#### **What is Docker Compose?**
- Docker Compose is a tool for defining and running multi-container Docker applications.
- It uses a YAML file (`docker-compose.yml`) to configure application services, networks, and volumes.
- With a single command, you can start, stop, or manage all your services together.

**Use Cases:**
- Applications requiring multiple services (e.g., web server, database).
- Simplifying development and testing environments.
- Streamlining deployments with consistent configurations.

---

#### **Installing Docker Compose**
Docker Compose comes pre-installed with Docker Desktop. To install it separately:

1. **Linux:**
   ```bash
   sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
   sudo chmod +x /usr/local/bin/docker-compose
   docker-compose --version
   ```

2. **macOS and Windows:**  
   Docker Compose is bundled with Docker Desktop. Simply install Docker Desktop and verify with:
   ```bash
   docker-compose --version
   ```

---

#### **Writing a `docker-compose.yml` File**
The core of Docker Compose is the YAML configuration file, which defines all the services, networks, and volumes needed for your application.

**Docker Command:**

```docker run -d --name nginx_container -p 8080:80 nginx:latest```

**Basic Structure:**
```yaml
version: '3.9'

services:
  nginx:
    image: nginx:latest
    container_name: nginx_container
    ports:
      - "8080:80" # Maps port 8080 on the host to port 80 in the container
```

### Explanation:
- **`image: nginx:latest`**: Specifies the Nginx image to use.
- **`container_name: nginx_container`**: Assigns the container a specific name (`nginx_container`).
- **`ports`**: Maps port `8080` on the host to port `80` in the container, allowing access to Nginx.

---

#### **Running Docker Compose**
After creating the `docker-compose.yml` file:

1. **Start Services**:
   ```bash
   docker-compose up
   ```
   - Use `-d` for detached mode:
     ```bash
     docker-compose up -d
     ```

2. **Stop Services**:
   ```bash
   docker-compose down
   ```

3. **View Logs**:
   ```bash
   docker-compose logs
   ```

4. **Execute Commands Inside a Service**:
   ```bash
   docker-compose exec app sh
   ```

5. **Rebuild Services**:
   If changes are made to the Dockerfile:
   ```bash
   docker-compose up --build
   ```

---

#### **Managing Multi-Container Applications**
**Example Application: WordPress with MySQL**

`docker-compose.yml`:
```yaml
version: "3.8"
services:
  wordpress:
    image: wordpress:latest
    ports:
      - "8000:80"
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: root
      WORDPRESS_DB_PASSWORD: rootpassword
      WORDPRESS_DB_NAME: wordpress
    networks:
      - wordpress-network

  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: wordpress
    networks:
      - wordpress-network

networks:
  wordpress-network:
```

**Steps to Run:**
1. Save the file as `docker-compose.yml`.
2. Start the application:
   ```bash
   docker-compose up -d
   ```
3. Access WordPress at `http://localhost:8000`.

---

#### **Docker Compose Commands Overview**
| Command                          | Description                           |
|----------------------------------|---------------------------------------|
| `docker-compose up`              | Start services in the `docker-compose.yml`. |
| `docker-compose down`            | Stop and remove all services.         |
| `docker-compose ps`              | List all running services.            |
| `docker-compose logs`            | View logs of services.                |
| `docker-compose exec <service>`  | Run a command in a running container. |
| `docker-compose build`           | Build or rebuild services.            |

---

#### **Best Practices with Docker Compose**
1. **Use Variables for Configuration**:
   Store sensitive data like passwords in an `.env` file and reference them in the `docker-compose.yml` file.
   ```yaml
   environment:
     MYSQL_ROOT_PASSWORD: ${MYSQL_ROOT_PASSWORD}
   ```

2. **Separate Development and Production Files**:
   Maintain separate files for development (`docker-compose.override.yml`) and production settings.

3. **Use Named Volumes**:
   Avoid anonymous volumes for better control:
   ```yaml
   volumes:
     - app-data:/path/to/data
   ```

4. **Optimize Build Context**:
   Use `.dockerignore` to exclude unnecessary files from the build context.

---

#### **Conclusion**
Docker Compose simplifies the orchestration of multi-container applications. It’s an essential tool for developers and DevOps engineers to manage, scale, and deploy containerized services effectively. In the next topic, we’ll dive into **advanced Docker concepts**, including Docker Swarm and Kubernetes. Stay tuned!
