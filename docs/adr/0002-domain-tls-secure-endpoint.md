# ADR-0002: Public DNS and TLS Termination with Caddy

## Status
Accepted

## Context
M03 menggunakan public IPv4 dan HTTP.
M04 membutuhkan hostname stabil dan secure endpoint via HTTPS.

## Decision
- Gunakan A record menuju IP Public VPS (`70.153.8.25`);
- Gunakan Caddy sebagai TLS terminator dan reverse proxy;
- Pertahankan Gunicorn pada 127.0.0.1:8000;
- Buka TCP/80 dan TCP/443;
- Gunakan automatic HTTPS Caddy.

## Consequences
- Endpoint aman berbasis HTTPS;
- Sertifikat SSL/TLS dikelola otomatis oleh Caddy;
- Backend tetap terisolasi di loopback (127.0.0.1:8000).
