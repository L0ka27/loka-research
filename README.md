# Loka Research — Setup GitHub Pages

Struktur folder ini:

```
loka-research-site/
├── index.html                  ← homepage, daftar semua laporan
└── reports/
    └── cast2030/
        └── index.html           ← laporan CAST2030
```

Setiap laporan baru = 1 folder baru di dalam `reports/`, isinya `index.html`.
Biar homepage-nya kedetect laporan baru, tambahin satu blok `<a class="report-card">` di `index.html` (contohnya udah ada, tinggal duplikat & ganti isinya).

## Opsi A — Deploy ke Vercel (paling cepat, nggak perlu git)

1. Buka [vercel.com/new](https://vercel.com/new), login pakai akun Google/GitHub
2. Pilih upload folder / drag & drop project, lalu drag folder `loka-research-site` ini ke situ
3. Vercel otomatis detect `vercel.json` dan deploy sebagai static site
4. Dapat URL kayak `loka-research-site.vercel.app` — laporan CAST ada di `.../reports/cast2030`
5. Custom domain nanti: Project Settings → Domains

**Catatan:** kalau upload manual (bukan connect ke repo GitHub), tiap nambah laporan baru kamu perlu drag & drop ulang seluruh folder. Kalau mau auto-deploy tiap ada laporan baru, hubungkan repo GitHub (Opsi B di bawah) ke project Vercel — sekali connect, tinggal push ke GitHub dan Vercel auto-redeploy sendiri.

## Opsi B — Deploy ke GitHub Pages (gratis selamanya, sekalian jadi source buat Opsi A)

1. Buat akun GitHub kalau belum punya: github.com
2. Buat repository baru:
   - Nama repo: `<username-kamu>.github.io` (contoh: kalau username-mu `loka723`, nama repo-nya HARUS `loka723.github.io` — ini bikin URL-nya langsung bersih tanpa embel-embel nama repo)
   - Set ke **Public**
3. Upload semua isi folder ini (index.html + folder reports/) ke root repo tersebut. Paling gampang: drag & drop lewat browser di halaman repo GitHub (tombol "Add file" → "Upload files").
4. Buka tab **Settings** di repo → **Pages** (menu kiri) → pastikan source-nya "Deploy from a branch", branch `main`, folder `/ (root)` → Save.
5. Tunggu 1-2 menit, situsnya akan live di:
   `https://<username-kamu>.github.io`
   dan laporan CAST2030 ada di:
   `https://<username-kamu>.github.io/reports/cast2030/`

## Nambah laporan baru ke depannya

1. Bikin folder baru: `reports/<nama-token>/`
2. Taruh file laporan (`index.html`) di situ
3. Tambahin satu blok kartu baru di homepage `index.html`, contoh:

```html
<a class="report-card" href="reports/nama-token/">
  <div class="report-top">
    <span class="report-title">NAMA TOKEN</span>
    <span class="report-date">Bulan Tahun</span>
  </div>
  <p class="report-desc">Satu kalimat ringkasan laporan.</p>
  <span class="verdict-chip">VERDICT DI SINI</span>
</a>
```

4. Upload ulang ke GitHub (atau pakai `git push` kalau udah nyaman pakai git dari terminal)

## Custom domain (opsional, nanti-nanti aja)

Kalau suatu saat mau pakai domain sendiri (misal `lokaresearch.id`), tinggal tambah file `CNAME` di root repo isinya domain itu, terus arahkan DNS domain ke GitHub Pages. Nggak perlu dipikirin sekarang — `username.github.io` udah cukup profesional buat mulai.
