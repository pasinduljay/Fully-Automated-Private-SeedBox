# Private Torrent Downloader with File Server

## Overview

This project sets up a **Private Torrent Downloader** on your server using **Transmission** for torrent downloading and **FileBrowser** for file management. **Nginx Proxy Manager** provides secure, easy access with HTTPS to both services.

With this setup, you can:
- **Download torrents** privately and securely on your own server.
- **Manage your downloaded files** with a simple web interface (FileBrowser).
- **Access all services securely** through Nginx Proxy Manager with HTTPS.

## Advantages
- **Privacy & Control**: Full control over your environment ensures privacy and avoids third-party clients.
- **Seamless Access**: User-friendly experience with Transmission, FileBrowser, and Nginx Proxy Manager.
- **Web-Based Management**: Both Transmission and FileBrowser are accessible through a web interface.
- **Enhanced Security**: Nginx Proxy Manager enables secure access to services via HTTPS.

## Requirements
- A **Linux server** with Docker and Docker Compose installed.
- A **GitHub account** for repository management.
- A **domain** for Nginx Proxy Manager setup (optional but recommended).

---
## Accessing the Services

- **Transmission**: Access your torrent downloader via [https://tor.techdevops.me](https://tor.techdevops.me)
- **FileBrowser**: Access your file manager via [https://download.techdevops.me](https://download.techdevops.me)

---
## Set up your own environment similar to this, follow these steps :


### Step 1: Fork and Clone the Repository
1. Fork the [Private-Torrent-Downloader](https://github.com/pasinduljay/Private-Torrent-Downlaoder-using-FileBrowser) repository on GitHub.

### Step 2: Configure GitHub Secrets
Set up GitHub secrets for automatic deployment:
1. Navigate to **Settings > Secrets > Actions** in your GitHub repository.
2. Add the following secrets:
   - `SSH_PRIVATE_KEY`: Your private SSH key for server access.
   - `GHUB_USERNAME`: Your GitHub username.
   - `TOKEN`: Your GitHub personal access token.

### Step 3: Configure `deploy.yml`
In `.github/workflows/deploy.yml`, set the following environment variables:
- `INSTANCE_IP`: Your server's IP address.
- `USERNAME`: Your server's username, usually `ubuntu`.

Ensure SSH access is configured by adding your public key to `~/.ssh/authorized_keys` on the server.

### Step 4: Trigger Deployment
Pushing changes to the main branch will automatically trigger the deployment process.

### Step 5: Configure Nginx Proxy Manager
Once deployment is complete, access Nginx Proxy Manager at `http://your-server-ip:81`.
1. Log in with default credentials:
   - **Email**: `admin@example.com`
   - **Password**: `changeme`
2. Set up a new admin user.
3. Add proxy hosts for Transmission and FileBrowser:
   - **Transmission**: Proxy host on port `9091`.
   - **FileBrowser**: Proxy host on port `80`.
4. Enable SSL with Let's Encrypt for HTTPS.

### Step 6: Access Transmission and FileBrowser
Access your services via the configured domain or IP:
- **Transmission**: `https://your-domain/transmission`
- **FileBrowser**: `https://your-domain/filebrowser`

### Step 7: Default Login for FileBrowser
Log in to FileBrowser with default credentials:
- **Username**: `admin`
- **Password**: `admin`

Change the password upon first login for security.

## Docker Compose Overview

### Transmission
- **Image**: `pasinduljay/transmission:1.1`
- **Purpose**: Torrent client for downloading torrents.
- **Volume Mounts**:
  - `/downloads`: Directory for downloaded files.
  - `/config`: Configuration files.

### FileBrowser
- **Image**: `pasinduljay/filebrowser:1.1`
- **Purpose**: Web-based file manager for managing downloaded files.
- **Volume Mounts**:
  - `/srv`: Directory shared with Transmission.

### Nginx Proxy Manager
- **Image**: `pasinduljay/nginx-proxy-manager:1.1`
- **Purpose**: Manage access with SSL-enabled proxy hosts.
