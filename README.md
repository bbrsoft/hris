# hris

# Hris

Hris adalah Enterprise Grade Human Resources Information System (HRIS) yang dapat digunakan untuk membantu memudahkan tugas HRD Perusahaan.

## Tahap Pengembangan

Hris belum dapat digunakan untuk produksi dan sedang dalam proses pengembangan.

## Minimum Requirement

- [X] PHP versi 7.1.7 dan extension yang diperlukan selama instalasi menggunakan composer
- [X] PostgreSQL Database minimal versi 9.6
- [X] Web Server (Apache, Nginx atau IIS)
- [X] APCu extension (untuk Production)

**NOTE**: 

- [X] Sistem ini dikembangkan menggunakan lingkungan pengembangan Linux, pengembang tidak menjamin jika sistem ini dapat berjalan dengan baik pada sistem operasi lain.
- [X] Walaupun dapat berjalan pada DB Engine lain seperti MySQL, namun sistem ini hanya mensupport untuk database PostgreSQL.

## Fitur

- [X] Manajemen Perusahaan
- [X] Support Multi Perusahaan
- [X] Manajemen Jabatan
- [X] Manajemen Karyawan
- [X] Support Multi Alamat
- [X] Support Penempatan Karyawan
- [X] Manajemen Kontrak Kerja
- [X] Manajemen Kontrak Perusahaan dengan Rekanan/Klien
- [X] Karir History
- [X] Promosi, Mutasi, dan Demosi
- [X] Manajemen Shift Kerja
- [X] Manajemen Jadwal Kerja
- [X] Manajemen Absensi dengan fitur *rules*
- [X] Manajemen Hari Libur
- [X] Manajemen dan Perhitungan Lembur sesuai dengan [peraturan yang berlaku](https://gajimu.com/main/pekerjaan-yanglayak/kompensasi/upah-lembur)
- [X] Manajemen BPJS Kesehatan
- [X] Manajemen dan Perhitungan BPJS Ketenagakerjaan (JKK, JKM, JHT dan JP) sesuai dengan [peraturan yang berlaku](http://www.pasienbpjs.com/2017/01/cara-menghitung-iuran-bpjs-ketenagakerjaan.html)
- [X] Pajak PPH21 sesuai [peraturan yang berlaku](https://www.online-pajak.com/id/cara-perhitungan-pph-21)
- [X] Gaji dan Credential data **dienkripsi** dengan algoritma RSA
- [X] Laporan Penggajian
- [X] Laporan Beban Gaji Perusahaan
- [X] Historikal Data Karyawan (Jenjang Karir, Gaji, Tunjangan, dan Pajak)
- [X] Backend Site and API sekaligus
- [X] Soft Delete (data tidak benar-benar dihapus)
- [X] Restore Deleted Record
- [X] Pelacakan Data (CreatedAt, CreatedBy, UpdatedAt, UpdatedBy, dan DeletedAt)

## Cara Install (Menggunakan Docker)

- [X] Clone/Download repository `git clone https://github.com/KejawenLab/Hris.git` dan pindah ke folder `Hris`
- [X] Build image dengan [`docker-compose`](https://docs.docker.com/compose) dengan menjalankan `docker-compose build && docker-compose up` 
- [X] Jalankan perintah `docker exec -it hris_db_1 psql -U hris`, bila perlu memasukkan password, masukkan `hris`
- [X] Jalankan perintah `CREATE EXTENSION IF NOT EXISTS "uuid-ossp";` untuk mengaktifkan ekstensi UUID.
- [X] Jalankan perintah `docker-compose exec app bin/console doctrine:schema:update --force` untuk membuat table yang dibutuhkan
- [X] Jalankan perintah `docker-compose exec app bin/console doctrine:fixtures:load -n` untuk *populate initial* data
- [X] Buka halaman `<HOST>:8000/` untuk halaman admin
- [X] Buka halaman `<HOST>:8000/api` untuk halaman API
- [X] Buka halaman `<HOST>:8080` untuk halaman Adminer

## Cara Install (Manual)

- [X] Clone/Download repository `git clone https://github.com/KejawenLab/Hris.git` dan pindah ke folder `Hris`
- [X] Jalankan [Composer](https://getcomposer.org/download) Install/Update `composer update --prefer-dist -vvv`
- [X] Setup koneksi database pada `.env`
```lang=bash
    _DB_DRIVER="pgsql"
    _DB_USER="hris"
    _DB_PASSWORD="hris"
    _DB_HOST="db"
    _DB_PORT="5432"
    _DB_NAME="hris"
```
- [X] Jalankan perintah `php bin/console doctrine:database:drop --force` untuk menghapus database lama (**optional**)
- [X] Jalankan perintah `php bin/console doctrine:database:create` untuk membuat database
- [X] Aktifkan ekstensi UUID dengan menjalankan perintah `CREATE EXTENSION IF NOT EXISTS "uuid-ossp";` pada Console DB/PgAdmin
- [X] Jalankan perintah `php bin/console doctrine:schema:update --force` untuk membuat table yang dibutuhkan
- [X] Jalankan perintah `php bin/console doctrine:fixtures:load` untuk *populate initial* data
- [X] Simpan username dan password yang ditampilkan untuk digunakan mengakses aplikasi
- [X] Jalankan perintah `php bin/console server:run` untuk mengaktifkan web server
- [X] Buka halaman `<HOST>:<PORT>/` untuk halaman admin
- [X] Buka halaman `<HOST>:<PORT>/api` untuk halaman API

## Unit Test

Untuk menjalankan unit testing, Anda cukup menjalankan perintah `php vendor/bin/phpunit`

## Kontributor

Proyek ini dikembangkan oleh [Mu](https://github.com/bbrsoft) dan para [kontributor]
.

## TODO

Untuk apa saja yang sudah dan belum dikerjakan bisa melihat [TODO LIST](TODO.md)

## ROADMAP

Untuk mengetahui roadmap dari aplikasi HRIS bisa melihat [ROADMAP](ROADMAP.md)

## Lisensi

Proyek ini menggunakan lisensi [MIT](https://tldrlegal.com/license/mit-license) &copy; Muhamad Surya Iksanudin.
Pastikan Anda memahami kewajiban dan hak Anda sebelum Anda memutuskan untuk menggunakan software ini.

## Donasi

Untuk mensupport proyek ini, Anda dapat memberikan donasi melalui rekening berikut:

- BCA 3080206535 a/n B Rahmat

## Profesional Support

Bila Anda memerlukan profesional support atau ingin mengadakan kerjasama dengan saya, dapat menghubungi saya melalui:
- WA: 082169419513

## Keamanan Aplikasi

## Preview

![Hris Profil Karyawan Preview](preview/preview.png)

![Hris Laporan Absensi Preview](preview/preview2.png)

![Hris Detail Gaji](preview/penggajian3.png)

![Hris API Preview](preview/api-preview.png)

Butuh lebih banyak screenshot? silahkan cek folder [preview](preview)
