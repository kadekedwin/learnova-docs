---
icon: graduation-cap
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
metaLinks:
  alternates:
    - https://app.gitbook.com/s/yE16Xb3IemPxJWydtPOj/
---

# About Learnova

**Learnova** is an educational private cloud service built on top of **Proxmox Virtual Environment (Proxmox VE)**. It is designed to support school or educational institution infrastructure by providing centralized management, cloud services, monitoring, and secure external access.

The platform is composed of several dedicated virtual servers, each with a specific role:

### 1. Proxmox Virtualization Layer

Proxmox VE acts as the core infrastructure layer, providing:

* Virtual machine (VM) management
* Resource allocation (CPU, RAM, storage)
* High availability and isolation between services
* Centralized control of all servers in the Learnova environment

All Learnova services run as virtual machines within Proxmox.

### 2. Windows Server (User & Client Management)

The **Windows Server** is responsible for:

* Managing client users (students, teachers, staff)
* Centralized authentication and authorization
* User policies and access control
* Device and user management within the Learnova ecosystem

This server enables structured and secure user administration for the school environment.

### 3. Ubuntu Application Server (Cloud Services)

The **Ubuntu App Server** provides cloud-based services, including:

* **Nextcloud** for file storage, sharing, and collaboration
* **Landing Page** website of Learnova Education

This server acts as the primary application layer for Learnova.

### 4. Ubuntu Monitoring Server (Observability)

The **Monitoring Server** is built using:

* **Prometheus** for metrics collection
* **Grafana** for visualization and dashboards

Its functions include:

* Monitoring server performance (CPU, RAM, disk, network)
* Tracking service availability
* Detecting performance issues early
* Providing dashboards for administrators
* Detect Network Speed in realtime on each minutes

This ensures system reliability and proactive maintenance.

### 5. Ubuntu Gateway Server (Ingress & Security)

The **Gateway Server** serves as the entry point to the Learnova platform and uses:

* **Cloudflared** as a secure ingress solution

Responsibilities include:

* Securely exposing internal services to the internet
* Acting as a reverse proxy for all servers
* Eliminating the need for direct public IP exposure
* Enhancing security through encrypted tunnels

All external access to Learnova services is routed through this gateway.

### Learnova Architecture Summary

Learnova delivers a **secure, scalable, and centrally managed private cloud** for educational institutions by combining:

* Proxmox virtualization
* Windows-based user management
* Linux-based cloud and monitoring services
* Secure ingress via Cloudflared

This architecture enables schools to provide modern IT services such as cloud storage, centralized user management, and real-time monitoring while maintaining security and control.
