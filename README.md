# GenAI-202511-Week10
A docker environment to host n8n

## Overview

This repository provides a Docker setup to run n8n (a low-code workflow automation platform) locally. n8n allows you to create complex automations and integrations without extensive coding.

## Prerequisites

- Docker installed on your system ([Install Docker](https://docs.docker.com/get-docker/))
- Docker Compose installed ([Install Docker Compose](https://docs.docker.com/compose/install/))
- Port 5678 available on your machine

## Quick Start

### 1. Start n8n

```bash
cd /workspaces/GenAI-202511-Week10
docker-compose up -d
```

### 2. Access n8n

Open your browser and navigate to:
```
http://localhost:5678
```

## Usage

### View Logs

To see real-time logs from the n8n container:

```bash
docker-compose logs -f n8n
```

### Stop n8n

To stop the running container:

```bash
docker-compose stop
```

### Stop and Remove

To completely remove the container (data persists in the volume):

```bash
docker-compose down
```

### Check Status

To view the status of running containers:

```bash
docker-compose ps
```

### Restart n8n

To restart the container:

```bash
docker-compose restart n8n
```

## Configuration

The Docker Compose setup includes the following configuration:

- **Image**: Latest n8n image (`n8nio/n8n:latest`)
- **Port**: 5678 (web interface)
- **Host**: localhost
- **Protocol**: HTTP
- **Environment**: Production
- **Restart Policy**: Auto-restart unless manually stopped
- **Data Volume**: `n8n_data` for persistent storage

### Environment Variables

Key environment variables in the `docker-compose.yml`:

- `N8N_HOST=localhost` - Server host
- `N8N_PORT=5678` - Server port
- `N8N_PROTOCOL=http` - Protocol (change to `https` if using SSL)
- `NODE_ENV=production` - Environment mode

To add or modify environment variables, edit the `environment` section in `docker-compose.yml`.

## Data Persistence

All n8n data (workflows, executions, settings) is stored in the `n8n_data` Docker volume. This ensures your data persists even if the container is stopped or removed.

To view the volume:

```bash
docker volume ls | grep n8n
```

## Troubleshooting

### Port 5678 Already in Use

If port 5678 is already in use, modify the `docker-compose.yml` file:

```yaml
ports:
  - "YOUR_PORT:5678"
```

Replace `YOUR_PORT` with an available port (e.g., 8080).

### Container Won't Start

Check the logs:

```bash
docker-compose logs n8n
```

### Data Not Persisting

Ensure the volume is properly configured and Docker has write permissions to the volume location.

## Next Steps

- Visit the [n8n Documentation](https://docs.n8n.io/)
- Explore [n8n Templates](https://n8n.io/workflows/)
- Connect external services and build your first workflow

## Additional Resources

- [n8n GitHub Repository](https://github.com/n8n-io/n8n)
- [Docker Documentation](https://docs.docker.com/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)

## License

This project includes Docker configuration for running n8n. See n8n's license for details on the n8n software itself.
