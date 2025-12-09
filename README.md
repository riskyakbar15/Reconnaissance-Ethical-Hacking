# Laporan Tugas Besar: Pengumpulan Informasi Target (Reconnaissance)

**Mata Kuliah:** Ethical Hacking
**Dosen Pengampu:** Pak Runal Rezkiawan

---

## 👨‍💻 Identitas Mahasiswa

| Atribut | Detail |
| :--- | :--- |
| **Nama** | Risky Akbar |
| **NIM** | 105841118223 |
| **Kelas** | JK-A |
| **Fakultas** | Teknik |
| **Prodi** | Teknik Informatika |

---

## 📌 Deskripsi Proyek

Repositori ini berisi dokumentasi lengkap untuk **Tugas Besar (Mid)**. Proyek ini merupakan simulasi audit keamanan (*security audit*) yang berfokus pada tahap **Information Gathering / Reconnaissance**.

Tujuan utama proyek ini adalah memetakan *attack surface* (permukaan serangan) dari target yang ditentukan untuk menemukan potensi kerentanan, baik melalui informasi publik (OSINT) maupun pemindaian jaringan aktif.

📂 **Struktur File:**
* `SKENARIO.md`: Penjelasan detail skenario simulasi, *Rules of Engagement*, dan batasan teknis.
* `Laporan_Final.pdf`: Laporan resmi hasil audit dalam format PDF.
* `README.md`: Ringkasan eksekutif dan dokumentasi teknis.

> **⚠️ PERHATIAN:** > Untuk membaca detail Skenario dan Aturan Main (*Rules of Engagement*) simulasi ini, silakan buka file **[SKENARIO.md](./SKENARIO.md)**.

---

## 🛠️ Tools & Lingkungan Kerja

Berikut adalah alat-alat yang digunakan dalam proses *capturing* dan analisis data:

### Lingkungan Sistem Operasi
* **Attacker Machine:** Kali Linux
* **Target Active:** VulnOSv2 (Running on VirtualBox)
* **Network Analysis:** Wireshark

### Tools Passive Reconnaissance
* **DNS & Subdomain:** DNSDumpster, Subfinder, Sublist3r
* **Teknologi Web:** Wappalyzer, WhatWeb
* **Email & User Enumeration:** theHarvester, Google Search
* **Vulnerability Search:** Google Dorking

### Tools Active Reconnaissance
* **Nmap:** Digunakan untuk Host Discovery, Port Scanning, Service Version Detection, dan OS Fingerprinting.

---

## 📝 Tahapan Dokumentasi (Methodology)

### 1. Passive Reconnaissance (Target Publik)
**Target:** `dephub.go.id`

Pada tahap ini, dokumentasi dilakukan dengan cara mengambil tangkapan layar (*screenshot*) dari hasil kueri tools OSINT. Langkah-langkah yang dilakukan:

1.  **Subdomain Enumeration:** Menggunakan `subfinder` dan `sublist3r` di terminal Kali Linux untuk menemukan domain pendukung seperti `bkkp`, `skrb`, dan `ppid`.
2.  **Identifikasi Teknologi:** Menggunakan ekstensi browser Wappalyzer dan tool CLI WhatWeb untuk mendeteksi *backend* (Laravel) dan server (F5 BigIP).
3.  **Data Mining:** Menggunakan `theHarvester` dan pencarian manual Google (`site:dephub.go.id`) untuk menemukan pola email pejabat dan file PDF yang bocor.
4.  **Google Dorking:** Mencari file konfigurasi sensitif. Ditemukan file `phpinfo` yang terbuka untuk publik.

### 2. Active Reconnaissance (Target Lab)
**Target IP:** `172.20.10.5` (VulnOS)

Pada tahap ini, dokumentasi dilakukan dengan merekam output terminal dan analisis trafik jaringan. Langkah-langkah yang dilakukan:

1.  **Host Discovery:** Memastikan target hidup menggunakan `nmap -sn`.
2.  **Port Scanning:** Melakukan pemindaian menyeluruh (TCP & UDP) untuk melihat port terbuka (*Open Ports*).
3.  **Service Detection:** Menjalankan `nmap -sV` untuk mengetahui versi aplikasi yang berjalan. Ditemukan versi usang pada FTP (vsftpd 2.3.4) dan HTTP (Apache 2.2.8).
4.  **OS Fingerprinting:** Menggunakan `nmap -O` untuk menebak Sistem Operasi target (Linux Kernel 3.x/4.x).
5.  **Traffic Analysis:** Menggunakan **Wireshark** untuk menangkap paket data selama proses scanning guna memverifikasi pola serangan (TCP SYN/ACK).

---

## 📊 Kesimpulan Hasil Audit

Berdasarkan hasil *Information Gathering*, ditemukan bahwa:
* **Target Publik** memiliki celah *Information Disclosure* pada konfigurasi PHP dan subdomain yang luas.
* **Target Lab (VulnOS)** sangat rentan karena menggunakan layanan yang sudah *End-of-Life* (EOL) dan memiliki backdoor yang diketahui publik (Critical Vulnerabilities).

---

*Dibuat untuk memenuhi Tugas Besar Semester Ganjil 2025.*

---

> **Disclaimer:** Segala tindakan reconnaissance pada target publik dilakukan secara pasif (non-intrusive) untuk tujuan pendidikan dan tidak merusak sistem.
