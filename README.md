# 📬 Roundcube Mail with Docker and Local DNS Server for `mail.izv.ies`

This repository allows you to run **Roundcube Webmail** locally using Docker, alongside a DNS server configured to resolve the mail server at the domain `mail.izv.ies`. This setup is ideal for local development or testing environments where you want a self-contained mail client environment with proper DNS resolution.

---

## 🚀 Features

- Runs **Roundcube** mail client inside a Docker container.
- DNS server running locally to resolve `mail.izv.ies` to the mail server container.
- Fully containerized setup using Docker and Docker Compose.
- Easy to start, stop, and configure.

---

## 🛠️ Prerequisites

- Docker (version 20.10+ recommended)
- Docker Compose
- Basic understanding of Docker and DNS

---

## Getting Started

### 1. Clone the repository

```bash
git clone <repo-url>
cd roundcube-docker-dns-server-main
```

### 2. Edit docker-compose.yml for adding email users and passwords. The users' passwords must contain at least 2 numbers to be valid.

```bash
    environment:
      - ADMIN_USERNAME=root
      - ADMIN_PASSWD=password
      - DOMAIN_NAME=izv.ies
      - USERS=user1:pass11,user2:pass22
```

### 3. Build and start the Docker containers

```bash
docker-compose up --build -d
```

This command will:

🏗️ Build the Roundcube Docker image if necessary.

▶️ Start the Roundcube webmail container.

🌐 Start the DNS server container configured to resolve mail.izv.ies.

### 4. Set the main DNS server in the host computer to 127.0.0.1

### 5. Access Roundcube

Open your browser and go to:

```
http://mail.izv.ies
```

🔐 Login using your user credentials configured for your mail server.
```
user1@izv.ies + pass11
```

---

## 🌍 DNS Configuration

The DNS server container included in this setup ensures that the hostname `mail.izv.ies` resolves correctly to the mail server container IP address. This is necessary for Roundcube to locate the mail server.

If you want to add other local DNS mappings or customize the domain, you can modify the DNS server configuration files inside the repository.

---

## ⚙️ Configuration

- **Roundcube config:**  in docker-compose.yml, set the environment variables needed.
- **DNS server config:** inside the `dns/` folder.

You can edit these files to match your environment, mail server details, and domain names.

---

## Stopping the Containers

To stop and remove the containers, run:

```bash
docker-compose down
```

---

## Troubleshooting

- Make sure Docker and Docker Compose are installed and running.
- Check Docker container logs for errors:

  ```bash
  docker-compose logs
  ```
- Ensure no other services are conflicting with ports 53 (DNS) or 25,80,110,143,965,993,995 (Roundcube).

---

## License

This project is licensed under the MIT License.

---

## Author

Jorge Del Rey Prieto
