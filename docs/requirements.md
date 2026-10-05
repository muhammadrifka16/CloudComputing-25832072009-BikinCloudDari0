# Requirements

## Problem Statement
Administrator laboratorium kesulitan memantau peminjaman perangkat
secara terpusat. Sistem akan menyediakan pencatatan perangkat,
peminjaman, dan status pengembalian sehingga penggunaan perangkat
dapat ditelusuri.

## Target Users
- Administrator laboratorium
- Mahasiswa peminjam perangkat

## User Needs
- Sebagai administrator, saya ingin melihat perangkat yang belum
  dikembalikan, sehingga saya dapat menindaklanjuti keterlambatan.
- Sebagai mahasiswa, saya ingin tahu perangkat yang tersedia,
  sehingga saya dapat merencanakan peminjaman.

## Functional Requirements
- FR-01 Sistem menampilkan halaman utama.
- FR-02 Sistem menyediakan health endpoint (/health).
- FR-03 Sistem menampilkan metadata aplikasi (/api/info).
- FR-04 Sistem menampilkan daftar objek utama proyek (M05+).

## Non-Functional Requirements
- NFR-01 Backend hanya listen pada loopback (127.0.0.1:8000).
- NFR-02 Aplikasi dikelola systemd.
- NFR-03 Request publik masuk melalui reverse proxy (Caddy).
- NFR-04 Secret tidak disimpan pada Git repository.
- NFR-05 Health endpoint mengembalikan HTTP 200 saat sehat.
- NFR-06 Deployment dapat direproduksi dari repository.
- NFR-07 Arsitektur sesuai VM 2 vCPU / 1 GiB RAM.

## Scope M03
In scope: repository, requirements, architecture, ADR, baseline
Flask app, SSH hardening, Gunicorn, systemd, Caddy, HTTP publik.
Out of scope: database, Docker, IaC, CI/CD, domain dan HTTPS,
horizontal scaling, monitoring stack.

## Constraints
- Azure VM Standard B2ats v2 (2 vCPU, 1 GiB RAM)
- Disk OS 29 GB
- Ubuntu Server 24.04 LTS
- Public IPv4 70.153.8.25

## Acceptance Criteria M03
- [x] first deployment dapat diakses dari internet
- [x] /health mengembalikan HTTP 200
- [x] backend tidak terbuka di 0.0.0.0:8000
- [x] service tetap hidup setelah reboot
