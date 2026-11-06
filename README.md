# LULUS SIM! — Latihan Ujian Teori SIM A & C

Latihan ujian teori SIM yang mensimulasikan ujian asli Korlantas Polri: **30 soal pilihan ganda, timer 15 menit, lulus minimal 70% (21 benar)**. Dilengkapi mode latihan per kategori, kamus rambu lalu lintas bergambar, dan statistik progres yang tersimpan di perangkat.

> **Disclaimer:** Soal latihan — bukan soal resmi Korlantas Polri. Materi disusun dari UU No. 22 Tahun 2009 tentang Lalu Lintas dan Angkutan Jalan, Perpol 5/2021, dan panduan latihan ujian teori SIM.

## Kenapa ide ini dipilih

Ribuan pemohon SIM gagal di ujian teori pada percobaan pertama — bukan karena tidak bisa mengemudi, tapi karena tidak hafal rambu, marka jalan, dan aturan. Gagal berarti pulang dan antre ulang 7–30 hari kemudian. Materi latihan yang beredar tersebar di blog dan tidak menyerupai format ujian asli. LULUS SIM! memberi rasa "ujian beneran": timer yang sama, ambang lulus yang sama, dan pembahasan per soal supaya yang salah langsung paham — bukan sekadar tahu skor.

## Fitur

- **Beranda** — statistik pengguna (soal dijawab, akurasi, ujian lulus, streak hari), riwayat ujian terakhir, dan tiga pintu masuk.
- **Mode Latihan** — 5 kategori: Rambu Lalu Lintas (14 soal), Marka Jalan (10), Peraturan & UU 22/2009 (14), Etika & Keselamatan (12), Teknis Kendaraan & Darurat (10). Soal dan opsi diacak tiap sesi; jawaban langsung dibahas dengan penjelasan + rujukan pasal.
- **Ujian Simulasi (format asli)** — 30 soal acak dari bank 60 soal, timer mundur 15:00, grid nomor soal 1–30 (dijawab / ragu-ragu / belum), lompat ke soal mana pun, konfirmasi sebelum submit, submit otomatis saat waktu habis. Timer merah berdenyut di 60 detik terakhir.
- **Hasil Ujian** — skor persen, jumlah benar/salah, status LULUS (≥70%) / BELUM LULUS, waktu pengerjaan, review per soal, dan confetti saat lulus.
- **Kamus Rambu** — 34 rambu dalam 4 golongan (Peringatan 12, Larangan 10, Perintah 6, Petunjuk 6), digambar sebagai SVG original, dengan filter per golongan dan detail arti + contoh situasi.
- **Statistik & Riwayat** — riwayat ujian, akurasi keseluruhan dan per kategori, streak hari latihan; semua tersimpan di localStorage (`lulus-sim-v1`), plus tombol reset data dengan konfirmasi.

## Cara pakai

Buka link hasil di HP atau laptop — tidak perlu install, tidak perlu login:

1. **Latihan** — pilih kategori, jawab soal satu per satu, baca penjelasannya.
2. **Ujian Simulasi** — tekan "Mulai ujian", kerjakan 30 soal dalam 15 menit seperti di Satpas. Tandai soal yang ragu-ragu, lalu submit.
3. **Kamus Rambu** — cari rambu yang belum hafal, tap untuk melihat arti dan contoh situasinya.
4. Ulangi sampai skor simulasi stabil di atas 70% — baru gas ke Satpas beneran.

## Cara menjalankan dari source

Aplikasi ini satu file statis (`src/index.html`, 92 KB) — tidak butuh build step:

```bash
# cara 1: buka langsung
open src/index.html

# cara 2: sajikan lewat server lokal
cd src && python3 -m http.server 8137
# lalu buka http://localhost:8137
```

## Tech stack

- HTML + CSS + JavaScript murni (tanpa framework, tanpa backend, tanpa dependency runtime)
- Font: Barlow Condensed (display) + Inter (body) via Google Fonts
- Data soal (60) dan rambu (34) sebagai konstanta JS di dalam `src/index.html`
- localStorage untuk statistik dan riwayat

## Struktur folder

```
2026-11-07-lulus-sim/
├── README.md
├── PRODUCT.md
├── src/
│   └── index.html          # aplikasi lengkap (HTML + CSS + JS + data soal & rambu)
└── openspec/
    └── changes/
        └── archive/
            └── 2026-11-07-lulus-sim/
                ├── proposal.md
                ├── design.md
                ├── tasks.md
                └── specs/
                    └── lulus-sim/
                        └── spec.md
```

## Link hasil

- Aplikasi: artifact `lulus-sim` (dibuka dari Library Muse)
- Repo: https://github.com/junanda24/daily-lulus-sim
- Rilis: 2026-11-07

## Catatan / temuan saat build

- **Format ujian terverifikasi dari riset web** (Perpol 5/2021; sumber Korlantas Polri via beberapa media): 30 soal, 15 menit, lulus minimal 70% (21 benar). Angka-angka hukum di soal (batas kecepatan 30/50/80/100 km/jam, denda tanpa SIM Rp1.000.000, tanpa helm Rp250.000, terobos lampu merah Rp500.000, main HP Rp750.000) dicek satu per satu dan di-spot-check ulang pada file hasil build.
- **Rambu digambar ulang sebagai SVG dari nol** (bentuk + garis + panah + huruf/angka) — bukan hasil unduh, bukan emoji. Audit build pertama menemukan huruf P/S pada rambu larangan parkir/berhenti tidak terlihat; sudah diperbaiki dan terverifikasi dari screenshot.
- **Tidak terverifikasi langsung di probe:** confetti saat lulus (butuh ≥21 benar dari 30 soal), timer merah berdenyut + auto-submit di detik terakhir (butuh menunggu 15 menit), dan modal konfirmasi reset — ketiganya memakai jalur kode yang sama dengan submit manual dan modal lain yang sudah terbukti jalan.
- **Google Fonts gagal dimuat di sandbox audit** karena egress lockdown di mesin build; di perangkat pengguna font termuat normal, dengan fallback font sistem bila offline.
- Yang sengaja tidak dibuat: mode SIM B (materi ujian teori B1/B2 lebih luas — perlu riset dan bank soal terpisah), sinkronisasi antar-perangkat (butuh backend/akun — di luar scope produk statis ini), dan soal bergambar situasi lalu lintas (butuh ilustrasi adegan, bukan cuma rambu).
