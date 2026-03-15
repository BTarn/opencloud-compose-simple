# OpenCloud Compose

This repository provides Docker Compose configurations for deploying OpenCloud in various environments.

> [!IMPORTANT]
> Please use the [official docs](https://docs.opencloud.eu/docs/admin/getting-started/container/docker-compose/docker-compose-base) for a **Production Deployment**.

## Overview

OpenCloud Compose offers a modular approach to deploying OpenCloud with several configuration options:

- **Standard deployment** with Traefik reverse proxy and Let's Encrypt certificates or certificates from files
- **External proxy** support for environments with existing reverse proxies (like Nginx, Caddy, etc.)
- **Collabora Online** integration for document editing
- **Keycloak and LDAP** integration for centralized identity management
- **Full text search** with Apache Tika for content extraction and metadata analysis
- **Monitoring** with metrics endpoints for observability and performance monitoring
- **Radicale** integration for Calendar and Contacts
- **ClamAV** antivirus scanning with ClamAV

## Quick Start Guide

### Prerequisites

- Docker and Docker Compose v2 installed.
- Domain names pointing to your server (for production deployment)
- Basic understanding of Docker Compose concepts

> [!IMPORTANT]
> Please use the docker installation guide from the [Official Documentation](https://docs.docker.com/engine/install/) to ensure using docker compose v2. Official linux distro package repositories might still contain docker compose v1, e.g. Debian 12 "Bookworm". Using docker compose v1 will lead to a broken docker deployment.

### Local Development

1. **Clone the repository**:
   ```bash
   git clone https://github.com/BTarn/opencloud-compose-simple.git
   mv opencloud-compose-simple openclud
   cd opencloud
   ```

2. **Create folder for mounting volumns**:
   ```bash
   mkdir config
   mkdir lib
   chmod 777 config
   chmod 777 lib
   ```

3. **Set admin password**:
   set `IDM_ADMIN_PASSWORD=your_secure_password` environment variable in `docker-compose.yml` file
4. **Domain**:
   set `OC_URL=your_https_url` environment variable in `docker-compose.yml` file
5. **Configure deployment options**:

   Then simply run:
   ```bash
   docker compose up -d
   ```

6. **Access OpenCloud**:
   - URL: your_https_url
   - Username: `admin`
   - Password: value of your `IDM_ADMIN_PASSWORD`

