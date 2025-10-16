# HNG13 Stage 0 DevOps Task 🚀

## 📜 Project Overview

This repository contains the solution for the Stage 0 DevOps task as part of the HNG Internship (HNG13). The objective was to deploy a simple NGINX web server on a cloud platform, make it publicly accessible, and serve a custom HTML page. This project demonstrates foundational DevOps skills including cloud infrastructure provisioning, server configuration, and basic web server management.

> The core challenge was to set up a live server from scratch, configure the necessary networking and firewall rules, and deploy a custom webpage accessible to the world via its public IP address on the standard HTTP port 80.

---

## 📋 My Information

* **Name:** `[Ngozi Hannah Opara]`
* **Slack Username:** `[@CloudWithHannah]`

---

## 🌐 Live Server Information

The custom webpage is live and can be accessed at the following address.

| Attribute           | Details                                                                    |
| ------------------- | -------------------------------------------------------------------------- |
| **Public IP Address** | **[http://34.60.241.89](http://34.60.241.89)** |
| **Cloud Provider** | Google Cloud Platform (GCP)                                                |
| **Deployment Date** | October 16, 2025                                                           |

---

## 🛠️ Technology Stack

* **Cloud Provider:** Google Cloud Platform (GCP) ☁️
* **Virtual Machine:** Compute Engine VM Instance
* **Operating System:** Debian 12 (Bookworm) 🐧
* **Web Server:** NGINX 🌐
* **Firewall:** UFW (Uncomplicated Firewall) & GCP VPC Firewall 🛡️
* **Version Control:** Git & GitHub 🐙

---

## 🚀 Deployment Steps

Here is a summary of the steps taken to deploy the web server.

### 1. Cloud Infrastructure Setup (GCP)

* A **VM Instance** was created in the GCP Compute Engine.
* The **Debian 12** operating system was selected as the boot disk.
* During instance creation, the crucial firewall rule to **"Allow HTTP traffic"** was enabled. This automatically configured the GCP VPC firewall to allow incoming connections on port 80.

### 2. Server Configuration

* Connected to the instance securely via the browser-based SSH provided by GCP.
* Updated the system's package manager:
    ```bash
    sudo apt update
    ```
* Installed the NGINX web server:
    ```bash
    sudo apt install nginx -y
    ```

### 3. Deploying the Custom HTML Page

* A custom `index.html` file was created with the required personal information.
* This file was copied to the NGINX web root directory at `/var/www/html/`.
* The default NGINX welcome page (`index.nginx-debian.html`) was renamed to ensure our custom page was served by default.
    ```bash
    sudo mv /var/www/html/index.nginx-debian.html /var/www/html/default.bak
    ```

### 4. Firewall Hardening (UFW)

To add an extra layer of security on the server itself, the Uncomplicated Firewall (UFW) was configured.

* Installed UFW:
    ```bash
    sudo apt install ufw -y
    ```
* Added rules to allow essential traffic. **SSH was added first to prevent lockout.**
    ```bash
    # Allow SSH connections
    sudo ufw allow ssh

    # Allow HTTP traffic to NGINX
    sudo ufw allow 'Nginx HTTP'
    ```
* Finally, the firewall was enabled:
    ```bash
    sudo ufw enable
    ```

---

## Final Result

After completing these steps, the server successfully serves the custom `index.html` file when accessed via its public IP address. The infrastructure is secure, properly configured, and fulfills all the requirements of the task.
