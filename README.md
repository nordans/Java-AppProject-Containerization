# Java-AppProject-Containerization

This project demonstrates containerization of a Java application using Vagrant, Docker Engine, and Docker Compose. A virtual machine with Docker is automatically provisioned, and the application runs in containers with NGINX as a reverse proxy to Tomcat.

## Project Structure

- `DockerEngineMachine/` – contains the `Vagrantfile` that configures the VM and provisions Docker Engine.
- `DockerFiles/` – contains Dockerfiles for application components (NGINX, Tomcat, MySQL).
- `compose.yaml` – defines the services and their configurations using Docker Compose.

## Requirements

- [Vagrant](https://www.vagrantup.com/downloads)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

## Running the Application

1. **Clone the repository and go to the Vagrant directory:**
   ```bash
   git clone https://github.com/nordans/Java-AppProject-Containerization.git
   cd Java-AppProject-Containerization/DockerEngineMachine
   ```

2. **Start the virtual machine with Docker Engine:**
   ```bash
   vagrant up
   ```
   Vagrant will automatically provision a VM with Docker installed.

3. **SSH into the VM:**
   ```bash
   vagrant ssh
   ```

4. **Navigate to the shared directory inside the VM:**
   ```bash
   cd /vagrant
   ```

5. **Build Docker images:**
   ```bash
   docker compose build
   ```

6. **Run the application in detached mode:**
   ```bash
   docker compose up -d
   ```

## Accessing the Application

- The application listens on **port 80** via NGINX reverse proxy.
- To get the VM's IP address, run:
  ```bash
  ip addr show
  ```
  Look for the address assigned to interface `eth1` or `enp0s8`.

- Then access the app in your browser:
  ```
  http://<VM_IP>
  ```

## Architecture

- **NGINX** – reverse proxy on port 80.
- **Tomcat** – hosts the Java application, receives traffic from NGINX.
- **MySQL** – database for the application.
- **Docker Compose** – orchestrates service startup.
- **Vagrant** – provisions a ready-to-use Docker environment.

## License

This project is licensed under the MIT License.