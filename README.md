# Dashboard Saham Usaha

Aplikasi web dashboard investasi/saham unit usaha, siap di-deploy ke GitHub Pages.

## Penting soal data

Aplikasi ini menyimpan data di **localStorage browser** (lihat `src/storageShim.js`).
Artinya data tersimpan per perangkat/browser — kalau Anda buka dari HP dan laptop,
datanya **tidak otomatis sinkron**. Kalau butuh data yang sama di semua perangkat,
beri tahu saya nanti dan bisa disambungkan ke database sungguhan (misal Supabase).

## Cara deploy ke GitHub Pages

1. **Buat repository baru di GitHub**
   - Buka https://github.com/new
   - Beri nama repo, misal `dashboard-saham`
   - Jangan centang "Add a README" (biar tidak konflik)
   - Klik "Create repository"

2. **Upload folder ini ke repo tersebut**

   Opsi A — lewat terminal (kalau punya git terinstall):
   ```bash
   cd saham-webapp
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/USERNAME/dashboard-saham.git
   git push -u origin main
   ```
   Ganti `USERNAME` dan nama repo sesuai punya Anda.

   Opsi B — lewat browser (tanpa terminal):
   - Di halaman repo GitHub, klik "uploading an existing file"
   - Drag & drop semua isi folder `saham-webapp` (termasuk folder `.github` dan `src`)
   - Commit langsung ke branch `main`

3. **Aktifkan GitHub Pages**
   - Di repo, buka **Settings → Pages**
   - Pada "Build and deployment", pilih Source: **GitHub Actions**
   - Selesai — workflow di `.github/workflows/deploy.yml` akan otomatis build & deploy
     setiap kali Anda push ke branch `main`

4. **Tunggu build selesai**
   - Buka tab **Actions** di repo untuk memantau proses build (biasanya 1-2 menit)
   - Setelah selesai, buka **Settings → Pages** lagi — link situs Anda akan muncul
     di bagian atas, biasanya berbentuk:
     `https://USERNAME.github.io/dashboard-saham/`

Setiap kali Anda mau update aplikasi, cukup push perubahan ke `main` dan GitHub
akan otomatis build ulang dan deploy versi terbaru.

## Menjalankan secara lokal (opsional)

Kalau ingin coba dulu di komputer sebelum deploy:
```bash
npm install
npm run dev
```
Lalu buka link yang muncul di terminal (biasanya `http://localhost:5173`).
