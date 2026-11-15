# Tinta

Ruang menulis lokal-first yang tidak mengunci fiturnya. Buku, bagian, dan bab; editor
tanpa gangguan dengan simpan otomatis; riwayat versi; pencarian lintas buku; statistik;
Markdown; dan ekspor — semuanya terbuka, tanpa akun, iklan, atau versi Pro.

Dibangun ulang secara **clean-room** dari fitur publik aplikasi menulis. Nama, palet, ikon,
 sampul, dan seluruh teks di sini dibuat untuk Tinta. Tidak ada kode, aset, logo, font, atau
teks milik aplikasi lain yang dipakai.

## Menjalankan

```bash
npm install       # atau npm ci
npm run dev       # http://localhost:3000
npm run build     # dist/index.html — satu berkas mandiri
npm run typecheck
```

Build memakai Vite + plugin single-file. Hasil `dist/index.html` (±600 KB, font ikut
tertanam) bisa dibuka langsung dari disk atau disajikan dari host statis mana pun.

## Fitur

- Editor fokus dengan simpan otomatis, hitungan kata/karakter, mode ketik, garis bantu,
  empat tema, tipografi yang bisa diatur, dan bilah sisipan frasa.
- Buku → bagian → bab, tarik-lepas urutan, duplikat, pindah antar buku, dan sampah dengan
  pemulihan.
- Riwayat otomatis/manual, diff baris, pratinjau, dan pemulihan dengan cadangan pengaman.
- Markdown per naskah dengan pratinjau aman; format teks lewat bilah alat dan pintasan.
- Cari & ganti lintas buku dengan opsi huruf besar/kecil, regex, filter buku, dan sorotan.
- Statistik harian, runtutan, peta panas 17 minggu, target kata, dan daftar terakhir disentuh.
- Ekspor TXT/Markdown/HTML, gambar PNG panjang, PDF lewat cetak, seluruh pustaka ke
  Markdown, serta cadangan JSON penuh + impor.
- Lokal-first: data di `localStorage` (`tinta.v1`), tanpa jaringan. Ekspor cadangan sebelum
  membersihkan data situs.

## Struktur

```
src/
  components/    shell, dialog, menu, cover, toast
  lib/           store, types, defaults, seed, markdown, diff, export, router, text
  screens/       Pustaka, Buku, Editor, Riwayat, Cari, Statistik, Sampah, Setelan
  styles/        tokens.css (tema), app.css
replica/         recon, fitur, arsitektur, desain, brand, QA, parity
artifacts/       build satu berkas + arsip sumber (dibuat setelah commit)
```

## Catatan

- Tidak ada backend, analitik, cookie, atau permintaan keluar. Font dan ikon ikut dibundel.
- Data peramban bisa hilang jika situs dibersihkan; aplikasi mengingatkan dan menyediakan
  cadangan JSON.
- Dua tab yang mengetik di naskah yang sama secara bersamaan masih last-writer-wins.
- Dokumen perencanaan lengkap ada di [`replica/`](replica/).
