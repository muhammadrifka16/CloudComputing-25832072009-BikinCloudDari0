# ADR-0001: Initial VM Deployment Architecture

## Status
Accepted

## Context
Azure VM Standard B2ats v2 (2 vCPU, 1 GiB RAM), Ubuntu Server 24.04.
Proyek perlu dapat diakses publik lewat IP dan bisa direproduksi.

## Decision
- Flask sebagai web framework
- Gunicorn dengan 1 worker dan 2 thread
- systemd sebagai process manager
- Caddy sebagai reverse proxy
- UFW dan Azure NSG sebagai firewall
- GitHub sebagai single source of truth

## Alternatives
1. Node.js + PM2
2. NGINX + Gunicorn
3. Docker
4. PHP-FPM

## Rationale
RAM hanya 1 GiB, sehingga stack dipilih yang ringan dan jumlah
worker dibatasi agar tersisa headroom untuk SSH, systemd, dan Caddy.
Python 3.12 sudah menjadi default Ubuntu 24.04. Caddy dipilih karena
konfigurasi reverse proxy sederhana dan siap HTTPS otomatis di M04.
Docker ditunda karena containerization materi M06.

## Consequences
### Positive
- footprint kecil, mudah dipahami
- service otomatis hidup kembali setelah reboot
- backend tidak terekspos langsung

### Negative
- deployment masih manual
- single point of failure
- HTTP belum terenkripsi

## Review Trigger
Review pada M06/M07.
