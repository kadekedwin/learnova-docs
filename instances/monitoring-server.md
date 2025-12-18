---
icon: ubuntu
---

# Monitoring Server

Server ini menjalankan service monitoring yang dimana ini akan membantu admin untuk mengetahui metric dari setiap komponen sistem tanpa harus masuk ke dalamnya secara satu persatu (terpusat).

### Grafana

> Link: [https://monitor.tlns.my.id](https://monitor.tlns.my.id/)

```
port: 3000
```

#### Exporter

* Proxmox exporter
* Node Exporter (prometheus/node-exporter)
* Mikrotik (mktxp)
* Server Inet Speed
* Nextcloud

### Uptime Kuma

> Link: [https://status.tlns.my.id](https://status.tlns.my.id/)

Digunakan untuk melihat status dan riwayat uptime aplikasi yang berjalan pada sistem learnova

> Seharusnya dibuat di server fisik terpisah, namun untuk kebutuhan praktik maka dibuat dalam satu server yang sama
