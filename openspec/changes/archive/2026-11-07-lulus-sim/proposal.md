# Proposal — LULUS SIM! (2026-11-07)

## Apa & kenapa
**LULUS SIM!** — aplikasi latihan ujian teori SIM (A & C) yang mensimulasikan ujian asli Korlantas Polri: 30 soal pilihan ganda, timer 15 menit, ambang lulus 70% (21 benar). Ditambah mode latihan per kategori, kamus rambu lalu lintas bergambar, dan statistik progres yang tersimpan di perangkat.

**Masalah yang diselesaikan:** ribuan pemohon SIM gagal di ujian teori pada percobaan pertama — bukan karena tidak bisa mengemudi, tapi karena tidak hafal rambu, marka, dan aturan UU 22/2009. Gagal = pulang, antre ulang 7–30 hari. Materi latihan yang beredar tersebar di blog, tidak menyerupai format ujian asli, dan tidak memberi rasa tegangnya ujian beneran.

## Kenapa ini mengejutkan
- Semua orang Indonesia pernah (atau akan) bikin SIM — pasarnya harfiah seluruh negeri.
- Simulasi yang *persis* format asli (30 soal / 15 menit / 70%) — bukan kuis generik.
- Kamus rambu visual: rambu digambar ulang sebagai SVG original, bisa dipakai belajar sambil menunggu antrean di Satpas.
- Efek kejut: "kok kepikiran sih" — karena yang gagal teori itu memalukan dan mahal waktunya, dan belum ada yang bikin latihan se-serius ini dalam bentuk web app.

## Kenapa bentuk output ini
Web app static (artifact), frontend-only, tanpa login/database. Progres di localStorage. Alasan: soal dan rambu adalah data statis; tidak ada yang perlu server. Bisa dibuka dari HP di mana saja, termasuk di antrean Satpas. Bukan npm/Flutter/CLI karena produknya adalah pengalaman interaktif (ujian + timer + visual rambu), bukan library.

## Kenapa tanpa backend
Tidak ada data yang berubah, tidak ada akun, tidak ada sinkronisasi antar-perangkat yang diminta. Backend hanya menambah biaya dan titik gagal. localStorage cukup untuk riwayat dan streak.

## Uji "sekelas kata-angka / Berani Resign?"
Bukan. Ini produk multi-fitur yang saling nyambung (latihan + ujian simulasi + kamus rambu + statistik + riwayat), ada state bertahan, alur end-to-end (belajar → simulasi → lulus → review), dan visual mobile-first yang niat. Selevel patokan: JUKIR!/TAWAR!/BengkelCheck.

## Anti-AI-slop
Copy Bahasa Indonesia natural, nada teman yang nyemangatin ("Gas, 15 menit, 30 soal — kayak aslinya"), tanpa frasa generik AI, tanpa emoji sebagai ikon, tanpa lorem ipsum.

## IP check
- Semua rambu digambar ulang sebagai SVG original (bentuk standar rambu itu sendiri adalah domain publik / regulasi pemerintah; gambar dibuat dari nol, bukan hasil unduh).
- Tidak ada aset berlisensi, foto, atau karakter pihak ketiga.
- Disclaimer tampil jelas: "Soal latihan — bukan soal resmi Korlantas Polri. Materi disusun dari UU 22/2009, Perpol 5/2021, dan panduan latihan ujian teori SIM."

## Kepatuhan
Mengikuti `CODE_STANDARDS.md` + `ARCHITECTURE.md` (pola static artifact: index.html + styles.css + app.js; satu objek state; localStorage lewat satu modul store; tanpa secret).
