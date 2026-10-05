# Evidence Notes M03

- VM: Azure Standard B2ats v2, Ubuntu 24.04, Indonesia Central
- Initial user: ZazaiVfs (login SSH dinonaktifkan via AllowUsers)
- Working user: cloudstudent (SSH key Ed25519)
- Firewall: Azure NSG (22, 80) dan UFW (OpenSSH, 80/tcp)
- Backend: Gunicorn 1 worker, 2 thread di 127.0.0.1:8000
- Reverse proxy: Caddy :80
- Service diuji tetap aktif setelah reboot
- Public endpoint: http://70.153.8.25/
- Tes publik dari laptop (2026-10-05): curl.exe http://70.153.8.25/health -> status ok
- curl.exe -I http://70.153.8.25/ -> HTTP/1.1 200 OK, Server: gunicorn, Via: 1.1 Caddy
- Tes publik dari laptop (2026-10-05): curl.exe http://70.153.8.25/health -> status ok
- curl.exe -I http://70.153.8.25/ -> HTTP/1.1 200 OK, Server: gunicorn, Via: 1.1 Caddy
