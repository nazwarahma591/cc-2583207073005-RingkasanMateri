# Requirements

## Problem Statement
Siswa dan mahasiswa mengalami kesulitan memahami materi pembelajaran yang panjang
dalam bentuk teks, PDF, dan dokumen Word, sehingga harus meringkas secara manual
dan memakan waktu. Sistem Ringkasan Materi menyediakan peringkasan otomatis berbasis
Artificial Intelligence (AI) sehingga pengguna dapat memahami inti materi dengan lebih
cepat dan praktis.

## Target Users
- Siswa dan mahasiswa yang perlu merangkum materi kuliah atau pelajaran
- Pengguna umum yang perlu memahami artikel atau dokumen teks yang panjang

## User Need
- Sebagai mahasiswa, saya ingin menempelkan teks materi dan mendapat rangkuman singkat,
  sehingga saya tidak perlu merangkum secara manual.
- Sebagai siswa, saya ingin mengunggah file PDF atau Word dan mendapat rangkuman,
  sehingga saya tidak perlu menyalin isi dokumen satu per satu.
- Sebagai pengguna, saya ingin memilih gaya rangkuman (poin-poin atau paragraf singkat),
  sehingga hasilnya sesuai kebutuhan belajar saya.

## Functional Requirements
Fitur M03 (baseline, sudah berjalan):
- FR-01 Sistem menampilkan halaman utama.
- FR-02 Sistem menyediakan health endpoint (/health).
- FR-03 Sistem menampilkan metadata aplikasi (/api/info).

Fitur produk (direncanakan pada pertemuan berikutnya):
- FR-04 Sistem menerima input teks materi secara langsung.
- FR-05 Sistem menerima unggahan file PDF berbasis teks.
- FR-06 Sistem menerima unggahan file Word (DOCX).
- FR-07 Sistem memvalidasi format dan ukuran file sebelum diproses.
- FR-08 Sistem menyediakan pilihan gaya rangkuman (poin penting, paragraf singkat).
- FR-09 Sistem mengirim teks ke layanan AI melalui API dan menampilkan hasil rangkuman.
- FR-10 Pengguna dapat menyalin atau mengunduh hasil rangkuman sebagai file teks.
- FR-11 (opsional) Sistem menyimpan riwayat rangkuman.

## Non-Functional Requirements
- NFR-01 Backend hanya listen pada loopback (127.0.0.1).
- NFR-02 Aplikasi dikelola systemd.
- NFR-03 Request publik masuk melalui reverse proxy (Caddy).
- NFR-04 Secret dan API key AI tidak disimpan di repository maupun frontend;
  disimpan sebagai environment variable pada server.
- NFR-05 Health endpoint mengembalikan HTTP 200 saat aplikasi sehat.
- NFR-06 Deployment dapat direproduksi dari repository.
- NFR-07 Arsitektur sesuai kapasitas VPS (RAM sekitar 1 GB); pemrosesan AI
  memakai API eksternal, bukan model lokal.
- NFR-08 Unggahan file dibatasi ukuran dan formatnya.

## Scope M03
In scope: repository, requirements, architecture, ADR, aplikasi Flask baseline,
SSH hardening, Gunicorn, systemd, Caddy, HTTP publik.
Out of scope M03: integrasi API AI, ekstraksi PDF/DOCX, database riwayat,
Docker, IaC, CI/CD, HTTPS/domain, monitoring penuh.

## Constraints
- Ubuntu Server 24.04 LTS, VPS Azure, public IPv4
- 2 vCPU, sekitar 1 GB RAM, disk 61 GB
- PDF hasil scan memerlukan OCR dan belum didukung pada versi awal
- Ketersediaan dan biaya API AI bergantung pada penyedia layanan

## Acceptance Criteria M03
- [x] First deployment dapat diakses melalui public IP
- [x] Health endpoint berfungsi
