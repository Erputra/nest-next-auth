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

##  Scaffolding tool
-   Membuat struktur project dari awall.

-   Command
    Bisa menggunakan perintah `npx create-turbo@latest` atau `npm create turbo@latest`


##  Set Up NestJS
-   Navigasi ke folder `next-nest-auth`
-   Install NestJS CLI secara global dengan perintah `npm i -g @nestjs/cli`
-   Pembuatan project nest dengan nama `api` menggunakan perintah `nest new api`

-   💡 Keunggulan
    Instalasi global dapat membuat project dengan cepat dan mempermudah pengelolaan project. CLI menyediakan banyak perintah berguna seperti:
    -   `nest generate module users`          # Membuat module users
    -   `nest generate controller users`      # Membuat controller users
    -   `nest generate service users`         # Membuat service users

    Jika tidak ingin install secara global dapat menggunakan perintah `npx @nestjs/cli new api`, Tapi, Setiap kali ingin menggunakan CLI maka harus memanggilnya dengan npx.

##  Terjadi error waktu commit NestJS API
⚠️  Masalah
    ❌   Karena menggunakan Turborepo, Struktur project memiliki workspace sendiri. 
          Ketika membuat project dengan perintah `nest new api` di `apps/api/`, NestJS otomatis membuat `.git` di dalamnya.
    ❌   Ini membuat `apps/api/` menjadi repository terpisah (sub-repo) sehingga tudak bisa langsung di track oleh repository utama.

-   Solusi
    Kita perlu menghapus `.git` lokal dalam `apps/api/` dengan menjalankan perintah `Remove-Item -Recurse -Force next-nest-auth/apps/api/.git`
    Setelah itu lakukan commit seperti biasa.

##  Terjadi Error "Cannot use JSX unless the --jsx flag is provided"
⚠️  Masalah
     Terjadi Karena TypeScript tidak diatur untuk mendukung JSX.

🔍  Solusi
    Pastikan di `tsconfig.json` di `apps/web` mengaktifkan JSX :

    ```TypeScript
        {
            "compilerOptions": {
                "jsx": "preserve", // Bisa juga "react-jsx" atau "react-jsxdev"
                "module": "NodeNext"
            }
        }
    ```

##  Testing Running Turborepo
🚀  Testing
    Gunakan perintah `npm run dev` pada `next-nest-auth` untuk menjalankan `script dev` dari `packages.json` di `web` dan `api` secara bersamaan.

## Prisma Set Up
🔧  Instalasi
    Gunakan perintah `npx prisma init` di `apps/api` kemudian jika prisma belum ada maka Turborepo akan menginstallnya.
    Prisma akan membuat folder `prisma` yang berisi file `schema.prisma` dan file `.env`.
    Kemudian jalankan `npx prisma db pull` untuk menyesuaikan `schema.prisma` sesuai dengan database fisik yang sudah ada.
    Lalu jalankan `npx prisma generate` untuk membuat Prisma Client agar kita bisa berinteraksi dengan database melalui Prisma di dalam kode.
    Langkah terakhir dengan menjalankan perintah `nest g s prisma` untuk membuat service agar bisa di gunakan secara global di NestJS.

### SCHEMA
    1️⃣ Tabel users (Pengguna)
        Fungsi:
        Menyimpan data pengguna seperti nama, email, dan password.

        Relasi:
        -   Terhubung one-to-one dengan profileInfo melalui id → userId.
        -   Terhubung one-to-many dengan posts melalui id → authorId.
        -   Terhubung one-to-many dengan comments melalui id → authorId.
        -   Terhubung many-to-many dengan groups melalui tabel perantara usersToGroups.

    2️⃣ Tabel profileInfo (Profil Pengguna)
        Fungsi:
        Menyimpan informasi tambahan tentang pengguna dalam format JSON.

        Relasi:
        -   Terhubung one-to-one dengan users melalui userId.
        -   (Setiap pengguna hanya memiliki satu profil tambahan.)

    3️⃣ Tabel posts (Postingan)
        Fungsi:
        Menyimpan postingan yang dibuat oleh pengguna.

        Relasi: 
        -   Terhubung many-to-one dengan users melalui authorId.
        -   (Setiap postingan dimiliki oleh satu pengguna, tapi satu pengguna bisa memiliki banyak postingan.)
        -   Terhubung one-to-many dengan comments melalui id → postId.
        -   (Satu postingan bisa memiliki banyak komentar.)

    4️⃣ Tabel comments (Komentar)
        Fungsi:
        Menyimpan komentar yang dibuat oleh pengguna pada postingan tertentu.

        Relasi:
        -   Terhubung many-to-one dengan users melalui authorId.
        -   (Setiap komentar dimiliki oleh satu pengguna, tapi satu pengguna bisa memiliki banyak komentar.)
        -   Terhubung many-to-one dengan posts melalui postId.
        -   (Setiap komentar hanya terkait dengan satu postingan.)

    5️⃣ Tabel groups (Grup)
        Fungsi:
        Menyimpan daftar grup yang bisa diikuti oleh pengguna.

        Relasi:
        -   Terhubung many-to-many dengan users melalui tabel perantara usersToGroups.

    6️⃣ Tabel usersToGroups (Hubungan Pengguna dan Grup)
        Fungsi:
        Menjembatani hubungan many-to-many antara pengguna dan grup.

        Relasi: 
        -   Terhubung many-to-one dengan users melalui userId.
        -   Terhubung many-to-one dengan groups melalui groupId.
        -   (Dengan ini, satu pengguna bisa masuk ke banyak grup, dan satu grup bisa memiliki banyak pengguna.)

    🔥 Kesimpulan
        Satu pengguna bisa memiliki banyak postingan dan komentar.
        Setiap komentar terhubung ke satu postingan dan satu pengguna.
        Setiap pengguna hanya memiliki satu profil tambahan (one-to-one).
        Pengguna dan grup memiliki hubungan many-to-many melalui tabel usersToGroups. 
###

### QUERY
    ```sql
        CREATE TABLE users (
            id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
            name VARCHAR(255) NOT NULL,
            email VARCHAR(255) UNIQUE NOT NULL,
            password VARCHAR(255) NOT NULL
        );

        CREATE TABLE profileInfo (
            id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
            userId UUID UNIQUE NOT NULL REFERENCES users(id) ON DELETE CASCADE,
            metadata JSONB
        );

        CREATE TABLE posts (
            id SERIAL PRIMARY KEY,
            authorId UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
            title VARCHAR(255) NOT NULL,
            content TEXT NOT NULL
        );

        CREATE TABLE comments (
            id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
            text TEXT NOT NULL,
            authorId UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
            postId INT NOT NULL REFERENCES posts(id) ON DELETE CASCADE
        );

        CREATE TABLE groups (
            id SERIAL PRIMARY KEY,
            name VARCHAR(255) UNIQUE NOT NULL
        );

        CREATE TABLE usersToGroups (
            userId UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
            groupId INT NOT NULL REFERENCES groups(id) ON DELETE CASCADE,
            PRIMARY KEY (userId, groupId)
        );
    ```
###

💡  Prisma Tech
    Di prisma ada migrate & Introspection, migrate di gunakan saat memulai schema dari 0 atau database yang benar benar baru, Sementara Introspection digunakan saat kita sudah memiliki database fisiknya jadi kita tidak perlu menulis schema dari awal.

✅ Kapan Menggunakan Migrasi?
    -    Saat membuat database dari nol.
    -    Saat menambahkan, mengubah, atau menghapus tabel atau kolom dalam database.
    -    Saat ingin memiliki riwayat perubahan database yang terkontrol.
    Gunakan perintah `npx prisma migrate dev --name nama_migrasi`, Perintah ini akan membuat file migrasi dalam folder `prisma/migrations/`.

✅ Kapan Menggunakan Introspeksi?
    -   Saat bekerja dengan database yang sudah ada tanpa harus membuat ulang skema dari nol.
    -   Saat ingin memigrasi proyek lama ke Prisma.
    -   Saat ingin memastikan bahwa skema Prisma sesuai dengan struktur database yang ada.    
    Gunakan perintah `npx prisma db pull`, Ini akan menghasilkan model Prisma yang sesuai dengan database yang sudah ada.

🔥 Perbedaan Utama
**Fitur**	        **Migration**	                                                **Introspection**
Tujuan	            Membuat atau mengubah database berdasarkan Prisma Schema	    Menghasilkan Prisma Schema dari database yang sudah ada
Kapan digunakan?	Saat membangun database baru atau mengubah skema yang ada	    Saat ingin mendapatkan skema Prisma dari database yang sudah ada
Perintah	        `npx prisma migrate dev --name nama_migrasi`	                `npx prisma db pull`
Hasil	            Membuat file migrasi dalam `prisma/migrations/`	                Memperbarui `schema.prisma` agar cocok dengan database

✅  Apa Itu `npx prisma generate`?
    Perintah ini digunakan untuk menghasilkan Prisma Client, yaitu sebuah paket yang memungkinkan kamu untuk berinteraksi dengan database menggunakan Prisma di dalam kode.

    Ini akan:
        Membuat kode TypeScript/JavaScript yang bisa digunakan untuk query database.
        Menghasilkan @prisma/client yang bisa kamu impor dalam kode.

    Jadi, pastikan selalu menjalankan npx prisma generate setelah melakukan perubahan skema!

    Notes:
        -   Start by importing your Prisma Client (See: https://pris.ly/d/importing-client)
        -   Easily identify and fix slow SQL queries in your app. Optimize helps you enhance your visibility: https://pris.ly/--optimize

✅  Apa yang Dilakukan Perintah `nest g s prisma`?
    -   Membuat file Prisma Service dalam folder `src/prisma/`.
    -   Menghasilkan file `prisma.service.ts` dan `prisma.service.spec.ts`.
    -   Menginjeksi PrismaClient ke dalam `src/app.module.ts`.

🚀 Kenapa Harus Membuat Prisma Service di NestJS?
    -   PrismaClient harus diinstansiasi hanya sekali untuk menghindari masalah koneksi database.
    -   Dengan Prisma Service, kita bisa menggunakan Prisma di berbagai module tanpa harus menginstansiasi ulang di setiap file.
    -   Memanfaatkan Dependency Injection (DI) dari NestJS agar Prisma lebih modular dan mudah digunakan.