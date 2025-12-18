---
icon: windows
---

# Windows Server

Windows Server pada platform **Learnova** berfungsi sebagai **server pusat untuk manajemen pengguna dan kebijakan**. Server ini bertanggung jawab atas **pengendalian domain, autentikasi pengguna, penerapan Group Policy, serta integrasi klien** dalam lingkungan pendidikan Learnova.

### Konfigurasi Jaringan

Windows Server telah dikonfigurasi menggunakan **alamat IP statis** untuk menjamin stabilitas dan konsistensi layanan domain.

* **Alamat IP**: 192.168.16.3
* **DNS Server**: 127.0.0.1
* **Mode Jaringan**: Internal / LAN

Mesin klien memperoleh alamat IP secara otomatis melalui **DHCP dari router**, sehingga konektivitas jaringan dapat berjalan dengan lancar tanpa perlu konfigurasi IP secara manual pada setiap perangkat klien.

### Active Directory Domain Services (AD DS)

#### Konfigurasi Forest dan Domain

Peran **Active Directory Domain Services (AD DS)** telah diinstal dan dikonfigurasi dengan struktur domain sebagai berikut:

* **Nama Forest**: gpo.learnova.edu
* **Tipe Domain**: Single forest, single domain
* **Domain Controller**: Windows Server (Primary DC)

Konfigurasi ini memungkinkan **manajemen identitas terpusat** serta **penerapan Group Policy** secara terintegrasi pada seluruh klien Learnova.

### Struktur Organizational Unit (OU)

Untuk memisahkan manajemen kebijakan dan kontrol administratif, telah dibuat dua **Organizational Unit (OU)** utama, yaitu:

| Nama OU          | Deskripsi                    |
| ---------------- | ---------------------------- |
| Learnova Staff   | Berisi staff user accounts   |
| Learnova Student | Berisi student user accounts |

### Akun Pengguna (User Account)

Beberapa **akun pengguna domain** telah dibuat dan ditempatkan sesuai dengan OU masing-masing untuk mendukung struktur manajemen dan penerapan kebijakan yang efektif.

| Username | Role    | OU               |
| -------- | ------- | ---------------- |
| catur    | Staff   | Learnova Staff   |
| amelia   | Student | Learnova Student |

### Konfigurasi Group Policy Object (GPO)

**Group Policy Object (GPO)** telah dikonfigurasi dan ditautkan ke **Organizational Unit (OU)** yang sesuai untuk menerapkan aturan dan pembatasan yang berbeda berdasarkan peran pengguna.

* GPO ditautkan pada tingkat OU
* Kebijakan diterapkan secara otomatis saat pengguna login ke komputer klien yang tergabung dalam domain
* Staf dan mahasiswa menerima set kebijakan yang berbeda

<table><thead><tr><th width="244.57421875">OU</th><th>Nama GPO</th></tr></thead><tbody><tr><td>Student dan Staff</td><td>Disable Control Panel &#x26; Settings</td></tr><tr><td>Student dan Staff</td><td>Disable Command Prompt</td></tr><tr><td>Student dan Staff</td><td>Disable Regedit</td></tr><tr><td>Student dan Staff</td><td>Auto Lock / Auto Logoff After Idle</td></tr><tr><td>Student dan Staff</td><td>Disable Powershell</td></tr><tr><td>Student</td><td>Disable USB Storage</td></tr><tr><td>Student</td><td>Disable Software Installation</td></tr><tr><td>Student</td><td>Create Student Folder in C:\</td></tr><tr><td>Staff</td><td>Create Staff Folder in C:\</td></tr></tbody></table>

### Konfigurasi Klien

Komputer klien dikonfigurasi dengan pengaturan sebagai berikut:

* **Pengalamatan IP**: Otomatis (DHCP dari router)
* **Resolusi DNS**: Disediakan oleh Windows Server (Domain Controller)
* **Domain Join**: Klien tergabung ke domain **gpo.learnova.edu**

Konfigurasi ini memungkinkan klien untuk secara otomatis memperoleh alamat IP serta kebijakan domain tanpa perlu pengaturan jaringan secara manual.
