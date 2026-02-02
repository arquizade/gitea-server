# Gitea Local AI Dev Stack

A self-hosted Git service with CI/CD and AI capabilities using Docker Compose.

## Overview

This project sets up a complete development environment with:

- **Gitea** - Self-hosted Git service with web UI
- **Gitea Runner** - CI/CD automation for your repositories
- **Ollama** - Local AI/LLM service for your projects

## Services

### Gitea
- **Port:** 3000 (HTTP), 2222 (SSH)
- **Database:** SQLite3
- **Data:** `./data/gitea/`
- Access at: `http://localhost:3000`

### Gitea Runner
- **Purpose:** Runs CI/CD workflows for your repositories
- **Configuration:** Connected to Gitea via `http://gitea:3000`
- **Data:** `./runner-data/`

### Ollama
- **Purpose:** Local AI/LLM service
- **Models:** Stored in `./ollama/models/`

## Getting Started

### Prerequisites
- Docker
- Docker Compose

### Starting the Services

```bash
docker-compose up -d
```

### Initial Access

1. Open `http://localhost:3000` in your browser
2. Complete the Gitea setup wizard
3. Create your first repository or user account

### SSH Access

To push/pull via SSH:
```bash
git clone ssh://git@localhost:2222/username/repo.git
```

## Directory Structure

```
├── data/                # Gitea data (git repos, configs, database)
├── ollama/              # Ollama models and configuration
├── runner-data/         # Gitea Runner state and configuration
└── docker-compose.yml   # Service definitions
```

## Configuration

Edit `docker-compose.yml` to customize:
- Port numbers
- Environment variables
- Volume mounts
- Resource limits

For Gitea-specific settings, edit `data/gitea/conf/app.ini` after initial setup.

## Useful Commands

```bash
# Start services
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs -f gitea

# Access Gitea container
docker-compose exec gitea bash
```

## Networking

All services communicate over the internal `gitea` network. This allows the runner and other services to access Gitea at `http://gitea:3000`.

## Documentation

- [Gitea Documentation](https://docs.gitea.io/)
- [Ollama Documentation](https://ollama.ai/)
