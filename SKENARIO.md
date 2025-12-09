# Skenario Simulasi & Rules of Engagement (RoE)

## 1. Latar Belakang & Peran
[cite_start]Dalam simulasi Tugas Besar ini, penulis bertindak sebagai **Konsultan Keamanan Siber Eksternal** (*External Security Consultant*)[cite: 6]. Penulis ditugaskan untuk melakukan audit keamanan awal (*initial security audit*) terhadap infrastruktur target.

[cite_start]Fokus utama dari kegiatan ini adalah **Information Gathering (Reconnaissance)** untuk mengidentifikasi potensi titik masuk (*entry points*) pada infrastruktur online maupun offline, serta memetakan permukaan serangan (*attack surface*) tanpa melakukan eksploitasi merusak[cite: 7, 265].

---

## 2. Lingkup Target (Scope of Work)

Audit ini dibagi menjadi dua kategori berdasarkan jenis target dan metode interaksi yang diizinkan:

### A. Lingkup Pasif (Passive Reconnaissance)
* [cite_start]**Target:** `dephub.go.id` (Kementerian Perhubungan Republik Indonesia)[cite: 27].
* **Metode:** OSINT (*Open-Source Intelligence*).
* **Batasan:** Pengumpulan informasi hanya dilakukan menggunakan sumber daya publik yang tersedia di internet.
* [cite_start]**Larangan Keras:** Dilarang melakukan *scanning* aktif, *brute-force*, atau mengirimkan paket berbahaya apa pun ke server `dephub.go.id` karena ini adalah target publik nyata (Live Production)[cite: 8].

### B. Lingkup Aktif (Active Reconnaissance)
* [cite_start]**Target:** `172.20.10.5` (Mesin Virtual: VulnOSv2)[cite: 278, 282].
* **Metode:** Network Scanning & Service Enumeration.
* **Lingkungan:** Laboratorium tertutup (*Isolated Lab Environment*).
* [cite_start]**Izin:** Diperbolehkan melakukan pemindaian port (*Port Discovery*) dan deteksi versi layanan (*Version Detection*) secara agresif hanya pada alamat IP yang ditentukan[cite: 9, 279].

---

## 3. Rules of Engagement (Aturan Main)
Seluruh kegiatan simulasi tunduk pada kode etik berikut:

1.  [cite_start]**No Denial of Service (DoS):** Dilarang melakukan tindakan yang dapat membanjiri lalu lintas jaringan atau mematikan layanan target[cite: 10].
2.  **No Data Theft:** Dilarang mencuri, mengubah, atau memanipulasi data sensitif apa pun yang ditemukan (khususnya pada target publik).
3.  [cite_start]**Privacy:** Jika ditemukan data pribadi (PII) pejabat atau pegawai, data tersebut hanya digunakan sebagai bukti konsep (*Proof of Concept*) dalam laporan dan disamarkan jika perlu[cite: 125, 268].
4.  **Specific Target Only:** Pada tahap aktif, serangan hanya boleh ditujukan ke IP `172.20.10.5`. [cite_start]IP lain dalam jaringan (seperti Gateway `172.20.10.1` atau Host lain) **keluar dari batasan (Out of Scope)**[cite: 279].

---

## 4. Inventaris Tools (Persenjataan)
Alat-alat berikut digunakan untuk mendukung skenario pengintaian:

| Kategori | Nama Tools | Kegunaan dalam Skenario |
| :--- | :--- | :--- |
| **DNS & Subdomain** | DNSDumpster, Subfinder, Sublist3r | [cite_start]Memetakan aset digital dan subdomain target publik [cite: 15-17]. |
| **Web Technology** | Wappalyzer, WhatWeb | [cite_start]Mengidentifikasi CMS, Framework, dan Web Server yang digunakan [cite: 18-19]. |
| **User Recon** | theHarvester, Google Search | [cite_start]Mengumpulkan alamat email dan nama pejabat untuk analisis *Social Engineering* [cite: 20-21]. |
| **Network Scanner** | Nmap | [cite_start]Melakukan Host Discovery, Port Scanning, dan OS Fingerprinting pada target lab[cite: 283]. |
| **Packet Analyzer** | Wireshark | [cite_start]Memantau lalu lintas jaringan untuk memastikan *scanning* berjalan sesuai protokol (TCP Handshake)[cite: 446]. |
| **Operating System** | Kali Linux | [cite_start]Platform utama penyerang (*Attacker Machine*)[cite: 281]. |

---

## 5. Objektif Akhir (Goals)
1.  Menghasilkan peta topologi jaringan target simulasi.
2.  Mengidentifikasi daftar layanan (*services*) yang berjalan beserta versinya.
3.  [cite_start]Menemukan kerentanan umum (*common vulnerabilities*) seperti *outdated software* atau *misconfiguration* yang dapat digunakan untuk tahap *Exploitation* di masa depan[cite: 498].
