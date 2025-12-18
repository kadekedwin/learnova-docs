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

**Learnova** adalah layanan **private cloud pendidikan** yang dibangun di atas **Proxmox Virtual Environment (Proxmox VE)**. Platform ini dirancang untuk mendukung infrastruktur sekolah atau institusi pendidikan dengan menyediakan **manajemen terpusat, layanan cloud, sistem monitoring, serta akses eksternal yang aman**.

Platform Learnova terdiri dari beberapa **server virtual khusus**, masing-masing dengan peran yang berbeda dan saling terintegrasi.

### 1. Lapisan Virtualisasi Proxmox

**Proxmox Virtual Environment (Proxmox VE)** berperan sebagai lapisan infrastruktur inti yang menyediakan:

* Manajemen mesin virtual (Virtual Machine / VM)
* Alokasi sumber daya (CPU, RAM, dan penyimpanan)
* Ketersediaan tinggi (high availability) dan isolasi antar layanan
* Kontrol terpusat terhadap seluruh server dalam lingkungan Learnova

Seluruh layanan Learnova dijalankan dalam bentuk **mesin virtual** yang dikelola oleh Proxmox VE.

### 2. Windows Server (Manajemen Pengguna dan Klien)

**Windows Server** bertanggung jawab dalam:

* Mengelola pengguna klien (siswa, guru, dan staf)
* Autentikasi dan otorisasi terpusat
* Penerapan kebijakan pengguna dan kontrol akses
* Manajemen perangkat dan pengguna dalam ekosistem Learnova

Server ini memungkinkan administrasi pengguna yang **terstruktur, aman, dan terpusat** sesuai dengan kebutuhan lingkungan sekolah.

### 3. Ubuntu Application Server (Layanan Cloud)

**Ubuntu Application Server** menyediakan layanan berbasis cloud, antara lain:

* **Nextcloud** untuk penyimpanan file, berbagi data, dan kolaborasi
* **Website Landing Page Learnova Education**

Server ini berfungsi sebagai **lapisan aplikasi utama** pada platform Learnova.

### 4. Ubuntu Monitoring Server (Observabilitas)

Server monitoring dibangun menggunakan:

* **Prometheus** untuk pengumpulan metrik
* **Grafana** untuk visualisasi dan dashboard

Fungsi utama server monitoring meliputi:

* Memantau performa server (CPU, RAM, disk, dan jaringan)
* Memantau ketersediaan layanan
* Mendeteksi masalah performa secara dini
* Menyediakan dashboard pemantauan untuk administrator
* Mendeteksi kecepatan jaringan secara real-time setiap menit

Dengan adanya sistem ini, keandalan sistem dapat terjaga dan pemeliharaan dapat dilakukan secara proaktif.

### 5. Ubuntu Gateway Server (Ingress dan Keamanan)

**Gateway Server** berfungsi sebagai pintu masuk utama ke platform Learnova dan menggunakan:

* **Cloudflared** sebagai solusi ingress yang aman

Tanggung jawab Gateway Server meliputi:

* Mengekspos layanan internal ke internet secara aman
* Bertindak sebagai reverse proxy untuk seluruh server
* Menghilangkan kebutuhan penggunaan IP publik langsung
* Meningkatkan keamanan melalui tunnel terenkripsi

Seluruh akses eksternal ke layanan Learnova diarahkan melalui server gateway ini.

### Ringkasan Arsitektur Learnova

Learnova menghadirkan **private cloud pendidikan yang aman, skalabel, dan dikelola secara terpusat** dengan mengombinasikan:

* Virtualisasi Proxmox
* Manajemen pengguna berbasis Windows
* Layanan cloud dan monitoring berbasis Linux
* Akses aman melalui Cloudflared

Arsitektur ini memungkinkan sekolah menyediakan layanan TI modern seperti **penyimpanan cloud, manajemen pengguna terpusat, dan pemantauan sistem secara real-time**, sambil tetap menjaga **keamanan dan kendali penuh** atas infrastruktur.
