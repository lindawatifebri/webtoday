# Panduan Deploy: Website PT. Tahan Angin

Situs ini statis: satu halaman HTML tanpa build, tanpa database, tanpa PHP. Semua CSS dan JavaScript ada di dalam `index.html`. Hanya font yang dimuat dari Google Fonts, jadi pengunjung perlu internet.

## Isi folder

| File | Fungsi |
|---|---|
| `index.html` | Halaman utama (seluruh situs) |
| `favicon.svg` | Ikon tab browser |
| `404.html` | Halaman "tidak ditemukan" |
| `robots.txt` | Izin untuk mesin pencari |
| `.htaccess` | Pengaturan Apache (Hostinger, IDwebhost, cPanel) |
| `.nojekyll` | Agar GitHub Pages menyajikan file apa adanya |

Pastikan file yang namanya diawali titik (`.htaccess`, `.nojekyll`) ikut terunggah. Di File Manager cPanel aktifkan "Show Hidden Files".

## Hostinger, IDwebhost, cPanel (hosting biasa)

1. Masuk ke File Manager (atau FTP seperti FileZilla).
2. Buka folder `public_html` (untuk domain utama) atau folder domain tambahan Anda.
3. Unggah **isi** folder `deploy`, bukan folder `deploy` itu sendiri. `index.html` harus berada langsung di `public_html/index.html`.
4. Buka domain Anda. Bila tampil halaman bawaan hosting, hapus `default.php` atau `index.php` bawaan di folder yang sama.
5. Aktifkan SSL gratis di panel hosting, lalu buka komentar bagian "Paksa HTTPS" di `.htaccess`.

## GitHub Pages

1. Buat repository baru di GitHub, lalu unggah isi folder `deploy` ke root repository (cabang `main`).
2. Buka Settings, lalu Pages. Pada Source pilih "Deploy from a branch", cabang `main`, folder `/ (root)`, lalu Save.
3. Tunggu 1 sampai 2 menit. Alamatnya: `https://NAMA-GITHUB.github.io/NAMA-REPO/`.
4. Domain sendiri: isi kolom Custom domain di Settings, lalu atur DNS sesuai petunjuk GitHub.

Catatan: pada alamat `.../NAMA-REPO/`, tautan `/favicon.svg` di `404.html` mengarah ke root domain. Ini tidak mengganggu `index.html`, yang memakai alamat relatif.

## Netlify, Cloudflare Pages, Vercel

Seret folder `deploy` ke dashboard (Netlify Drop) atau hubungkan repository. Build command dikosongkan, publish directory `/` (atau `deploy`).

## Sebelum tayang

- Seluruh isi bersifat **fiktif** dan ada keterangannya di atas halaman dan di footer. Ganti dengan data asli sebelum dipakai untuk bisnis nyata, lalu hapus keterangan itu.
- Ubah teks, alamat, telepon, dan email langsung di `index.html`. Cari bagian `id="kontak"`.
- Setelah punya domain, tambahkan `<link rel="canonical" href="https://domain-anda.com/">` di `<head>`, dan file `sitemap.xml` bila perlu.
- Tombol "Salin" kontak memakai Clipboard API, yang hanya bekerja di HTTPS. Aktifkan SSL.
- Hindari mengunggah file ini ke halaman yang mengaku sebagai perusahaan pelayaran sungguhan tanpa izin pemilik nama tersebut.
