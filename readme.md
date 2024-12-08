# Private SeedBox (Simplified Deployment)

## Overview

This project sets up a **Private SeedBox** on your own server using **Transmission** for torrent downloading and **FileBrowser** for file management. **Nginx** is used as a reverse proxy to enable secure HTTPS access to both services using Cloudflare SSL certificates.

With this setup, you can:
- **Download torrents privately** and securely on your own server.
- **Manage downloaded files** via a simple web interface (FileBrowser).
- **Access all services securely** using HTTPS without manual configuration.

---

## Key Features
- **No Manual Configuration**: Automatic setup with GitHub Actions and Docker Compose.
- **Customizable**: Users can fork and adjust the repository as needed.
- **Secure Access**: Services are secured using HTTPS with Cloudflare SSL.

---

## Requirements
- A **Linux server**
- A **Domain Attached with Cloudflare** 

---

## Getting Started

Follow these steps to deploy the environment on your server:

### Step 1: Fork the Repository

1. Fork this [Private-Torrent-Downloader](https://github.com/pasinduljay/Fully-Automated-Private-SeedBox/fork) to your own GitHub account.

### Step 2: Set Up Your Server

1. Create a **Linux server** (Ubuntu recommended) with the following specifications:
   - Username: `ubuntu` (default).  
     **Note**: If you use a different username, update all file paths in the repository to reflect the new username.
   - Ensure **port 443** is open in the server for public HTTPS access.

2. Get the server's public IP address.

### Step 3: Update the GitHub Workflow

1. In your forked repository, navigate to `.github/workflows/deploy.yml`.
2. Replace the existing `INSTANCE_IP` with your server's public IP address.

### Step 4: Configure GitHub Secrets

Set up the required GitHub secrets to enable automatic deployment:
1. Go to **Settings > Secrets > Actions** in your forked repository.
2. Add the following secrets:
   - `SSH_PRIVATE_KEY`: The private key for SSH access to your server.
   - `GHUB_USERNAME`: Your GitHub username.
   - `TOKEN`: Your GitHub personal access token.
   - `SSL_CERT`: Your Cloudflare SSL certificate.
   - `SSL_KEY`: Your Cloudflare SSL private key.

### Step 5: Deploy the Environment

1. Commit and push any changes to your forked repository.
2. GitHub Actions will automatically trigger the deployment process. Wait for the workflow to complete.

---

## Accessing the Services

Once the deployment is complete, access the services using your server's IP address or domain name:

- **Transmission**: Access the torrent downloader at `https://your-server-ip/transmission`.
- **FileBrowser**: Access the file manager at `https://your-server-ip/filebrowser`.

---

## Default Credentials

### FileBrowser
- **Username**: `admin`
- **Password**: `admin`

**Important**: Change the password upon first login for security.

---

## Docker Compose Overview

### Transmission
- **Purpose**: Torrent client for downloading torrents.
- **Port**: Exposed internally for reverse proxy.
- **Volume Mounts**:
  - `/downloads`: Directory for downloaded files.
  - `/config`: Configuration files.

### FileBrowser
- **Purpose**: Web-based file manager for managing downloaded files.
- **Volume Mounts**:
  - `/srv`: Directory shared with Transmission.

### Nginx
- **Purpose**: Reverse proxy for secure access to both services.
- **Features**:
  - Configured for HTTPS using Cloudflare SSL.
  - Automatically proxies `Transmission` and `FileBrowser`.

---

## Notes
1. This setup automates everything; no manual configuration is required after pushing the changes.
2. Ensure your server has **Docker** and **Docker Compose** installed. The setup script verifies and installs them if needed.
3. If you need to customize the username or paths, update all file paths in the repository accordingly.

Enjoy your secure, private torrent downloader and file manager!

---
<br><br>

# 💰 You can help me by Donating
<img align="center" alt="Coding" width="400" src="https://github.com/pasinduljay/pasinduljay/blob/main/Resources/user2.gif">

<a href="https://buymeacoffee.com/pasinduljay" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" height="50px" ></a>
<a href="https://paypal.me/980822" target="_blank"><img src="https://img.shields.io/badge/PayPal-00457C?style=for-the-badge&logo=paypal&logoColor=white" alt="Buy Me A Coffee" height="50px" >
<br><br>