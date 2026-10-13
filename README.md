# MoneyMind — Kelola Uang, Raih Masa Depan
**Aplikasi Web Pengelola Keuangan Mahasiswa (Prototipe UAS S1 Sistem Informasi)**

Aplikasi web modern, bersih (Gen Z UI), ringan, dan siap di-deploy langsung ke **GitHub Pages** tanpa backend server atau database eksternal. Semua data tersimpan aman secara offline di browser pengguna menggunakan **HTML5 LocalStorage**.

---

## 1. Ringkasan Fitur Aplikasi

- **Dashboard Finansial Terpadu**:
  - 4 Kartu Metrik Utama dinamis: *Saldo Saat Ini*, *Total Pemasukan Bulan Ini*, *Total Pengeluaran Bulan Ini*, dan *Sisa Anggaran*.
  - Grafik Donut SVG interaktif untuk proporsi pengeluaran kategori.
  - Rekomendasi/Insight Finansial otomatis dihitung secara real-time.
  - Tabel 5 Transaksi Terbaru & ringkasan target tabungan aktif.
- **Manajemen Transaksi (CRUD Penuh)**:
  - Tambah, Ubah (Edit), dan Hapus transaksi pemasukan & pengeluaran.
  - Filter multi-kriteria: Kata kunci pencarian, jenis transaksi, kategori, dan periode bulan.
  - Pengurutan data berdasarkan tanggal atau nominal.
  - Validasi ketat (menolak nominal <= 0 atau nama kosong).
  - Ekspor seluruh riwayat transaksi ke format **CSV**.
- **Anggaran Bulanan (Budgeting)**:
  - Pasang batas anggaran per kategori (Makan & Minum, Transportasi, Pendidikan, Kost, dll).
  - Indikator bar visual dengan status: *Aman (<75%)*, *Perhatian (75-99%)*, dan *Over Budget (≥100%)*.
- **Tujuan Tabungan (Savings Goals)**:
  - Kantong alokasi tabungan untuk laptop kuliah, dana darurat, liburan, sertifikasi.
  - Simulasi menabung (+ deposit) dan penarikan dana tabungan dengan validasi saldo.
- **Statistik & Laporan Finansial**:
  - Filter rentang waktu: Bulan ini, bulan lalu, tahun ini, dan semua waktu.
  - Bar chart perbandingan kategori pengeluaran terbesar.
  - Estimasi rata-rata pengeluaran harian dan rasio tabungan (*saving rate*).
- **Pengaturan & Manajemen Data LocalStorage**:
  - Personalisasi nama mahasiswa dan program studi.
  - **Dark Mode (Mode Gelap)** toggle ramah mata.
  - **Ekspor & Impor Cadangan JSON** untuk transfer data antar laptop/perangkat.
  - Muat Ulang Data Demo mahasiswa & opsi kosongkan data secara aman dengan dialog konfirmasi.

---

## 2. Struktur Proyek

Proyek sengaja dirancang seringkas mungkin agar mudah diuji mahasiswa pemula maupun dievaluasi dosen:

```text
moneymind/
├── index.html        # Seluruh aplikasi (Struktur HTML, Tailwind CSS, Arsitektur Vanilla JS)
└── README.md         # Dokumentasi teknis, cara pakai, dan panduan deployment
```

> **Catatan Struktur Modular:** Semua komponen dirancang menggunakan *single-source of truth* via objek `MoneyMindApp` dengan pemisahan peran modul data, antarmuka, dan penyimpanan lokal.

---

## 3. Pembagian Tugas Kelompok 3 Orang (UAS S1 Sistem Informasi)

| Anggota | Peran Utama | Rincian Tanggung Jawab |
|---|---|---|
| **Anggota 1** | Transaksi & Logika Finansial | Struktur data JSON, fungsi CRUD transaksi, perhitungan saldo kumulatif, validasi form, dan ekspor CSV. |
| **Anggota 2** | UI/UX & Frontend Styling | Layout responsif (Desktop sidebar + Mobile bottom nav), palet warna SaaS/Gen-Z, modal dialog, Dark mode, dan SVG donut chart. |
| **Anggota 3** | Anggaran, Tabungan & Pengujian | Modul alokasi budget bulanan, simulasi target tabungan, skenario pengujian 14 titik, dan dokumentasi deployment. |

---

## 4. Cara Menjalankan Aplikasi Secara Lokal

Aplikasi tidak memerlukan `npm install`, Node.js, atau server backend apa pun!

### Cara 1: Buka Langsung di Browser
1. Unduh atau clone repository ini.
2. Klik ganda (double-click) file `index.html` pada File Explorer / Finder.
3. Aplikasi langsung terbuka di Google Chrome, Edge, Firefox, atau Safari.

### Cara 2: Menggunakan VS Code Live Server
1. Buka folder proyek di **Visual Studio Code**.
2. Pasang ekstensi **Live Server** (oleh Ritwick Dey).
3. Klik kanan file `index.html` lalu pilih **"Open with Live Server"**.

---

## 5. Cara Deployment ke GitHub Pages (100% Gratis & Otomatis)

1. Buat repository baru di [GitHub](https://github.com) dengan nama misalnya `moneymind`.
2. Unggah file `index.html` dan `README.md` ke branch `main`.
3. Di repository GitHub Anda, klik tab **Settings**.
4. Pada menu sebelah kiri, pilih **Pages** (di bawah bagian *Code and automation*).
5. Pada bagian **Build and deployment**:
   - **Source**: Pilih `Deploy from a branch`.
   - **Branch**: Pilih `main` dan folder `/ (root)`.
6. Klik **Save**.
7. Tunggu sekitar 1–2 menit, tautan website publik Anda akan muncul di bagian atas (contoh: `https://username.github.io/moneymind/`).

---

## 6. Skenario Pengujian (Checklist UAS)

| No | Skenario Uji | Prosedur | Hasil yang Diharapkan |
|---|---|---|---|
| 1 | Tambah Pemasukan | Masukkan "Gaji Asisten Lab" Rp500.000 | Saldo bertambah Rp500.000, indikator hijau. |
| 2 | Tambah Pengeluaran | Masukkan "Makan Siang" Rp25.000 | Saldo berkurang, donut chart proporsi terupdate otomatis. |
| 3 | Validasi Input Kosong | Tekan simpan dengan nominal 0 atau kosong | Muncul pesan error merah, data tidak tersimpan. |
| 4 | Edit Transaksi | Ubah nominal transaksi lama | Perhitungan saldo, grafik, dan riwayat langsung sinkron. |
| 5 | Hapus Transaksi | Klik tombol hapus pada transaksi | Dialog konfirmasi muncul, setelah setuju saldo disesuaikan. |
| 6 | Anggaran Kategori | Atur budget Makan Rp300.000 | Progress bar menunjukkan persentase realisasi akurat. |
| 7 | Simulasi Tabungan | Tambah dana Rp100.000 ke target laptop | Progres tabungan naik tanpa mengurangi saldo transaksi konsumsi. |
| 8 | Persistensi Data | Tekan F5 (Refresh halaman) | Seluruh data transaksi & anggaran tetap utuh (LocalStorage). |
| 9 | Ekspor Cadangan JSON | Klik Ekspor JSON di Pengaturan | File `.json` terunduh dan dapat diimpor kembali. |
| 10 | Tampilan Ponsel | Buka via DevTools (Inspect Mobile View) | Muncul navigasi bawah (bottom navigation), tidak ada horizontal scroll. |

---

## 7. Catatan Mengenai Python dan Backend

Jika dosen penguji menanyakan integrasi Python:
- **Arsitektur Saat Ini**: Beroperasi di sisi klien (*Client-Side Static Architecture*) menggunakan Vanilla JS & LocalStorage, sehingga dapat di-hosting tanpa biaya di GitHub Pages.
- **Jika Diperlukan Logika Python**: Logika perhitungan saldo (`calculateFinances`) dan CRUD data transaksi dapat diimplementasikan menggunakan Python CLI atau framework ringan seperti **Flask / FastAPI**.
- Karena GitHub Pages hanya menyajikan aset statis, backend Python dapat dideploy terpisah di platform gratis seperti Render, Railway, atau PythonAnywhere, kemudian dihubungkan ke antarmuka ini melalui `fetch()` API.
