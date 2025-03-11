Ini adalah file catatan untuk proyek NEST-NEXT-AUTH.

# Daftar Isi
1. [Pendahuluan](#pendahuluan)
2. [Instalasi](#instalasi)
3. [Penggunaan](#penggunaan)
4. [Kontribusi](#kontribusi)
5. [Lisensi](#lisensi)

# Pendahuluan
Proyek ini adalah implementasi otentikasi menggunakan NEST dan NEXT.

# Instalasi
Untuk menginstal proyek ini, jalankan perintah berikut:
```bash
npm install
```

# Penggunaan
Untuk menjalankan proyek ini, gunakan perintah berikut:
```bash
npm run dev
```

# Kontribusi
Jika Anda ingin berkontribusi, silakan buat pull request atau buka isu di repositori ini.

# Lisensi
Proyek ini dilisensikan di bawah lisensi MIT.

# Catatan

##  Installasi Turbo
-   TurboRepo digunakan untuk mengelola Project next dan nest dalam satu repository yang sama dengan beberapa keuntungan salah satunya adalah, Dapat berbagi dependecy antar project 
    dan dapat Build & Run secara paralel dan otomatis.

    **Fitur**	            **Tanpa Turborepo**	                        **Dengan Turborepo**
    Struktur Repo	        Bisa monorepo, tapi tanpa optimasi	        Monorepo dengan optimasi
    Dependency Management	Harus install ulang di setiap folder	    Berbagi dependency antar proyek
    Build & Run	            Jalankan backend/frontend secara manual	    Bisa paralel dan otomatis
    Caching	                Tidak ada	                                Build/test yang sama tidak diulang
    Task Pipelines	        Manual (pakai script sendiri)	            Bisa otomatis dan berurutan

-   Instalasi
    Instalasi untuk local bisa menggunakan perintah `npm install turbo --save-dev` dan untuk global bisa dengan `npm i turbo --global`.

##  GIT
    1️⃣ git branch -M master
    Mengubah nama branch menjadi master (kalau sebelumnya ada nama branch lain).
    -M berarti mengganti nama branch secara paksa jika sudah ada branch sebelumnya.
    2️⃣ git remote add origin https://github.com/Erputra/nest-next-auth.git
    Menambahkan remote repository dengan nama origin yang mengarah ke GitHub repository-mu.
    Artinya, proyek di lokal akan dikaitkan dengan repository di GitHub.
    3️⃣ git push -u origin master
    Mengunggah (push) kode ke branch master di repository origin (GitHub).
    -u berarti mengatur branch tracking. Jadi, ke depannya kamu bisa cukup mengetik git push tanpa harus menyebutkan origin master.
    Output Penjelasan
    ✅ Enumerating objects: 24, done.
    → Menghitung jumlah file yang akan dikirim.

    ✅ Counting objects: 100% (24/24), done.
    → Semua file sudah dihitung.

    ✅ Delta compression using up to 4 threads
    → Git melakukan kompresi data untuk mempercepat pengiriman.

    ✅ Compressing objects: 100% (23/23), done.
    → Semua file sudah dikompresi sebelum dikirim.

    ✅ Writing objects: 100% (24/24), 14.04 MiB | 1.99 MiB/s, done.
    → Kode sebesar 14.04 MB berhasil dikirim ke GitHub dengan kecepatan 1.99 MB/s.

    ✅ To https://github.com/Erputra/nest-next-auth.git
    → Ini adalah repository tujuan di GitHub.

    ✅ * [new branch] master -> master
    → Branch master di lokal telah dibuat di GitHub.

    ✅ Branch 'master' set up to track remote branch 'master' from 'origin'.
    → Sekarang branch master di lokal terhubung ke branch master di GitHub.

