# Awesome Docker Compose Stacks

A curated collection of production-ready Docker Compose stacks and service examples designed to get you from zero to running quickly. Each folder contains a self-contained Compose file, with notes on production considerations.

---

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/)

---

### Quick Start

1.  Clone the repository:
    ```sh
    git clone https://github.com/ashish404403/awesome-docker-compose.git
    cd awesome-docker-compose
    ```

2.  Choose a service, navigate to its directory, and run it:
    ```sh
    cd <service-name>
    docker compose up -d
    ```

3.  To stop and remove containers and networks:
    ```sh
    docker compose down
    ```

---

### Best Practices

-   **Health Checks**: Many services include a `healthcheck` to ensure they are running correctly before other services depend on them.
-   **Named Volumes**: Data persistence is handled using named volumes to separate data from the container lifecycle.
-   **Restart Policies**: Services are configured with `restart: unless-stopped` or `restart: always` to ensure they come back up after a daemon or host reboot.
-   **Security**: Be sure to change default credentials and never commit secrets directly into your `docker-compose.yaml` files. Use environment variables or Docker secrets for production.

---

### Troubleshooting Tips

-   **Container fails to start**: Inspect logs with `docker compose logs -f <service-name>`.
-   **Port conflict**: Check `docker ps` for used ports and change the host port mapping in the `docker-compose.yaml` file (e.g., change `"8080:8080"` to `"8081:8080"`).
-   **Persistent data missing**: Ensure volumes are defined and not accidentally removed by running `docker compose down -v`.
-   **Healthcheck failing**: Run the check command manually inside the container to see error details: `docker exec <container_name> <command>`.

---

### Contributing Guidelines

Contributions are welcome! Please feel free to submit a pull request with new services or improvements to existing ones.

-   **Additions**: Add a new service in its own folder with a clear `docker-compose.yaml`.
-   **Quality**: Include healthchecks and persistent volume configurations where applicable.
-   **Security**: Never commit secrets, API keys, or private certificates. Use placeholders or comments to indicate where they should go.
-   **Pull Request Checklist**:
    -   The service runs with `docker compose up -d` on a fresh host.

---

### License

This project is open-source and available under the **MIT License**. Feel free to reuse and adapt these Compose stacks in your projects.
