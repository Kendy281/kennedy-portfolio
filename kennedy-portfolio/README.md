# Kwao Kennedy — Portfolio Website

A responsive, static portfolio website built with HTML, CSS, and a small amount of JavaScript. It is designed to run in Docker on a Linux VPS.

## Before publishing

1. Open `index.html`.
2. Replace `YOUR_EMAIL@example.com` with the email address you want to publish.
3. Review the role/experience descriptions and adjust anything you want to be more precise.
4. Keep confidential employer information, internal architecture, credentials, and private dashboards off the public site.

## Run locally with Docker

```bash
docker build -t kennedy-portfolio:v1 .
docker run -d --name kennedy-portfolio --restart unless-stopped -p 8080:80 kennedy-portfolio:v1
```

Visit `http://localhost:8080`.

## Deploy to your VPS

This is intended to coexist with your existing operations lab app on port 5000. The Compose file exposes the portfolio on port 8080.

1. Copy this folder to your VPS (or clone a repository containing it).
2. From the folder, run:

```bash
sudo docker compose up -d --build
sudo docker ps
```

3. Visit `http://YOUR_VPS_IP:8080`. If it does not load, check the VPS firewall/provider firewall and allow inbound TCP 8080.

### If Docker Compose is unavailable

```bash
sudo docker build -t kennedy-portfolio:v1 .
sudo docker run -d --name kennedy-portfolio --restart unless-stopped -p 8080:80 kennedy-portfolio:v1
```

### Useful operations

```bash
sudo docker logs -f kennedy-portfolio
sudo docker restart kennedy-portfolio
sudo docker stop kennedy-portfolio
sudo docker start kennedy-portfolio
sudo docker rm -f kennedy-portfolio
```

## Public hosting notes

- Port 8080 is used to avoid colliding with the Flask operations lab currently using port 5000.
- For a polished public deployment, use a domain and HTTPS through a reverse proxy such as Caddy or Nginx Proxy Manager. Do not expose admin services or databases publicly.
- The current version uses a placeholder email link. Replace it before launch.
