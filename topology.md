---
icon: sitemap
---

# Topology

Tipologi jaringan Learnova dirancang menggunakan pendekatan **terpusat (centralized topology)** dengan **router sebagai gateway utama**, **Proxmox sebagai server virtualisasi**, serta **segmentasi jaringan** untuk memisahkan akses **student, staff, dan admin**.

<figure><img src=".gitbook/assets/Jarprise (1).jpg" alt=""><figcaption></figcaption></figure>

Arsitektur ini bertujuan untuk:

* Mempermudah pengelolaan server dan klien
* Meningkatkan keamanan jaringan
* Mengatur akses berdasarkan peran pengguna
* Mendukung layanan pendidikan berbasis cloud

### Router sebagai Gateway Utama

Router berfungsi sebagai **gateway utama jaringan Learnova** dan penghubung ke internet.

* **IP Router:** `192.168.16.1`
* Fungsi:
  * Gateway seluruh jaringan internal
  * Routing antar subnet
  * Penyedia koneksi internet
  * Pengelolaan bandwidth nirkabel (5 GHz)

Router terhubung langsung ke server Proxmox dan juga menyediakan koneksi wireless.

### Proxmox Virtual Environment

Server Proxmox berperan sebagai **host virtualisasi** untuk seluruh server Learnova.

* **IP Proxmox:** `192.168.16.2`
* Koneksi: Terhubung langsung ke router
* Mode jaringan: **Proxmox Bridge**

Proxmox bridge memungkinkan setiap mesin virtual mendapatkan akses jaringan langsung seolah-olah berada pada jaringan fisik yang sama.

### Server Virtual pada Proxmox

Melalui Proxmox bridge, beberapa server virtual dijalankan dengan alamat IP statis sebagai berikut:

| Server                   | Sistem Operasi | IP Address     | Fungsi Utama               |
| ------------------------ | -------------- | -------------- | -------------------------- |
| Windows Server           | Windows Server | `192.168.16.3` | Domain Controller & GPO    |
| Ubuntu App Server        | Ubuntu Server  | `192.168.16.4` | Nextcloud dan Landing Page |
| Ubuntu Monitoring Server | Ubuntu Server  | `192.168.16.5` | Grafana & Prometheus       |
| Ubuntu Gateway Server    | Ubuntu Server  | `192.168.16.6` | Cloudflared Ingress        |

Semua server berada dalam satu segmen jaringan server untuk mempermudah komunikasi internal dan pengelolaan.

### Segmentasi Jaringan Client (DHCP)

Jaringan client dibagi menjadi beberapa subnet berdasarkan peran pengguna. **Seluruh client menggunakan DHCP** sehingga alamat IP diberikan secara otomatis oleh router.

#### Jaringan Client Wireless (2.4 GHz)

Seluruh user yang terhubung secara **wireless melalui jaringan 2.4 GHz** mendapatkan alamat IP secara otomatis melalui DHCP.

* Network: `192.168.100.0/24`
* Gateway: `192.168.100.1`
* IP Address: DHCP (otomatis)
* Media: Wi-Fi 2.4 GHz

#### Jaringan Client Student

* Network: `192.168.20.0/24`
* Gateway: `192.168.20.1`
* IP Address: DHCP (otomatis)
* Media: LAN

#### Jaringan Client Staff

* Network: `192.168.25.0/24`
* Gateway: `192.168.25.1`
* IP Address: DHCP (otomatis)
* Media: LAN

#### Jaringan Client Admin

* Network: `192.168.30.0/24`
* Gateway: `192.168.30.1`
* IP Address: DHCP (otomatis)
* Media: LAN

### Alur Koneksi Jaringan

* Router terhubung ke hotspot HP (5 GHz) sebagai sumber internet
* Router mendistribusikan koneksi internet ke seluruh subnet
* Client terhubung:
  * Wireless 2.4 GHz → `192.168.100.0/24`
  * Wired → subnet sesuai peran
* Client mendapatkan IP otomatis melalui DHCP
* Client mengakses layanan Learnova sesuai kebijakan
* Akses eksternal layanan melalui Ubuntu Gateway (Cloudflared)

### Ringkasan Tipologi

Tipologi jaringan Learnova kini mencakup:

* Internet dari hotspot HP (5 GHz)
* Wi-Fi 2.4 GHz untuk akses user umum
* Segmentasi LAN berbasis peran
* DHCP terpusat pada router
* Infrastruktur server berbasis Proxmox

Desain ini memberikan **fleksibilitas koneksi**, **kemudahan manajemen**, dan **keamanan jaringan** untuk lingkungan pendidikan Learnova.
