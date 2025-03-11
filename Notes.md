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

