# Pilkades Serentak (satu kecamatan)

Tampilan di **GitHub Pages**, data di **Google Spreadsheet** lewat **Google Apps Script** (API).

```
GitHub Pages (index.html)  --HTTPS-->  Apps Script (/exec)  -->  Google Spreadsheet
```

## A. Pasang backend (Google Spreadsheet + Apps Script)
1. Buat **Google Spreadsheet kosong baru** → menu **Extensions > Apps Script**.
2. Hapus isi `Code.gs`, tempel seluruh isi `apps-script/Kode.gs`. Simpan.
3. Pilih fungsi **setup** → **Run** → beri izin akses (sekali). Sheet Desa, Calon, Admin, Pemilih, Suara dibuat otomatis.
4. **Deploy > New deployment** → jenis **Web app**:
   - Execute as: **Me**
   - Who has access: **Anyone**  (bukan "Anyone with Google account")
5. Salin **Web app URL** (berakhiran `/exec`).
   Cek: buka URL itu di peramban, harus tampil `{"ok":true,"layanan":"Pilkades Serentak API"}`.

## B. Pasang tampilan (GitHub Pages)
1. Buat repository GitHub, unggah isi folder ini: `index.html`, `config.js`, `.nojekyll` (folder `apps-script` boleh ikut).
2. Edit `config.js`, ganti `API_URL` dengan Web app URL dari langkah A5.
3. Repository **Settings > Pages** → Source: *Deploy from a branch* → Branch: `main`, folder `/ (root)` → Save.
4. Alamat situs: `https://NAMA-AKUN.github.io/NAMA-REPO/` (tunggu 1–2 menit).

## C. Pakai
1. Buka situs → **Admin** → **Admin Kecamatan**, PIN awal `admin123` → **segera ganti PIN** (menu Pengaturan).
2. Pengaturan: nama kecamatan, **tanggal, jam mulai, jam selesai** (WITA). Pemilihan dibuka/ditutup otomatis.
3. Tambah Desa → Calon → akun Admin Desa. Admin Desa menambah pemilih dan **mencetak undangan ber-QR**.
4. **Cetak undangan dari alamat GitHub Pages yang final** (bukan dari file lokal). QR memuat alamat situs ini; jangan pindah domain/nama repo setelah undangan tercetak.

## Mengubah kode backend
Setelah `Kode.gs` diubah: **Deploy > Manage deployments > ikon pensil > Version: New version > Deploy**. Alamat `/exec` tidak berubah.
