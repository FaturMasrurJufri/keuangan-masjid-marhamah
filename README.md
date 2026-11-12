# Sistem Informasi Kas Masjid Al-Marhamah

Aplikasi pencatatan, pelaporan, dan transparansi keuangan **Takmir Masjid Al-Marhamah** (Perum Candi Gebang Permai, Wedomartani, Ngemplak, Sleman). 

Aplikasi ini berbasis web (*Single-File HTML*) yang ringan, responsif untuk layar HP maupun laptop, serta terintegrasi langsung secara *real-time* dengan **Google Sheets (Google Drive)** sebagai penyimpanan awan (*cloud database*).

---

## Fitur Utama

1. **Dua Mode Akses dalam 1 Aplikasi (`index.html`):**
   - **Mode Jamaah (Publik / *Read-Only*):** Tampilan bersih tanpa form input. Jamaah dapat melihat laporan bulanan/tahunan serta mengunduh laporan tanpa risiko mengubah atau menghapus data.
   - **Mode Bendahara (Dilindungi PIN):** Membuka form input transaksi, penghapusan data, pengaturan nama pengurus/PIN, serta fitur *Backup/Restore*.
2. **Sinkronisasi Otomatis Google Sheets:** Setiap perubahan transaksi otomatis tersimpan di memori perangkat (`localStorage`) dan dikirim ke Google Sheets.
3. **Kalkulasi Saldo Berkelanjutan (*Running Balance*):** Menghitung otomatis Saldo Awal dari akumulasi bulan/tahun sebelumnya, Total Pemasukan, Total Pengeluaran, hingga Saldo Akhir.
4. **Ekspor Laporan Siap Sebar:**
   - **Simpan JPG (Share WA):** Menghasilkan gambar laporan beresolusi tajam yang siap dikirim ke grup WhatsApp Jamaah.
   - **Simpan PDF:** Menghasilkan dokumen laporan ukuran A4 siap arsip.
   - **Cetak Printout:** Format cetak langsung untuk ditempel di papan pengumuman masjid.
5. **Cadangan Lokal (*Backup & Restore JSON*):** Memungkinkan penyimpanan cadangan data ke file `.json` di HP/komputer.

---

## Struktur File Proyek

Proyek ini hanya membutuhkan **1 file utama** agar mudah dikelola dan tidak terjadi duplikasi data:

- `index.html` — Berisi seluruh struktur antarmuka (HTML), desain (CSS), dan logika aplikasi + koneksi Google Sheets (JavaScript ES6+).
- `README.md` — Dokumentasi panduan penggunaan dan informasi lisensi.

---

## Panduan Penggunaan

### A. Untuk Jamaah (Melihat & Mengunduh Laporan)
1. Buka tautan (*link*) web Sistem Kas Masjid Al-Marhamah melalui browser HP atau komputer.
2. Pada bagian atas tabel laporan, pilih:
   - **Jenis Laporan:** *Laporan Bulanan* atau *Laporan Tahunan*.
   - **Bulan & Tahun:** Pilih periode laporan yang ingin dilihat.
3. Klik tombol **Muat Ulang Data** jika ingin memastikan data yang tampil adalah kiriman terbaru dari Google Sheets.
4. Untuk menyimpan atau membagikan laporan:
   - Ketuk **Simpan JPG (WA)** untuk mengunduh gambar laporan.
   - Ketuk **Simpan PDF** untuk mengunduh dokumen format PDF.
   - Ketuk **Cetak** untuk mencetak langsung ke printer.

---

### B. Untuk Bendahara (Mengelola Transaksi & Pengaturan)

#### 1. Masuk ke Mode Bendahara (Login)
1. Buka halaman web utama (`index.html`).
2. Ketuk tombol kuning **Login Bendahara** di pojok kanan atas.
3. Masukkan PIN Bendahara (PIN bawaan: `1234`), lalu tekan **OK**.
4. Status di atas akan berubah menjadi **Mode Bendahara (Aktif)** dan panel input di sisi kiri/atas akan muncul.

#### 2. Menambah Transaksi Kas (Masuk / Keluar)
1. Pada kotak **Input Transaksi Kas**, isi kolom berikut:
   - **Tanggal Transaksi:** Pilih tanggal terjadinya transaksi.
   - **Jenis Transaksi:** Pilih *Pemasukan (Kas Masuk)* atau *Pengeluaran (Kas Keluar)*.
   - **Kategori Pos Dana:** Pilih dari daftar saran yang muncul (misal: *Infaq Jumat*, *Operasional & Listrik/Air*) atau ketik langsung kategori baru.
   - **Deskripsi / Uraian Lengkap:** Ketik rincian transaksi secara jelas.
   - **Nominal (Rp):** Masukkan angka nominal tanpa titik atau koma (contoh: `1500000`).
2. Ketuk tombol **Simpan Transaksi**. Data akan langsung masuk ke tabel laporan dan otomatis tersinkronisasi ke Google Sheets.

#### 3. Menghapus Transaksi yang Salah Input
1. Pastikan Anda sedang berada di **Mode Bendahara (Aktif)** dan memilih **Laporan Bulanan**.
2. Cari baris transaksi yang ingin dihapus pada tabel laporan.
3. Ketuk tombol merah **Hapus** di kolom paling kanan (*Aksi*), lalu konfirmasi penghapusan.

#### 4. Mengubah Nama Pengurus & Mengganti PIN
1. Di panel **Pengurus, PIN & Cadangan**, ubah **Nama Ketua Takmir** atau **Nama Bendahara** sesuai kepengurusan saat ini.
2. Untuk mengganti PIN keamanan, ketik PIN baru pada kolom **PIN Login Bendahara**.
3. Ketuk tombol **Simpan Pengaturan**. Perubahan nama dan PIN otomatis tersimpan hingga ke Google Sheets.

#### 5. Backup, Restore, & Reset Data
- **Backup JSON:** Ketuk untuk mengunduh seluruh riwayat transaksi ke dalam file `.json` sebagai arsip cadangan di HP/Laptop.
- **Restore JSON:** Ketuk untuk memulihkan data dari file `.json` cadangan yang pernah disimpan.
- **Kosongkan Semua Data Kas:** Menghapus bersih seluruh transaksi di browser HP maupun di Google Sheets (gunakan hanya saat ingin memulai pembukuan baru dari nol).

#### 6. Keluar dari Mode Bendahara (Logout)
- Setelah selesai menginput data, ketuk tombol merah **Keluar Mode Bendahara** di pojok kanan atas agar tampilan kembali terkunci ke Mode Jamaah.

---

## Lisensi (MIT License)

Hak Cipta (c) 2026 Takmir Masjid Al-Marhamah & Fatchurohman

Dengan ini diberikan izin secara cuma-cuma kepada siapa pun yang memperoleh salinan perangkat lunak ini dan file dokumentasi terkait ("Perangkat Lunak"), untuk menggunakan Perangkat Lunak tanpa batasan, termasuk namun tidak terbatas pada hak untuk menggunakan, menyalin, memodifikasi, menggabungkan, mempublikasikan, mendistribusikan, mensublisensikan, dan/atau menjual salinan Perangkat Lunak, dan mengizinkan orang yang menerima Perangkat Lunak untuk melakukan hal tersebut, dengan tunduk pada ketentuan berikut:

Pemberitahuan hak cipta di atas dan pemberitahuan izin ini harus disertakan dalam semua salinan atau bagian penting dari Perangkat Lunak.

---

### MIT License (English Version)

Copyright (c) 2026 Takmir Masjid Al-Marhamah & Fatchurohman

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
