# Ringkasan Materi

Website peringkas materi berbasis Artificial Intelligence (AI).

Cloud Computing — PTI 2802 | Pertemuan 3 — Project Inception

## Author
Nazwa / 2583207073005 / 2A

## Problem
Siswa dan mahasiswa kesulitan memahami materi pembelajaran yang panjang dan
harus merangkumnya secara manual. Ringkasan Materi merangkum teks, PDF, dan
dokumen Word secara otomatis dengan bantuan AI.

## Target Users
Siswa, mahasiswa, dan pengguna umum yang perlu merangkum materi atau dokumen teks.

## Features M03
- Aplikasi baseline Flask
- Health endpoint `/health`
- Deployment di VPS Ubuntu 24.04

## Planned Features
- Input teks langsung, unggah PDF dan DOCX
- Pilihan gaya rangkuman (poin penting / paragraf singkat)
- Rangkuman AI melalui API, salin atau unduh hasil
- Riwayat rangkuman (opsional)

## Architecture

```mermaid
flowchart LR
    U[User] --> C[Caddy] --> G[Gunicorn] --> F[Flask]
```

Detail: `docs/architecture.md`.

## Infrastructure
- Ubuntu Server 24.04, Caddy, Gunicorn, systemd, UFW, GitHub

## Public Endpoint
`http://20.194.24.209/`

## Health Check
`GET /health`

## Deployment
Lihat `docs/deployment.md`.

## Security
- SSH key-only, root login nonaktif, UFW aktif, backend loopback-only
- API key AI tidak disimpan di repository

## Current Limitations
- HTTP saja, fitur peringkasan AI belum diimplementasikan
- Tanpa database, tanpa container, deployment manual

## Roadmap
M04 DNS/HTTPS, M05 Data dan integrasi AI, M06 Container, M07 IaC, M09 CI/CD
