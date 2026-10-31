# CLAUDE.md — clau-market

> Peta repo untuk AI agent. Baca file ini dulu sebelum menjelajah repo. Last updated: 2026-10-23

> 🔔 **Sesi baru: baca [status & handoff CLAU AI](https://github.com/deakasep/content/blob/main/docs/status.md) dulu** (otoritas, keputusan yang sudah diambil, status, pekerjaan terbuka). Repo Jerco milik Pak Indra: jangan disentuh tanpa persetujuan beliau.

## 1. Identitas

| Item | Nilai |
|---|---|
| Repo | `deakasep/market` (public, hanya untuk dilihat; LICENSE) |
| Peran | Pilar 1 — AI Marketing (konten & pemasaran) untuk hospitality Indonesia |
| Submodule | `core/` → clau-core · `agents/` → clau-agent (`agents/core/` ikut pin agents; `core/` disamakan dengan pin itu) |
| Default branch | `main` |

## 2. Peta File

| Path | Fungsi |
|---|---|
| `CONTENT-WORKFLOW.md` · `AGENTS.md` | Workflow konten 9 langkah · instruksi agent Pilar 1 (v1.1.0 Approved) |
| `rules/01–09` | Standard konten (integritas, klaim, voice, privacy, platform, bahasa, AI visual, approval, data) |
| `skills/` · `prompts/` | 9 skill agent · prompt library |
| `knowledge/` | Segment, platform, kalender, destinasi, voice guide, market, regulasi |
| `templates/` · `schemas/` | Template brief/approval + fact sheet per vertical (akomodasi, F&B, wedding, travel) · `content-brief.schema.json` (v1.4) |
| `qa/` | Claim verification (per kalimat), content review, privacy, visual AI, publication, scoring rubric, lembar kerja review independen (manusia) |
| `commercial/` | Paket jual Pilar 1 (Approved v1.0.0): katalog, discovery, proposal, FAQ, SOP delivery (+ realita lapangan), template kontrak & DPA (belum boleh ditandatangani sebelum cek hukum). Harga tidak di repo |
| `examples/` | Pilot **fiktif** (SIMULASI) untuk 4 vertical fokus: villa, kafe, wedding, travel, plus `pilot-2/` (uji ulang alur lengkap). Nama properti fiktif wajib mengandung "Contoh" |
| `automations/` | Otomasi bertahap; `level-1-manual/` = alur manual yang berlaku sekarang (dirujuk `core/docs/getting-started.md`) |
| `scripts/` | `validate.py`, `check_caption.py` (+ `test_check_caption.py`), `sync-submodules.sh`, `check-core-pins.sh` |
| `SUBMODULE.md` | Update, sync, troubleshooting submodule & setup token Actions (identik dengan clau-agent) |
| `.github/workflows/` | `validate.yml`, `cross-repo-validate.yml`, `sync-submodules.yml` (PR bot bump agents + core), `main-guard.yml` |

## 3. Command

```bash
git submodule update --init --recursive
python scripts/validate.py --require-submodules
python scripts/check_caption.py --markdown <file> --brief <brief.json>   # hasil: PASS (mekanis), bukan lulus QA
scripts/sync-submodules.sh --dry-run
```

Jangan mengedit file di `core/` atau `agents/`; edit di repo aslinya.

## Aturan Kerja untuk Agent

- Baca `AGENTS.md` (instruksi agent) dan, untuk aturan induk, `core/AI-CONSTITUTION.md` + `core/AI-BOUNDARY.md`.
- **Otoritas perubahan:** dokumen berstatus Approved hanya diubah atas perintah **Pak Indra** atau **Dea Karisna (d34faiza)**.
- AI **tidak** publish, kirim ke pihak luar, atau self-approve. Review independen L2/L3 = manusia.
- **Jangan** commit data client nyata (brief, fact sheet, caption, harga, foto, data tamu), `.env`, atau credential. Data client nyata ada di Client Workspace (Drive), bukan repo.
- Label evidence dipakai persis: `DATA FINAL`, `ASSUMPTION`, `CLIENT CONFIRMATION`, `FIELD VERIFICATION`, `RISK`, `NEXT ACTION`.
- Commit message: `feat:`, `fix:`, `docs:`, `refactor:`, `chore:`, `test:`. Jalankan validator sebelum push.
- `main` wajib lewat PR dengan CI hijau (`validate`, `cross-validate`; dijaga `main-guard`). Jangan push langsung.

## Hemat kuota: satu chat per topik (perintah owner, 2026-11-01)

- **Satu chat = satu topik/tugas** (mis. web CLAU, JASA, video agen). Chat panjang membuat setiap balasan membaca ulang seluruh riwayat, jadi kuota cepat habis.
- **Di akhir setiap tugas** perbarui file status (CLAU: [content `docs/status.md`](https://github.com/deakasep/content/blob/main/docs/status.md); JASA: `jasa/STATUS.md`) supaya chat baru langsung nyambung.
- **Chat baru** cukup dibuka owner dengan "lanjutkan dari status": AI membaca file status dulu, tidak menanyakan ulang hal yang sudah diputuskan.
- Bila chat sudah panjang atau topik berganti, AI menyarankan owner membuka chat baru (satu kalimat), **setelah** status diperbarui dan semua kerja di-push.
