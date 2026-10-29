# H2 — Tara hospitality bundle

Candidate untuk SIMULASI, bukan production release. Satu paket immutable dari sumber
core/market/persona yang dipin, dengan output schema H1, validator config, kontrak tool
read-only, metadata freshness dan 60 skenario evaluasi. Tidak ada data klien nyata.

```bash
git submodule update --init --recursive
python scripts/tara_bundle.py check
python scripts/tara_bundle.py build --output /tmp/clau-tara-bundle
python -m unittest discover -s scripts -p 'test_*.py'
```

`manifest.json` memuat SHA-256 exact bytes. `prompt-version.txt` adalah hash manifest
canonical sesuai H1. `sources.json` menentukan allowlist sumber; hanya file yang disebut
yang disalin ke artifact. Build tidak mengambil file baru dari internet dan tidak
memperbarui checksum diam-diam. File berubah → `check` gagal. Setelah review perubahan:
`python scripts/tara_bundle.py refresh`, regression tests, PR, lalu expected digest baru.
Jangan memakai refresh untuk membenarkan artifact asing atau rusak.

Output schema diturunkan dari H1; perubahan kontrak harus di core terlebih dahulu.
Tool contracts adalah spesifikasi H2, bukan bukti bahwa tool runner telah diimplementasikan.
Provider dipin `fake`/`fake-0`: real provider/model/settings harus menjadi bundle versi
baru setelah persetujuan konfigurasi, privacy/budget gates dan regression eval.

## Versi

- **0.1.2** (2026-10-29): hanya checksum `core/AI-CONSTITUTION.md` v4.0.0 dan `core/AI-BOUNDARY.md` v2.0.0 (model langganan) yang berubah; aturan market, persona dan schema tetap. Digest `5f571c41bbe603135c936123dda7a91410a1ed1ff5f4e193a9057c261b673946`. Tetap candidate SIMULASI.

## Scope

Villa/guesthouse/homestay/hotel/resort, restoran/cafe/beach club, spa/wellness,
wedding/event dan travel/tour. Channel Instagram, Facebook, TikTok, GBP. Caption feed,
carousel, Reels/TikTok, promo dan informasi; tidak meliputi script video penuh atau OTA.
Bilingual memakai dua generation terpisah yang diperiksa kesetaraan faktanya.

## Bukti yang belum tersedia

- `eval-cases.json` adalah input dan expected behavior, **bukan 60 hasil model lulus**.
- `fixtures.json` hanya contoh schema-valid; tidak dinilai sebagai kualitas copy manusia.
- Knowledge dapat mengandung ASSUMPTION. `knowledge-index.json` menyimpan sumber internal,
  waktu inventory dan status belum diverifikasi ulang; tidak mengarang tanggal akses sumber primer.
- H3: image/loader, context tenant-scoped, provenance dan freshness enforcement.
- H4: rekonsiliasi seluruh caption, validator pipeline, penyimpanan evidence dan review UI.
- H5/H6: provider nyata, pengukuran biaya/latency, output regression dan human rubric.
- H7: pilot simulasi dan klien nyata dengan bukti approval. Lihat
  [pilot operations](../../commercial/pilot-operations.md).

Promosi wajib: critical hallucination/leakage/privacy/injection success = 0;
schema-valid ≥99%, deterministic ≥95%, human mean ≥4.2/5 dan setiap dimensi ≥3,
approval tanpa major revision target ≥80%. Dengan 60 kasus, satu schema failure
sudah di bawah 99%. Jangan membulatkan untuk meloloskan gate; denominator harus lengkap.
Hasil manusia dan legal tidak dapat diisi AI.
