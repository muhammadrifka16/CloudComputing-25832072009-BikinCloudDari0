# Cloud Project: Peminjaman Perangkat Lab

Cloud Computing, PTI 2802. Pertemuan 3: Project Inception.

## Author
Muhammad Rifka Z / 25832072009

## Problem
Administrator laboratorium kesulitan memantau peminjaman perangkat
secara terpusat.

## Features M03
- baseline aplikasi Flask
- health endpoint
- deployment VM Azure

## Infrastructure
- Azure VM Standard B2ats v2 (2 vCPU, 1 GiB RAM)
- Ubuntu Server 24.04, Caddy, Gunicorn, systemd, UFW

## Public Endpoint
http://70.153.8.25/

## Health Check
GET /health

## Deployment
Lihat docs/deployment.md.

## Security
- SSH key-only, root login nonaktif
- UFW dan Azure NSG aktif
- backend loopback-only

## Current Limitations
- HTTP only, tanpa database, tanpa container, deployment manual

## Roadmap
M04 DNS/HTTPS, M05 Data, M06 Container, M07 IaC, M09 CI/CD
