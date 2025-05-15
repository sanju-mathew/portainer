# 🧭 Portainer with Traefik Reverse Proxy

This repository contains a setup to run [Portainer CE](https://www.portainer.io/) behind a Traefik reverse proxy with secure HTTPS access and automatic redirect from HTTP.

---

## 🚀 Overview

Portainer provides a simple UI to manage Docker environments. In this setup, it's securely exposed through Traefik with TLS support and external access via a custom domain.

---

## 🗂️ Services

- **Portainer CE** — Web-based Docker management UI  
- **Traefik** — Reverse proxy and automatic SSL management (pre-configured via labels)

---

## 🛠️ Configuration Notes

- Portainer is deployed as a Docker container.
- It mounts the Docker socket for full Docker control and stores data in a persistent volume.
- The service is attached to a shared `proxy` network used by Traefik.
- Labels configure routing:
  - HTTPS redirection from HTTP
  - TLS termination with automatic certificates
  - Host-based routing (e.g., `portainer.example.com`)

> 🔐 Replace `portainer.example.com` with your actual domain  
> 🏠 Replace `/home/your-user/portainer/data` with your actual home directory

---

## ✅ Prerequisites

- Docker & Docker Compose installed
- Traefik already running with an external `proxy` network
- DNS records pointing `portainer.example.com` to your server
- TLS configured via Let's Encrypt (Traefik handles this)

---

## 🧑‍💻 Usage

Bring up the stack:

```bash
docker compose up -d
