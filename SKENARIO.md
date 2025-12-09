# Skenario Simulasi & Rules of Engagement (RoE)

## 1. Latar Belakang & Peran

Dalam simulasi Tugas Besar ini, penulis bertindak sebagai **Konsultan Keamanan Siber Eksternal** (*External Security Consultant*). Penulis ditugaskan untuk melakukan audit keamanan awal (*initial security audit*) terhadap infrastruktur target.

Fokus utama dari kegiatan ini adalah **Information Gathering (Reconnaissance)** untuk mengidentifikasi potensi titik masuk (*entry points*) pada infrastruktur online maupun offline, serta memetakan permukaan serangan (*attack surface*) tanpa melakukan eksploitasi merusak.

---

## 2. Lingkup Target (Scope of Work)

Audit ini dibagi menjadi dua kategori berdasarkan jenis target dan metode interaksi yang diizinkan:

### A. Lingkup Pasif (Passive Reconnaissance)
* **Target:** `dephub.go.id` (Kementerian Perhubungan Republik Indonesia).
* **Metode:** OSINT (*Open-Source Intelligence*).
* **Batasan:** Pengumpulan informasi hanya dilakukan menggunakan sumber daya publik yang tersedia di internet.
* **Larangan Keras:** Dilarang melakukan *scanning* aktif, *brute-force*, atau mengirimkan paket berbahaya apa pun ke server `dephub.go.id` karena ini adalah target publik nyata (Live Production).

### B. Lingkup Aktif (Active Reconnaissance)
* **Target:** `172.20.10.5` (Mesin Virtual: VulnOSv2).
* **Metode:** Network Scanning & Service Enumeration.
* **Lingkungan:** Laboratorium tertutup (*Isolated Lab Environment*).
* **Izin:** Diperbolehkan melakukan pemindaian port (*Port Discovery*) dan deteksi versi layanan (*Version Detection*) secara agresif hanya pada alamat IP yang ditentukan.

---

## 3. Rules of Engagement (Aturan Main)

Seluruh kegiatan simulasi tunduk pada kode etik berikut:

1.  **No Denial of Service (DoS):** Dilarang melakukan tindakan yang dapat membanjiri lalu lintas jaringan atau mematikan layanan target.
2.  **No Data Theft:** Dilarang mencuri, mengubah, atau memanipulasi data sensitif apa pun yang ditemukan (khususnya pada target publik).
3.  **Privacy:** Jika ditemukan data pribadi (PII) pejabat atau pegawai, data tersebut hanya digunakan sebagai bukti konsep (*Proof of Concept*) dalam laporan dan disamarkan jika perlu.
4.  **Specific Target Only:** Pada tahap aktif, serangan hanya boleh ditujukan ke IP `172.20.10.5`. IP lain dalam jaringan (seperti Gateway `172.20.10.1` atau Host lain) **keluar dari batasan (Out of Scope)**.

---

## 4. Inventaris Tools (Persenjataan)

Alat-alat berikut digunakan untuk mendukung skenario pengintaian:

| Kategori | Nama Tools | Kegunaan dalam Skenario |
| :--- | :--- | :--- |
| **DNS & Subdomain** | DNSDumpster, Subfinder, Sublist3r | Memetakan aset digital dan subdomain target publik. |
| **Web Technology** | Wappalyzer, WhatWeb | Mengidentifikasi CMS, Framework, dan Web Server yang digunakan. |
| **User Recon** | theHarvester, Google Search | Mengumpulkan alamat email dan nama pejabat untuk analisis *Social Engineering*. |
| **Network Scanner** | Nmap | Melakukan Host Discovery, Port Scanning, dan OS Fingerprinting pada target lab. |
| **Packet Analyzer** | Wireshark | Memantau lalu lintas jaringan untuk memastikan *scanning* berjalan sesuai protokol (TCP Handshake). |
| **Operating System** | Kali Linux | Platform utama penyerang (*Attacker Machine*). |

---

## 5. Objektif Akhir (Goals)

1.  Menghasilkan peta topologi jaringan target simulasi.
2.  Mengidentifikasi daftar layanan (*services*) yang berjalan beserta versinya.
3.  Menemukan kerentanan umum (*common vulnerabilities*) seperti *outdated software* atau *misconfiguration* yang dapat digunakan untuk tahap *Exploitation* di masa depan.
