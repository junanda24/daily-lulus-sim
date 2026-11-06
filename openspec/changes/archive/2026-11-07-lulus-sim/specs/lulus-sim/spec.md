# Spec — LULUS SIM!

## Konteks
Aplikasi latihan ujian teori SIM (SIM A & C), web static, frontend-only, mobile-first, Bahasa Indonesia. Format ujian asli terverifikasi: 30 soal pilihan ganda, 15 menit, lulus minimal 70% (21 benar) — Perpol 5/2021, Korlantas Polri.

## Requirements

### R1 — Beranda
- SHALL menampilkan judul "LULUS SIM!", ringkasan statistik pengguna (total soal dijawab, akurasi, ujian lulus, streak hari), dan tiga pintu masuk: Latihan, Ujian Simulasi, Kamus Rambu.
- SHALL menampilkan disclaimer "Soal latihan — bukan soal resmi Korlantas Polri" di beranda.
- WHEN pengguna baru membuka aplikasi THEN statistik menunjukkan nol dengan copy penyemangat, bukan layar kosong.

### R2 — Mode Latihan
- SHALL menyediakan 5 kategori: Rambu Lalu Lintas, Marka Jalan, Peraturan & UU 22/2009, Etika & Keselamatan, Teknis Kendaraan & Darurat.
- SHALL menampilkan soal satu per satu; pengguna memilih jawaban lalu langsung melihat benar/salah beserta penjelasan dan rujukan aturan.
- SHALL mengacak urutan soal dan opsi jawaban di setiap sesi latihan.
- SHALL menyimpan progres per kategori (soal yang sudah dijawab benar) di localStorage.
- WHEN pengguna menjawab THEN tombol "Soal Berikutnya" muncul; tidak ada jalan buntu.

### R3 — Mode Ujian Simulasi (format asli)
- SHALL mengambil 30 soal acak dari bank 60 soal, dengan timer mundur 15:00.
- SHALL menampilkan grid nomor soal 1–30 dengan status (dijawab / ragu-ragu / belum), dan memungkinkan lompat ke soal mana pun.
- SHALL mengizinkan menandai soal "ragu-ragu".
- SHALL mengakhiri ujian otomatis saat timer habis (jawaban yang sudah dipilih tetap dinilai).
- SHALL meminta konfirmasi sebelum submit manual, dan menampilkan jumlah soal belum dijawab.
- WHEN timer tersisa 60 detik THEN timer berubah merah dan berdenyut sebagai peringatan.

### R4 — Hasil Ujian & Review
- SHALL menampilkan skor persen, jumlah benar/salah, status LULUS (≥70%) atau BELUM LULUS, dan waktu pengerjaan.
- SHALL menyimpan riwayat ujian (tanggal, skor, lulus/tidak) di localStorage dan menampilkannya di beranda.
- SHALL menyediakan review per soal: soal, jawaban pengguna, jawaban benar, dan penjelasan.
- WHEN pengguna lulus THEN tampilkan perayaan (confetti) dan copy penyemangat.

### R5 — Kamus Rambu
- SHALL menampilkan minimal 24 rambu dalam 4 golongan: Peringatan (kuning), Larangan (merah-putih), Perintah (biru), Petunjuk (hijau/biru).
- SHALL menggambar setiap rambu sebagai SVG original (bukan gambar unduhan, bukan emoji).
- SHALL menampilkan arti dan contoh situasi untuk tiap rambu; tap rambu membuka detail.
- SHALL menyediakan filter per golongan.

### R6 — Bank Soal
- SHALL berisi 60 soal, terbagi ke 5 kategori (Rambu 14, Marka 10, Peraturan 14, Etika 12, Teknis & Darurat 10).
- SHALL tiap soal punya tepat 4 opsi, 1 jawaban benar, penjelasan, dan rujukan aturan (mis. "UU 22/2009 Pasal 134").
- SHALL semua jawaban benar sesuai fakta terverifikasi: 30 soal/15 menit/70% lulus; batas kecepatan 30 (permukiman) / 50 (perkotaan) / 80 (antar kota) / 100 (tol); hak utama kendaraan darurat; denda-denda UU 22/2009 (tanpa SIM Rp1.000.000, tanpa helm Rp250.000, terobos lampu merah Rp500.000, main HP Rp750.000).

### R7 — Statistik & Persistensi
- SHALL menyimpan di localStorage: riwayat ujian, total soal dijawab, akurasi keseluruhan, akurasi per kategori, streak hari latihan.
- SHALL menyediakan tombol reset data dengan konfirmasi.
- WHEN localStorage kosong THEN aplikasi tetap berfungsi penuh (statistik nol).

### R8 — Kualitas umum
- SHALL mobile-first (nyaman di lebar 360px), Bahasa Indonesia natural, tanpa lorem ipsum, tanpa tombol mati, tanpa placeholder palsu.
- SHALL semua ikon digambar sebagai SVG (tanpa emoji sebagai ikon).
- SHALL kontras teks ≥ 4.5:1 dan tombol berlabel jelas; navigasi keyboard dasar berfungsi.

### R9 — Delight
- SHALL ada momen delight: confetti saat lulus ujian, animasi timer, transisi antar-layar, penanda streak.
