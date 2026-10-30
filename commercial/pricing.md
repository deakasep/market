# Harga Langganan & Tarif Kredit — CLAU AI (self-serve)

> **Status:** **Approved v1.1.0 (2026-10-30)**, perintah owner Dea Karisna: disesuaikan dengan sistem yang berjalan (clau-agent 0.14.0) dan alur kredit Sintra.ai. v1.0.0 (2026-10-29): perintah owner Dea Karisna (d34faiza) dengan konfirmasi bahwa Pak Indra sudah menyetujui model langganan seperti Sintra.ai (clau-core AI-CONSTITUTION v4.0.0 §4b). Ini **sumber tunggal** angka harga publik: landing page (`web/src/data/pricing.ts`) dan platform (clau-agent) wajib memakai angka yang sama. Harga layanan terkelola (managed) tetap di price sheet privat owner.

## 1. Paket

Semua paket berisi **semua agent aktif** (agent baru otomatis masuk) dan **500 kredit per bulan**. Kredit bulanan masuk tiap periode bulan berjalan dan tidak menumpuk. Langganan dibayar di muka dan **tidak diperpanjang otomatis** tanpa persetujuan klien.

| Durasi | Harga | Setara per bulan | Hemat |
|---|---|---|---|
| 1 bulan | Rp149.000 | Rp149.000 | – |
| 3 bulan | Rp399.000 | Rp133.000 | 11% |
| 6 bulan | Rp749.000 | Rp124.800 | 16% |
| 12 bulan | Rp1.390.000 | Rp115.800 | 22% |

## 2. Top Up Kredit

| Paket | Harga | Per kredit | Masa berlaku |
|---|---|---|---|
| 250 kredit | Rp50.000 | Rp200 | 12 bulan |
| 550 kredit | Rp100.000 | ±Rp182 (bonus 10%) | 12 bulan |
| 1.500 kredit | Rp250.000 | ±Rp167 (bonus 20%) | 12 bulan |

Aturan kredit (sama dengan sistem, kontrak clau-core API 0.14.0; alur seperti Sintra.ai):

- **Urutan pemakaian:** kredit bulanan dulu, lalu kredit top up yang masih berlaku dan paling cepat kedaluwarsa.
- **Masa berlaku top up:** 12 bulan sejak pembayaran lunas. Sisa yang belum terpakai **hangus otomatis** setelah itu.
- **Terlihat di dashboard:** saldo bulanan & top up, dan **top up terdekat yang akan hangus beserta tanggalnya**.
- **Kredit yang tidak hangus:** kredit kembali dari job AI yang gagal/dibatalkan, dan bonus/kompensasi dari tim CLAU.
- **Tanpa paket aktif:** sisa kredit top up tetap bisa dipakai; kredit bulanan hanya ada selama paket aktif.
- **Kredit menipis/habis:** dashboard memberi peringatan; agent berhenti sebelum memanggil AI (tidak ada tagihan tambahan).

## 3. Tarif Kredit per Aksi

| Aksi | Agent | Kredit | Status agent |
|---|---|---|---|
| Chat dengan agent (per pesan) | Semua | 2 | Planned (fitur chat belum ada) |
| Caption + hashtag + cek fakta | Tara | 8 | Aktif |
| Naskah Reels/TikTok | Raka | 13 | Aktif |
| Rangkaian Stories | Sekar | 8 | Aktif |
| Listing / deskripsi produk | Bayu | 10 | Aktif |
| Balasan komentar/review | Laras | 3 | Aktif |
| Kalender konten 30 hari | Dimas | 18 | Aktif |
| Rencana kampanye musiman | Ayu | 18 | Aktif |
| Terjemahan / lokalisasi | Nara | 5 | Aktif |
| Laporan bulanan 1 halaman | Intan | 20 | Aktif |
| Posting terjadwal | Platform | 1 | Menunggu integrasi kanal |
| Gambar AI (2K) | Nova | 29 | Planned |
| Video AI 8 detik (standar / cepat) | Aruna | 111 / 222 | Planned |
| Analisis data (1 file) | Dara | 20 | Planned |
| Anotasi data (100 baris) | Dara | 10 | Planned |
| Tugas integrasi / developer / website | Teguh | 39 | Planned |
| SOP / dokumen kerja | Teguh | 10 | Planned |
| Balas pertanyaan calon pelanggan | Galih | 3 | Planned |
| Pesan ke tamu (konfirmasi, pengingat) | Sari | 3 | Planned |

Catatan realita (30 Okt 2026): platform masih tahap uji. Agent berstatus **Aktif** sudah lengkap di sistem, tetapi provider AI nyata belum tersambung, jadi pemakaian berbayar baru berjalan setelah peluncuran. Tarif yang dipotong sistem = `clau-agent/backend/app/billing/catalog.py` (dites sama dengan tabel ini).

## 4. Aturan Hitung (internal, berlaku untuk setiap perubahan tarif)

1. Tarif kredit per aksi **minimal 3× biaya provider AI** per aksi pada nilai jual Rp200/kredit (AI-CONSTITUTION §4b). Biaya provider dihitung dengan kurs berbantalan (di atas kurs pasar) dan tarif provider terbaru.
2. Hitung ulang bila harga provider atau kurs bergerak > 10%, atau model agent diganti. Perubahan tarif = PR ke file ini + landing page + konfigurasi platform, berlaku untuk pemakaian sesudahnya (kredit yang sudah dibeli tidak dikurangi nilainya secara diam-diam: perubahan diumumkan di dashboard).
3. Rincian biaya provider per aksi disimpan di price sheet privat owner, bukan di repo public ini.
4. Belum termasuk PPN; bila usaha sudah PKP, harga tampil termasuk PPN (**CLIENT CONFIRMATION** owner + konsultan pajak, lihat [legal-tax-research-2026.md](./legal-tax-research-2026.md)).

## Revision History

| Version | Date | Status | Summary |
|---|---|---|---|
| 1.1.0 | 2026-10-30 | Approved | Disesuaikan dengan sistem & alur Sintra.ai (perintah owner Dea Karisna): aturan kredit lengkap (urutan pakai, top up hangus 12 bulan otomatis, top up terdekat hangus di dashboard, refund & bonus tidak hangus, top up tanpa paket aktif); chat ditandai Planned; tarif SOP, balas calon pelanggan, pesan tamu, website yang sudah ada di sistem dicantumkan; catatan tahap uji |
| 1.0.0 | 2026-10-29 | Approved | Harga langganan 1/3/6/12 bulan, top up, tarif kredit per aksi untuk model langganan (core AI-CONSTITUTION v4.0.0). Perintah owner dengan konfirmasi persetujuan Pak Indra |
