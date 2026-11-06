# Design — LULUS SIM!

## Stack
- Web artifact static (HTML + CSS + JS client-side). Pola `ARCHITECTURE.md` §1: `index.html` (struktur) + `styles.css` (token → komponen → responsif) + `app.js` (state → render → events).
- Tanpa framework, tanpa backend, tanpa dependency runtime. Font: Barlow Condensed (display, nuansa rambu jalan) + Inter (body) via Google Fonts.
- Data soal + rambu sebagai konstanta JS terpisah dari logic.

## Dunia visual (committed world)
"Jalan raya Indonesia": aspal gelap `#12151A` sebagai latar, marka jalan kuning `#FFC800` sebagai aksen utama, merah rambu `#E5484D`, biru perintah `#2563EB`, putih marka sebagai teks. Tanpa gradient dekoratif (aturan desain). Garis marka putus-putus sebagai motif divider. Mode impeccable: Operate.

## Struktur layar (SPA, satu state)
- `home` — hero judul + statistik + 3 pintu masuk + riwayat ujian + disclaimer.
- `latihan-kategori` — pilih 1 dari 5 kategori (dengan progres per kategori).
- `latihan-soal` — kartu soal, 4 opsi, feedback benar/salah + penjelasan + rujukan, tombol lanjut, progress "Soal 3/14".
- `ujian` — header timer + progress, kartu soal, grid nomor 1–30 (modal/drawer), tandai ragu-ragu, submit.
- `hasil` — skor besar, status LULUS/BELUM LULUS, ring akurasi, review per soal (accordion), tombol "Ujian Lagi" / "Latihan Lagi".
- `kamus` — filter 4 golongan + grid rambu (SVG) + detail modal (arti + contoh situasi).
- `statistik` — bagian dari home + halaman riwayat (boleh digabung di home).

## State — lima keranjang (ARCHITECTURE.md §2)
1. **Lokal** — layar aktif, soal berjalan, jawaban sesi, timer, filter kamus.
2. **URL** — tidak dipakai (artifact static, satu halaman).
3. **Server state** — tidak ada (tanpa backend).
4. **Global client UI** — tidak ada yang butuh store global; state cukup di satu objek `state` + render.
5. **Form** — tidak ada form bebas; pilihan jawaban sebagai button.

Persistensi: satu modul `store` (localStorage key `lulus-sim-v1`): riwayat ujian, progres kategori, total dijawab, streak.

## Data
- `QUESTIONS[60]`: `{ id, category, question, sign? (key rambu), options[4], answer (index), explanation, ref }`.
- `SIGNS[≥24]`: `{ id, group, name, meaning, example, svg (descriptor: shape + glyph) }` — SVG digambar dari descriptor (lingkaran/segitiga/persegi + garis + panah + huruf/angka), bukan file gambar.
- Kategori: `rambu` (14), `marka` (10), `peraturan` (14), `etika` (12), `teknis` (10).

## Animasi & interaksi
- Transisi layar: fade + slide 240ms, exponential ease-out.
- Timer: ring + angka; <60 detik: merah berdenyut.
- Confetti: partikel canvas sederhana saat lulus (warna marka jalan).
- Feedback jawaban: opsi benar hijau, salah merah + getar halus kartu; penjelasan muncul dengan slide-down.
- Micro-interaction: tombol "Gas" berdenyut halus; kartu rambu scale-on-hover; streak dengan penanda api SVG (digambar, bukan emoji).

## Aturan kode
- Satu objek `state`, render murni `state → DOM`, handler tipis, logic bisnis di fungsi bernama.
- querySelector di-cache; IIFE/module scope; tanpa `console.log` tersisa; tanpa god component/file >300 baris (pecah `data.js` untuk soal+rambu bila perlu).
- Semua fakta hukum dicek lawan lembar fakta terverifikasi (lihat spec R6); penjelasan soal mengutip pasal, bukan mengarang.
