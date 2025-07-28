# 🛠️ Home Server Compose Files

This repository contains the Docker Compose configuration files for all services running on my home server. It acts as a backup and source of truth for recovery, re-deployment, and documentation of my homelab setup.

---

## 📦 Purpose

This repo is **not meant to run all services at once**, but instead stores each service's Compose file in its own folder. It ensures:

- Easy disaster recovery  
- Version control of configuration  
- Quick reference for manual or automated redeployments

---

## 📁 Structure

Each subfolder in `/opt/stacks/` represents a self-contained service (e.g. `jellyfin/`, `radarr/`, `uptime-kuma/`), and typically includes:

- `docker-compose.yml`  
- `.env` (if used — private, but can be templated)  
- Optional `README.md` or notes for each service

### Example layout:
```markdown
/opt/stacks/
├── jellyfin/
│   └── docker-compose.yml
├── radarr/
│   └── docker-compose.yml
├── uptime-kuma/
│   └── docker-compose.yml
```
---

## 🔐 Sensitive Info

While this repo may include `.env` files for convenience while private, they will be removed or `.gitignore`-d if the repo is ever made public.

---

## 🚀 Recovery Process

To restore a service:

1. Navigate to the service's folder:
   ```bash
   cd /opt/stacks/<service>
   ```
2. If applicable, copy .env.example to .env and edit it.
3. Start the containers using dockage or:
    ```bash
    docker compose up -d
    ```
---

## 🔄 Update Workflow

I use a custom script to:
	•	Traverse each service folder
	•	Commit and push only changed Compose files
	•	Skip any unchanged folders

This helps keep the repo lightweight and focused on meaningful updates only.

---

## 🧠 Notes

This repo is for personal use and reflects my specific setup.
Feel free to fork or adapt it to match your own homelab layout and service structure.

---
