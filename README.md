# Docker Compose SonarQube Setup

Ready-to-use Docker Compose setup for launching SonarQube with a PostgreSQL database.

## Usage

### Setup

After cloning this repository, you must copy `env.example` to `.env` and customize it as needed. The file contains the following environment variables:

- `EXPOSE_SONAR`: The port on which SonarQube will be accessible
- `POSTGRES_DB`: The name of the PostgreSQL database to create
- `POSTGRES_MAX_CONNECTIONS`: The maximum number of connections for the PostgreSQL database
- `POSTGRES_PASSWORD`: The password for the PostgreSQL database
- `POSTGRES_SHARED_BUFFERS`: The shared buffers setting for the PostgreSQL database
- `POSTGRES_USER`: The username for the PostgreSQL database
- `PROJECT_NAME`: The name of the project (used for naming the Docker containers)

### Startup

Once the secrets are generated and the `.env` file is configured, you can start the services by executing the following
command:

```bash
docker compose -f docker-compose.yml --env-file .env up -d
```

To stop the services, you can execute the following command:

```bash
docker compose -f docker-compose.yml --env-file .env down
```

To stop the services and remove the volumes, you can execute the following command:

```bash
docker compose -f docker-compose.yml --env-file .env down -v
```

To recreate the containers, you can execute the following command:

```bash
docker compose -f docker-compose.yml --env-file .env up -d --force-recreate
```

### Connexion

Open your web browser and navigate to `http://localhost:${EXPOSE_SONAR}` to access the SonarQube interface.
By default the SonarQube interface uses the following credentials:

- Username: `admin`
- Password: `admin`

You should change the default password after the first login for security reasons.
