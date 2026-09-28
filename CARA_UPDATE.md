# Update Platform Demo Sales — hanya berkas yang berubah

Versi: `main` @ `5f58a6b` (perbaikan lisensi dicabut + animasi pindah halaman).

## Isi paket

| Berkas | Untuk |
|---|---|
| `perubahan-saja.zip` | **Hanya 9 berkas yang berubah**, susunan foldernya sama dengan repo. Ini yang dipakai. |
| `sales-management-platform-lengkap.zip` | Seluruh kode versi terbaru — cadangan bila repo demo ingin disamakan total. |

Berkas yang berubah:

```
app/(app)/admin/_components/TabLisensi.tsx   ← lisensi dicabut → form Ajukan lisensi baru + Trial
components/shared/ProgresNavigasi.tsx        ← BARU: bilah progres pindah halaman
components/shared/Shell.tsx                  ← animasi masuk halaman + memuat yang halus
app/globals.css                              ← gaya animasi
lib/lisensi/server.ts                        ← pengajuan dibuka lagi setelah dicabut, pesan error jelas
supabase/SETUP_LENGKAP.sql                   ← BARU: 1 berkas SQL untuk Supabase baru (tidak perlu di demo)
scripts/gabung-migrasi.mjs                   ← BARU: pembuat berkas SQL di atas
package.json                                 ← tambah perintah `npm run sql:setup`
README.md                                    ← dokumentasi
```

**Database Supabase demo tidak perlu diubah** — tidak ada migrasi baru.

---

## Cara A — Git di laptop (disarankan)

Hanya berkas yang berubah yang terkirim; berkas lain di repo tidak tersentuh.

**1. Ambil repo demo ke laptop** (sekali saja; lewati bila sudah ada foldernya):

```
git clone https://github.com/<akun>/<repo-demo>.git
cd <repo-demo>
```

Bila foldernya sudah ada, masuk dan ambil versi terbaru dulu:

```
cd <repo-demo>
git pull
```

**2. Salin berkas perubahan.** Ekstrak `perubahan-saja.zip`, lalu salin **isinya** (`app`, `components`, `lib`,
`scripts`, `supabase`, `package.json`, `README.md`) ke folder repo → pilih **Replace / Timpa** bila ditanya.
Berkas lain di folder repo tidak ikut terhapus.

**3. Periksa apa yang berubah:**

```
git status
```

Harus muncul kurang lebih 9 berkas (merah). Bila muncul ratusan berkas, berarti salah folder — jangan lanjut.

**4. Kirim ke GitHub:**

```
git add -A
git commit -m "Perbaikan lisensi dicabut + animasi pindah halaman"
git push
```

**5. Selesai.** Vercel demo otomatis deploy ulang (±2–3 menit). Cek di Vercel → Deployments → status **Ready**.

### Arti pesan yang mungkin muncul

| Pesan | Artinya / tindakan |
|---|---|
| `nothing to commit` | Berkas belum tersalin ke folder yang benar. Ulangi langkah 2 di folder yang berisi `package.json`. |
| `rejected ... fetch first` | Ada perubahan di GitHub yang belum ada di laptop. Jalankan `git pull`, lalu `git push` lagi. |
| `Please tell me who you are` | Sekali saja: `git config --global user.email "email@anda.com"` dan `git config --global user.name "Nama"`. |
| Diminta login | Masuk dengan akun GitHub pemilik repo demo (browser akan terbuka). |

---

## Cara B — Tanpa Git (lewat website GitHub)

Untuk tiap berkas yang berubah:

1. Buka repo demo di GitHub → masuk ke folder berkasnya
   (mis. `app` → `(app)` → `admin` → `_components`).
2. **Add file → Upload files** → seret berkas dari hasil ekstrak `perubahan-saja.zip` yang namanya sama
   (mis. `TabLisensi.tsx`) → **Commit changes**. Berkas lama otomatis tertimpa.
3. Ulangi untuk: `lib/lisensi/server.ts`, `components/shared/Shell.tsx`, `components/shared/ProgresNavigasi.tsx`,
   `app/globals.css`, `package.json`, `README.md`, `scripts/gabung-migrasi.mjs`, `supabase/SETUP_LENGKAP.sql`.

Cara B lebih lambat dan tiap berkas memicu deploy sendiri — wajar; yang dipakai adalah deploy terakhir.

---

## Setelah update

Admin → Lisensi di platform demo: bila lisensinya **dicabut**, kini tampil **Tempel Kode Aktivasi baru**
dan **Ajukan lisensi baru** (Trial / Berlangganan) — tidak lagi "Permintaan tidak dapat dikirim".
Pastikan Kantor Pusat juga sudah memakai ZIP terbarunya (lepas ikatan platform otomatis setelah dicabut).
