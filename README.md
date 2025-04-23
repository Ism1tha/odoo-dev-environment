# 🚀 Odoo development starter template

This is a Docker-based development environment for Odoo, designed to help you **kickstart your custom Odoo module development** with minimal setup. It includes PostgreSQL, volume persistence, secrets management, and mounts for custom configuration and addons.

---

## 📦 What's Inside

- **Odoo (latest)** with developer mode and auto-update enabled.
- **PostgreSQL 15** as the database backend.
- **Docker secrets** for safe password management.
- **Volume mounts** for configuration, extra addons, and persistent data.
- **Example addon** support: just drop your modules inside `./addons`.

---

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone git@github.com:Ism1tha/odoo-environment-template.git
cd odoo-environment-template
```

### 2. Add the PostgreSQL Password Secret

This project uses Docker secrets. You must include a file named `odoo_pg_pass` at the root of the project containing your PostgreSQL password (no newline at the end).

If you are uploading it directly, make sure it's securely stored and not exposed publicly.

Example content of `odoo_pg_pass`:

```
your_strong_password
```

### 3. Launch the Environment

```bash
docker compose up -d
```

> The first launch might take a bit while images are downloaded and Odoo is initialized.

---

## 🔧 Configuration Overview

| Path / Variable   | Description                             |
| ----------------- | --------------------------------------- |
| `./addons/`       | Your custom Odoo modules go here        |
| `./config/`       | Optional Odoo configuration directory   |
| `8069`            | Port exposed for accessing Odoo         |
| `demo_enterprise` | Default database name (used on startup) |
| `odoo_pg_pass`    | File containing the PostgreSQL password |

---

## 📂 Directory Structure

```
.
├── addons/                 # Your custom addons
├── config/                 # (Optional) Odoo config files
├── odoo_pg_pass            # Secret password file (now included)
└── docker-compose.yml
```

---

## 🛠️ Developer Mode

The Odoo container runs with:

```bash
odoo -d demo_enterprise --update=all --dev=all
```

This enables full developer tools and updates all modules at startup. Useful during development.

---

## 🧼 Stop & Clean Up

To stop and remove containers, volumes, and networks:

```bash
docker compose down -v
```

---

## 📣 Notes

- Make sure `odoo_pg_pass` is stored safely and is not pushed to a public repository.
- Odoo will attempt to use the `demo_enterprise` database. If it doesn't exist, it will try to create it.
- This setup is **not intended for production**.

---

## 📄 License

MIT – do whatever you want, just don’t blame me if your Odoo breaks 😉

---

Happy coding!
