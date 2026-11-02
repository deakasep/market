# Harga Langganan & Tarif Kredit — CLAU AI (self-serve)

> **Status:** **Approved v1.3.0 (2026-11-02)**, perintah owner Dea Karisna: kredit percobaan 50 kredit / 3 hari sekali per akun (§2a). v1.2.0 (2026-11-02): Mode AI Standar/Pro + model ringan untuk tugas ringan (§3a). v1.1.0 (2026-10-30): disesuaikan dengan sistem yang berjalan (clau-agent 0.14.0) dan alur kredit Sintra.ai. v1.0.0 (2026-10-29): perintah owner Dea Karisna (d34faiza) dengan konfirmasi bahwa Pak Indra sudah menyetujui model langganan seperti Sintra.ai (clau-core AI-CONSTITUTION v4.0.0 §4b). Ini **sumber tunggal** angka harga publik: landing page (`web/src/data/pricing.ts`) dan platform (clau-agent) wajib memakai angka yang sama. Harga layanan terkelola (managed) tetap di price sheet privat owner.

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

- **Urutan pemakaian:** kredit percobaan dulu (§2a), lalu kredit bulanan, lalu kredit top up yang masih berlaku dan paling cepat kedaluwarsa.
- **Masa berlaku top up:** 12 bulan sejak pembayaran lunas. Sisa yang belum terpakai **hangus otomatis** setelah itu.
- **Terlihat di dashboard:** saldo bulanan & top up, dan **top up terdekat yang akan hangus beserta tanggalnya**.
- **Kredit yang tidak hangus:** kredit kembali dari job AI yang gagal/dibatalkan, dan bonus/kompensasi dari tim CLAU.
- **Tanpa paket aktif:** sisa kredit top up tetap bisa dipakai; kredit bulanan hanya ada selama paket aktif.
- **Kredit menipis/habis:** dashboard memberi peringatan; agent berhenti sebelum memanggil AI (tidak ada tagihan tambahan).

## 2a. Kredit Percobaan (seperti trial Sintra.ai)

| Item | Nilai |
|---|---|
| Jumlah | **50 kredit**, gratis, tanpa kartu atau pembayaran |
| Masa berlaku | **3 hari** sejak diberikan; sisa yang belum terpakai hangus otomatis |
| Siapa | **Sekali per akun usaha** (klien), diberikan saat email pendaftar mandiri terverifikasi. Klien yang didaftarkan staf atau klien SIMULASI tidak mendapat kredit percobaan |
| Urutan pakai | Dipakai paling dulu (paling cepat hangus) |
| Refund | Job AI yang gagal/dibatalkan mengembalikan kredit percobaannya; bila masa berlaku sudah lewat, kredit itu ikut hangus |

Kredit percobaan bukan langganan: tidak ada kredit bulanan dan tidak ada tagihan otomatis setelah 3 hari. Untuk lanjut, klien memilih paket (§1) atau top up (§2). Aturan hitung §4 tetap berlaku untuk tarif yang dipotong dari kredit percobaan. Sistem: kontrak clau-core API 0.15.0 (bucket `trial`).

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

## 3a. Mode AI (seperti Spark/Smart/Pro Sintra.ai)

Keputusan owner 2026-11-02: **klien memilih sendiri** tingkat model per pekerjaan; tidak ada model mahal yang dipakai diam-diam.

| Mode | Model (`ASSUMPTION` sampai TASK-004 dikonfigurasi) | Dipakai untuk | Tarif |
|---|---|---|---|
| **Ringan** (otomatis) | Claude Haiku (kelas terbaru) | Tugas ringan yang dipilih sistem: balasan chat singkat, format ulang, ringkas teks pendek | Sama dengan tarif §3 (tidak ada potongan sampai biaya nyata terukur) |
| **Standar** (default) | Claude Sonnet (kelas terbaru) | Semua pekerjaan agent di §3 | Tarif §3 |
| **Pro** (pilihan klien) | **Claude Fable 5.1** | Pekerjaan teks yang klien tandai Pro sebelum mulai | **4× tarif §3**, dibulatkan ke atas (contoh: caption Tara 8 → 32 kredit) |

Aturan mode:

1. Tarif Pro tampil **sebelum** klien mengirim permintaan; pindah mode tidak pernah terjadi otomatis ke Pro.
2. Pro hanya untuk agent teks. Gambar (Nova) dan video (Aruna) memakai model gambar/video sendiri; tarifnya tetap §3.
3. Mode Ringan tidak dipakai untuk pekerjaan berisiko (review negatif, harga/promo, agama/adat, laporan angka); pekerjaan itu minimal Standar dan tetap mengikuti level approval.
4. Pengali 4× dipilih karena harga API Fable 5.1 sekitar 3,3× kelas Sonnet (Fable $10/$50 per juta token masuk/keluar, sumber pihak ketiga 2026-11-02, `ASSUMPTION`); sisa bantalan menjaga aturan §4.1. Dihitung ulang dengan harga resmi saat TASK-004.
5. Mode tidak mengubah aturan persetujuan: semua hasil tetap draft sampai disetujui manusia.
6. Belum aktif: mode berlaku setelah provider AI nyata tersambung (TASK-004). Sampai itu web menandainya **segera hadir**.

## 4. Aturan Hitung (internal, berlaku untuk setiap perubahan tarif)

1. Tarif kredit per aksi **minimal 3× biaya provider AI** per aksi pada nilai jual Rp200/kredit (AI-CONSTITUTION §4b). Biaya provider dihitung dengan kurs berbantalan (di atas kurs pasar) dan tarif provider terbaru.
2. Hitung ulang bila harga provider atau kurs bergerak > 10%, atau model agent diganti. Perubahan tarif = PR ke file ini + landing page + konfigurasi platform, berlaku untuk pemakaian sesudahnya (kredit yang sudah dibeli tidak dikurangi nilainya secara diam-diam: perubahan diumumkan di dashboard).
3. Rincian biaya provider per aksi disimpan di price sheet privat owner, bukan di repo public ini.
4. Belum termasuk PPN; bila usaha sudah PKP, harga tampil termasuk PPN (**CLIENT CONFIRMATION** owner + konsultan pajak, lihat [legal-tax-research-2026.md](./legal-tax-research-2026.md)).

## Revision History

| Version | Date | Status | Summary |
|---|---|---|---|
| 1.3.0 | 2026-11-02 | Approved | Kredit percobaan §2a: 50 kredit, 3 hari, sekali per akun usaha, dipakai paling dulu, sisa hangus. Perintah owner Dea Karisna (pilihan sama dengan trial Sintra.ai) |
| 1.2.0 | 2026-11-02 | Approved | Mode AI (§3a): Ringan (Haiku, otomatis untuk tugas ringan, tarif sama), Standar (Sonnet, default), Pro (Fable 5.1, pilihan klien, 4× tarif). Perintah owner Dea Karisna; aktif setelah TASK-004 |
| 1.1.0 | 2026-10-30 | Approved | Disesuaikan dengan sistem & alur Sintra.ai (perintah owner Dea Karisna): aturan kredit lengkap (urutan pakai, top up hangus 12 bulan otomatis, top up terdekat hangus di dashboard, refund & bonus tidak hangus, top up tanpa paket aktif); chat ditandai Planned; tarif SOP, balas calon pelanggan, pesan tamu, website yang sudah ada di sistem dicantumkan; catatan tahap uji |
| 1.0.0 | 2026-10-29 | Approved | Harga langganan 1/3/6/12 bulan, top up, tarif kredit per aksi untuk model langganan (core AI-CONSTITUTION v4.0.0). Perintah owner dengan konfirmasi persetujuan Pak Indra |
