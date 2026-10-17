# ADR-0001: Initial VPS Deployment Architecture

## Status
Accepted

## Context
Proyek Ringkasan Materi adalah website peringkas materi berbasis AI. VPS yang
tersedia adalah Azure Ubuntu Server 24.04 dengan 2 vCPU, sekitar 1 GB RAM, dan
disk 61 GB. Aplikasi perlu dapat diakses publik dan nantinya mengekstrak teks
dari PDF/DOCX serta memanggil API AI.

## Decision
Flask, Gunicorn (1 worker, 2 thread), systemd, Caddy, UFW, GitHub.
Pemrosesan AI memakai API eksternal.

## Alternatives
1. Node.js + PM2
2. NGINX + Gunicorn
3. Docker
4. PHP-FPM

## Rationale
Flask dipilih karena ringan dan Python memiliki pustaka yang dibutuhkan proyek
ini, yaitu PyMuPDF untuk PDF dan python-docx untuk DOCX. Gunicorn dengan satu
worker menjaga pemakaian RAM tetap kecil pada VPS 1 GB. systemd membuat aplikasi
berjalan sebagai layanan dan hidup kembali setelah reboot. Caddy sederhana sebagai
reverse proxy dan mudah ditingkatkan ke HTTPS otomatis pada M04. Model AI tidak
dipasang di VPS karena RAM terbatas, sehingga peringkasan dilakukan lewat API
eksternal. Docker belum dipakai karena containerization adalah materi M06.

## Consequences
### Positive
- Ringan, sederhana, mudah dipahami dan dipelihara
- Model AI tidak membebani resource VPS
### Negative
- Satu server tanpa redundansi, deployment masih manual
- HTTP belum terenkripsi pada tahap ini
- Bergantung pada ketersediaan dan biaya API AI pihak ketiga

## Review Trigger
Review pada M06/M07.
