---
icon: ubuntu
---

# Gateway Server

Gateway server adalah sebuah LXC (Linux Container) yang menjalankan daemon cloudlfared. Instance ini digunakan sebagai jembatan antara permintaan HTTP yang datang dari internet ke dalam internal sistem.

Berikut merupakan ingress dari cloudflared yang digunakan saat ini:

```yaml
tunnel: learnova-tunnel
credentials-file: ~/.cloudflared/<tunnel-id>.json

ingress:
    ## landing page
  - hostname: tlns.my.id
    service: http://192.168.16.4:8000
    
    ## nextcloud
  - hostname: cloud.tlns.my.id
    service: http://192.168.16.4:11000
    
    ## grafana
  - hostname: monitor.tlns.my.id
    service: http://192.168.16.5:3000
    
    ## uptime kuma
  - hostname: status.tlns.my.id
    service: http://192.168.16.5:3001
    
  - service: http_status:404
```
