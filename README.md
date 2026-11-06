# Masjid Digital Enterprise — PWA (GitHub Pages)

Aplikasi PWA yang terhubung ke server Google Apps Script milik masjid. Bisa di-*install* di ponsel/PC dan tetap terbuka saat offline (data terakhir + antrean input).

## Isi repo (5 berkas)
| File | Fungsi |
|---|---|
| `index.html` | Seluruh aplikasi (UI + logika), satu file |
| `manifest.webmanifest` | Metadata PWA (nama, ikon, warna) |
| `sw.js` | Service worker: cache shell untuk mode offline |
| `icon.svg` | Ikon aplikasi |
| `README.md` | Dokumen ini |

## Deploy
1. Deploy dulu backend Apps Script (folder `1_KLIEN/apps-script`) sebagai Web app, salin URL `…/exec`.
2. Buat repo GitHub baru, unggah 5 berkas ini.
3. (Opsional) Edit `index.html`, cari `PASTE_URL_WEB_APP_DI_SINI`, ganti dengan URL `/exec`. Jika tidak diisi, aplikasi meminta URL saat pertama dibuka.
4. Settings → Pages → Source: *Deploy from a branch* → `main` / root → Save.
5. Buka `https://<user>.github.io/<repo>/` → menu browser → **Install app / Tambahkan ke layar utama**.

Portal publik: `https://<user>.github.io/<repo>/?portal=<slug-masjid>`

## Mode offline
- Shell aplikasi di-cache oleh `sw.js`; data terakhir disimpan di perangkat.
- Penerimaan/pengeluaran & data modul baru yang diinput saat offline masuk **antrean** dan dikirim otomatis saat online (idempotency key mencegah dobel).
- Persetujuan, posting, dan reversal **wajib online** demi integritas keuangan.

## Update
Ganti `index.html`, lalu naikkan versi `CACHE` di `sw.js` agar perangkat mengambil versi baru.

© 2026 Penyedia Masjid Digital Enterprise. Penggunaan tunduk pada EULA & lisensi aktif.
