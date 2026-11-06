# LULUS SIM! — Latihan Ujian Teori SIM

## Produk
Aplikasi latihan ujian teori SIM (A & C) untuk orang Indonesia yang mau bikin SIM baru atau naik golongan. Simulasi ujian asli: 30 soal pilihan ganda, timer 15 menit, lulus minimal 70% (21 benar). Dilengkapi mode latihan per kategori, kamus rambu lalu lintas bergambar (SVG original), dan statistik progres yang tersimpan di perangkat.

## Masalah
Banyak pemohon SIM gagal di ujian teori pada percobaan pertama — bukan karena tidak bisa nyetir, tapi karena tidak hafal rambu, marka jalan, dan aturan UU 22/2009. Gagal berarti pulang dan antre ulang 7–30 hari kemudian. Materi latihan yang ada tersebar di blog, formatnya tidak menyerupai ujian asli, dan tidak ada yang memberi rasa "ujian beneran" dengan timer dan ambang lulus yang sama.

## Pengguna
- Calon pemohon SIM A / SIM C (usia 17+, mayoritas anak muda & pekerja)
- Pemohon perpanjangan / naik golongan yang mau pemanasan
- Siapa pun yang mau menguji pengetahuan lalu lintasnya

## Mode (impeccable: Operate)
Pengunjung datang untuk menyelesaikan tugas: latihan dan lulus simulasi. Scanability, rasa ujian yang tegang tapi adil, dan umpan balik instan lebih penting daripada ekspresi visual.

## Dunia visual (committed world)
"Jalan raya Indonesia di malam hari": aspal gelap, marka jalan kuning-putih, merah rambu larangan, biru rambu perintah. Display face: Barlow Condensed (nuansa rambu jalan tol); body: Inter. Tanpa gradient dekoratif, tanpa emoji sebagai ikon — semua ikon digambar sebagai SVG.

## Asumsi (inferred, tanpa wawancara — run terjadwal, user tidak menonton)
- Format ujian asli: 30 soal, 15 menit, lulus ≥ 70% — terverifikasi via riset web 2026-11-07 (Perpol 5/2021; sumber: Korlantas Polri via auksi.co.id, moladin.com, daihatsu.co.id, gridoto.com).
- Soal ditulis dari materi umum ujian teori (rambu, marka, UU 22/2009, etika, teknis kendaraan, darurat) — bukan soal bocoran resmi; disclaimer "latihan, bukan soal resmi Korlantas" tampil di aplikasi.
- Frontend-only, tanpa login/database; progres di localStorage.
