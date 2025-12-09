# Laporan Tugas Besar: Network Security Reconnaissance

**Mata Kuliah:** Keamanan Jaringan  
**Dosen Pengampu:** [Nama Dosen Anda]  

---

## 👨‍💻 Identitas Mahasiswa
* [cite_start]**Nama:** Risky Akbar [cite: 3]
* [cite_start]**NIM:** 105841118223 [cite: 4]
* [cite_start]**Kelas:** JK-A [cite: 4]
* **Fakultas:** Teknik
* **Prodi:** Teknik Informatika

---

## 📌 Deskripsi Proyek
Repositori ini berisi dokumentasi lengkap untuk **Tugas Besar (Mid) Keamanan Jaringan**. [cite_start]Proyek ini merupakan simulasi audit keamanan (*security audit*) yang berfokus pada tahap **Information Gathering / Reconnaissance**[cite: 1].

[cite_start]Tujuan utama proyek ini adalah memetakan *attack surface* (permukaan serangan) dari target yang ditentukan untuk menemukan potensi kerentanan, baik melalui informasi publik (OSINT) maupun pemindaian jaringan aktif[cite: 8, 9].

📂 **Struktur File:**
* `SKENARIO.md`: Penjelasan detail skenario simulasi, *Rules of Engagement*, dan batasan teknis.
* `Laporan_Final.pdf`: Laporan resmi hasil audit dalam format PDF.
* `README.md`: Ringkasan eksekutif dan dokumentasi teknis.

> **⚠️ PERHATIAN:** > Untuk membaca detail Skenario dan Aturan Main (*Rules of Engagement*) simulasi ini, silakan buka file **[SKENARIO.md](./SKENARIO.md)**.

---

## 🛠️ Tools & Lingkungan Kerja
[cite_start]Berikut adalah alat-alat yang digunakan dalam proses *capturing* dan analisis data[cite: 14, 280]:

**Lingkungan Sistem Operasi:**
* [cite_start]**Attacker Machine:** Kali Linux [cite: 281]
* [cite_start]**Target Active:** VulnOSv2 (Running on VirtualBox) [cite: 282]
* [cite_start]**Network Analysis:** Wireshark [cite: 447]

**Tools Passive Reconnaissance:**
* [cite_start]**DNS & Subdomain:** DNSDumpster, Subfinder, Sublist3r [cite: 15-17]
* [cite_start]**Teknologi Web:** Wappalyzer, WhatWeb [cite: 18-19]
* [cite_start]**Email & User Enumeration:** theHarvester, Google Search [cite: 20-21]
* [cite_start]**Vulnerability Search:** Google Dorking [cite: 22]

**Tools Active Reconnaissance:**
* [cite_start]**Nmap:** Untuk Host Discovery, Port Scanning, Service Version Detection, dan OS Fingerprinting[cite: 283].

---

## 📝 Tahapan Dokumentasi (Methodology)

### 1. Passive Reconnaissance (Target Publik)
[cite_start]**Target:** `dephub.go.id` [cite: 27]

Pada tahap ini, dokumentasi dilakukan dengan cara mengambil tangkapan layar (*screenshot*) dari hasil kueri tools OSINT. Langkah-langkah yang dilakukan:

1.  [cite_start]**Subdomain Enumeration:** Menggunakan `subfinder` dan `sublist3r` di terminal Kali Linux untuk menemukan domain pendukung seperti `bkkp`, `skrb`, dan `ppid` [cite: 118-124].
2.  [cite_start]**Identifikasi Teknologi:** Menggunakan ekstensi browser Wappalyzer dan tool CLI WhatWeb untuk mendeteksi *backend* (Laravel) dan server (F5 BigIP) [cite: 226-238].
3.  [cite_start]**Data Mining:** Menggunakan `theHarvester` dan pencarian manual Google (`site:dephub.go.id`) untuk menemukan pola email pejabat dan file PDF yang bocor [cite: 127-148].
4.  **Google Dorking:** Mencari file konfigurasi sensitif. [cite_start]Ditemukan file `phpinfo` yang terbuka untuk publik[cite: 251].

### 2. Active Reconnaissance (Target Lab)
[cite_start]**Target IP:** `172.20.10.5` (VulnOS) [cite: 309]

Pada tahap ini, dokumentasi dilakukan dengan merekam output terminal dan analisis trafik jaringan. Langkah-langkah yang dilakukan:

1.  [cite_start]**Host Discovery:** Memastikan target hidup menggunakan `nmap -sn`[cite: 309].
2.  [cite_start]**Port Scanning:** Melakukan pemindaian menyeluruh (TCP & UDP) untuk melihat port terbuka (Open Ports)[cite: 319, 340].
3.  **Service Detection:** Menjalankan `nmap -sV` untuk mengetahui versi aplikasi yang berjalan. [cite_start]Ditemukan versi usang pada FTP (vsftpd 2.3.4) dan HTTP (Apache 2.2.8)[cite: 493, 495].
4.  [cite_start]**OS Fingerprinting:** Menggunakan `nmap -O` untuk menebak Sistem Operasi target (Linux Kernel 3.x/4.x)[cite: 407, 420].
5.  [cite_start]**Traffic Analysis:** Menggunakan **Wireshark** untuk menangkap paket data selama proses scanning guna memverifikasi pola serangan (TCP SYN/ACK)[cite: 446, 486].

---

## 📊 Kesimpulan Hasil Audit
Berdasarkan hasil *Information Gathering*, ditemukan bahwa:
* [cite_start]**Target Publik** memiliki celah *Information Disclosure* pada konfigurasi PHP dan subdomain yang luas[cite: 270].
* [cite_start]**Target Lab (VulnOS)** sangat rentan karena menggunakan layanan yang sudah *End-of-Life* (EOL) dan memiliki backdoor yang diketahui publik (Critical Vulnerabilities) [cite: 498-500].

---
*Dibuat untuk memenuhi Tugas Besar Semester Ganjil 2025.*
