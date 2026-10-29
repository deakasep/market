# clau-market

Runtime candidate: [H2 Tara hospitality bundle](./bundles/tara/README.md).
Operasi klien pertama: [pilot terukur](./commercial/pilot-operations.md).

**Pilar 1 CLAU AI: AI Marketing** (konten & pemasaran) untuk hospitality & tourism Indonesia. Berisi rules, prompt, skill, knowledge, template, dan QA gate untuk memproduksi konten yang **jujur, legal, on-brand, dan siap publish**, dengan AI sebagai content partner, bukan pengganti approval manusia.

> **Status:** Public, hanya untuk dilihat ([LICENSE](./LICENSE)), split dari `clau-content` 2026-10-04. Status kerja terkini: [status & handoff](https://github.com/deakasep/content/blob/main/docs/status.md)
> **Fondasi:** submodule [`core/`](https://github.com/deakasep/core) → `AI-CONSTITUTION.md`, `AI-BOUNDARY.md`, pipeline, orchestrator
> **Workflow konten:** [CONTENT-WORKFLOW.md](./CONTENT-WORKFLOW.md) · **Agent:** [AGENTS.md](./AGENTS.md) · **Credit:** [ACKNOWLEDGMENT.md](./ACKNOWLEDGMENT.md)

> **Constitution:** `core/AI-CONSTITUTION.md` v4.0.0 **Approved** (2026-10-29: platform karyawan AI berlangganan untuk UMKM + hospitality, kredit & top up, posting setelah approval klien; v3.1.0 2026-10-12: `main` wajib lewat PR + CI hijau; v3.0.0 2026-10-09: 5 pilar v2, otonomi A/B/C default B, 4 vertical fokus; v2.0.0 2026-10-04); menggantikan *CLAU AI Content Constitution v1.0.0* (Superseded, arsip di repo [clau-content](https://github.com/deakasep/content/blob/main/CONTENT-CONSTITUTION.md)).
>
> **Otoritas perubahan:** Perubahan atas dokumen Approved hanya atas perintah **Pak Indra** atau **Dea Karisna (d34faiza)** (`core/AI-CONSTITUTION.md` §14).

## Setup

```bash
git clone --recurse-submodules https://github.com/deakasep/market.git
# atau, bila sudah ter-clone:
git submodule update --init --recursive
```

Link ke `core/...` dan `agents/...` di dokumen repo ini baru berfungsi setelah submodule ter-init. Panduan lengkap (update, sync, troubleshooting, GitHub Actions): [SUBMODULE.md](./SUBMODULE.md).

## Target Industri

Sesuai `core/AI-CONSTITUTION.md` v4.0.0 § 2 (UMKM semua sektor + hospitality; template hospitality di bawah tetap berlaku) dan `core/docs/verticals.md`:

| # | Vertical | Status | Fact sheet |
|---|---|---|---|
| 1 | Villa / Guesthouse / Homestay | **Fokus** | [akomodasi](./templates/property-fact-sheet.md) |
| 2 | Restaurant / Cafe / Beach Club | **Fokus** | [F&B](./templates/fnb-fact-sheet.md) |
| 3 | Wedding & Event | **Fokus** | [wedding](./templates/wedding-fact-sheet.md) |
| 4 | Travel & Tour | **Fokus** | [travel](./templates/travel-fact-sheet.md) |
| 5 | Hotel / Resort, Spa / Wellness / Retreat, Tourism Experience | Tetap dilayani | [akomodasi](./templates/property-fact-sheet.md) |

Paket yang dijual, kontrak, dan SOP delivery: [commercial/](./commercial/README.md).

## Struktur

```text
clau-market/
├── README.md · AGENTS.md · CONTENT-WORKFLOW.md · SUBMODULE.md · ACKNOWLEDGMENT.md · LICENSE
├── core/              # submodule → clau-core (jangan diedit di sini)
├── agents/            # submodule → clau-agent (registry & platform; jangan diedit di sini)
├── rules/             # 9 content standard
├── prompts/           # prompt library (caption, campaign, OTA, review, destination, seasonal, reel, stories)
├── skills/            # 9 AI agent skill (SKILL.md + agents/openai.yaml)
├── knowledge/         # segment, platform, kalender, destinasi, voice, market, regulasi
├── templates/         # brief, fact sheet, calendar, campaign, onboarding, approval, report
├── qa/                # 5 QA gate + rubrik skor + lembar kerja review independen (manusia)
├── schemas/           # content-brief.schema.json (v1.4; brief v1.3 tetap valid)
├── commercial/        # katalog paket, discovery, proposal, kontrak & DPA (draft), FAQ klien, SOP delivery
├── automations/       # Level 1 manual
├── examples/          # pilot fiktif (SIMULASI)
└── scripts/           # validate.py, check_caption.py, sync-submodules.sh, check-core-pins.sh
```

## Versi Dokumen

| Dokumen | Versi | Status |
|---|---|---|
| [CONTENT-WORKFLOW.md](./CONTENT-WORKFLOW.md) | 1.0.0 | Approved |
| [AGENTS.md](./AGENTS.md) | 1.1.0 | Approved |

Constitution & boundary di-version di clau-core.

## Klasifikasi Wajib

6 label: **DATA FINAL**, **ASSUMPTION**, **CLIENT CONFIRMATION**, **FIELD VERIFICATION**, **RISK**, **NEXT ACTION**, plus 4 axis (Sensitivity, Lifecycle, Scope, Evidence): [rules/09](./rules/09-DATA-CLASSIFICATION.md).

## Quick Start

1. Baca `core/AI-CONSTITUTION.md`, `core/AI-BOUNDARY.md`, lalu [CONTENT-WORKFLOW.md](./CONTENT-WORKFLOW.md).
2. Onboard client: [templates/client-onboarding.md](./templates/client-onboarding.md).
3. Isi [templates/property-fact-sheet.md](./templates/property-fact-sheet.md), lalu [templates/content-brief.md](./templates/content-brief.md) (valid terhadap [schema](./schemas/content-brief.schema.json)).
4. Pakai skill/prompt yang sesuai (index di bawah).
5. Jalankan `python scripts/check_caption.py` (hasilnya *PASS (mekanis)*, bukan lulus QA), QA gate di [qa/](./qa/claim-verification.md), lalu skor dengan [rubrik](./qa/scoring-rubric.md). Untuk L2/L3 dan penilaian pilot, reviewer manusia memakai [lembar kerja review independen](./qa/independent-review-worksheet.md).
6. Catat approval di [templates/approval-record.md](./templates/approval-record.md).

## Index Rules

| No | Standard | Dipakai ketika |
|---|---|---|
| 01 | [Content Integrity](./rules/01-CONTENT-INTEGRITY-STANDARD.md) | Semua konten, selalu berlaku |
| 02 | [Hospitality Claim](./rules/02-HOSPITALITY-CLAIM-STANDARD.md) | Klaim fasilitas, rating, sertifikasi, harga, lokasi, positioning |
| 03 | [Client Brand Voice](./rules/03-CLIENT-BRAND-VOICE-STANDARD.md) | Menulis atas nama brand client |
| 04 | [Privacy, Consent & UGC](./rules/04-PRIVACY-CONSENT-UGC-STANDARD.md) | Ada foto/nama/review tamu, staf, atau UGC |
| 05 | [Platform](./rules/05-PLATFORM-STANDARD.md) | Format per platform, termasuk Reels, Stories, alt text |
| 06 | [Localization & Bahasa](./rules/06-LOCALIZATION-BAHASA-STANDARD.md) | Konten ID/EN atau multi-bahasa |
| 07 | [AI Visual & Disclosure](./rules/07-AI-VISUAL-DISCLOSURE-STANDARD.md) | Ada visual AI atau editing berat |
| 08 | [Approval & Publication](./rules/08-APPROVAL-PUBLICATION-STANDARD.md) | Sebelum publish, selalu berlaku; review independen L2/L3 |
| 09 | [Data Classification](./rules/09-DATA-CLASSIFICATION.md) | Semua data, selalu berlaku |

## Index Skills

| Skill | Fungsi |
|---|---|
| [`draft-caption`](./skills/draft-caption/SKILL.md) | Caption IG/TikTok/FB sesuai brand voice & claim rule |
| [`draft-reel-script`](./skills/draft-reel-script/SKILL.md) | Script Reels/TikTok: hook, shot list, klaim & consent per shot |
| [`reply-guest-review`](./skills/reply-guest-review/SKILL.md) | Balas review tamu secara aman |
| [`build-content-calendar`](./skills/build-content-calendar/SKILL.md) | Kalender konten bulanan berbasis kalender Indonesia |
| [`write-ota-listing`](./skills/write-ota-listing/SKILL.md) | Deskripsi properti untuk OTA & website |
| [`localize-content`](./skills/localize-content/SKILL.md) | Lokalisasi ID ↔ EN |
| [`plan-seasonal-campaign`](./skills/plan-seasonal-campaign/SKILL.md) | Campaign musiman (Ramadan, Nataru, libur sekolah) |
| [`draft-stories`](./skills/draft-stories/SKILL.md) | Stories IG/Facebook 3–5 frame, info harian yang berlaku hari itu |
| [`build-monthly-report`](./skills/build-monthly-report/SKILL.md) | Laporan bulanan apa adanya: kuota paket, SLA, performa, review |

## Index Prompts

| Jenis | Prompt |
|---|---|
| Caption | [draft-instagram-caption](./prompts/caption/draft-instagram-caption.md) |
| Campaign | [plan-campaign](./prompts/campaign/plan-campaign.md) |
| OTA listing | [write-hotel-description](./prompts/ota-listing/write-hotel-description.md) |
| Review response | [reply-guest-review](./prompts/review-response/reply-guest-review.md) |
| Destination story | [storytelling-destination](./prompts/destination-story/storytelling-destination.md) |
| Seasonal promo | [seasonal-campaign](./prompts/promo-seasonal/seasonal-campaign.md) |
| Reel / short video | [reel-script](./prompts/video/reel-script.md) |
| Instagram Stories | [stories-sequence](./prompts/stories/stories-sequence.md) |
| Template | [prompt-template](./prompts/templates/prompt-template.md) |

## Automations

Level 1 (manual/semi-manual) aktif: [automations/level-1-manual/README.md](./automations/level-1-manual/README.md).

## Task Management

Board kerja: **ClickUp** folder **CLAW AI** → list **Marketing** (board baru sejak 2026-10-29; kode & server di list **Platform**). Board Markdown [clau-content/tasks](https://github.com/deakasep/content/tree/main/tasks) dibekukan sebagai riwayat.

## Validation

```text
python scripts/validate.py
```

Mengecek file wajib, section rules/prompts/skills, frontmatter skill, versi dokumen, schema & contoh brief, link relatif, dan pola secret. Link ke `core/` dan `agents/` dicek hanya bila submodule ter-init; `--require-submodules` membuatnya wajib (dipakai workflow Cross-Repo Validation).

## Lisensi

Proprietary, source-available (hanya untuk dilihat; tidak boleh disalin, dipakai, atau dipakai melatih AI tanpa izin tertulis). Lihat [LICENSE](./LICENSE).
