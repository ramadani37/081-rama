## 1. Pengertian SQL dan ORM

### SQL (Structured Query Language)
SQL adalah bahasa deklaratif standar yang digunakan untuk berkomunikasi secara langsung dengan *Relational Database Management System* (RDBMS). SQL memberikan kendali penuh kepada pengembang untuk memanipulasi data, merancang skema relasional, hingga mengoptimalkan *execution plan* dan indeksasi tingkat rendah.

Contoh SQL tingkat lanjut:
```sql
SELECT j.id, j.mata_kuliah, d.nama_dosen 
FROM jadwal j 
JOIN dosen d ON j.dosen_id = d.id 
WHERE j.hari = 'Senin';

ORM (Object-Relational Mapping)
ORM adalah teknik pemetaan arsitektur perangkat lunak yang memungkinkan programmer berinteraksi dengan database menggunakan objek pemrograman berorientasi objek atau domain model, tanpa harus menulis string query SQL secara manual. ORM menerjemahkan kode aplikasi menjadi Abstract Syntax Tree (AST) sebelum dikompilasi menjadi query native database.

Salah satu contoh ORM modern pada ekosistem Node.js adalah Prisma.

Contoh menggunakan Prisma dengan relasi:
const jadwal = await prisma.jadwal.findMany({
  where: {
    hari: 'Senin'
  },
  include: {
    dosen: true
  }
});
## 2. Contoh Operasi Menggunakan SQL (Pendekatan Kompleks)Misalkan terdapat relasi tabel database antara jadwal dan dosen:idmata_kuliahharidosen_id1Pemrograman WebSenin1012Basis DataSelasa102Untuk mengambil data gabungan (join) antara tabel jadwal dan informasi dosen penanggung jawab, digunakan query:
SELECT jadwal.mata_kuliah, jadwal.hari, dosen.nama_dosen 
FROM jadwal 
JOIN dosen ON jadwal.dosen_id = dosen.id 
WHERE jadwal.id = 1;
SQL mentah (raw SQL) memungkinkan optimasi manual menggunakan indeks komposit (composite index) dan analisis query cost secara presisi demi menjaga performa latensi tetap rendah.

##3. Contoh Operasi Menggunakan ORM (Pendekatan Kompleks)
Jika menggunakan Prisma sebagai ORM, operasi relasional yang kompleks dapat diselesaikan melalui abstraksi relasi otomatis (relation querying):
const detailJadwal = await prisma.jadwal.findUnique({
  where: {
    id: 1
  },
  include: {
    dosen: {
      select: { nama_dosen: true, email: true }
    }
  }
});

##1. Perbedaan Cara Penulisan Operasi Database (SQL vs ORM)
SQL Langsung (Raw SQL): Pengembang menulis instruksi kueri menggunakan string berbasis bahasa SQL standar yang dikirim langsung ke database relasional.

Contoh: SELECT * FROM jadwal WHERE id = 1;

ORM (Object-Relational Mapping): Pengembang berinteraksi dengan database menggunakan pemanggilan fungsi, metode objek, atau domain model dari bahasa pemrograman yang digunakan (seperti JavaScript/TypeScript) tanpa perlu mengetik kueri SQL secara manual.

Contoh: prisma.jadwal.findUnique({ where: { id: 1 } });

##2. Kelebihan SQL Mentah (Raw SQL)
Kontrol Performa Penuh: Memberikan kendali absolut terhadap optimasi indeks, execution plan, dan analisis biaya kueri (query cost).

Fitur Kompleks Tingkat Lanjut: Sangat unggul dan fleksibel dalam menangani operasi tingkat lanjut seperti Window Functions, Recursive CTE (Common Table Expressions), dan Stored Procedures.

Efisiensi Memori: Minimnya overhead karena tidak melalui proses konversi baris tabel menjadi objek (object hydration).

Portabilitas Tinggi: Sangat cocok untuk sistem berskala besar atau pemrosesan transaksi berkecepatan tinggi (high-frequency transaction processing).

##3. Kelebihan ORM
Kecepatan Pengembangan: Meningkatkan produktivitas pengembang secara signifikan melalui abstraksi data berbasis objek (Rapid Application Development).

Manajemen Migrasi: Menyediakan fitur migrasi skema otomatis untuk melacak perubahan struktur database antarversi aplikasi.

Reduksi Human Error: Mengurangi potensi kesalahan penulisan sintaks manual berkat struktur kode yang terstandardisasi.

Dukungan Type-Safety: Terintegrasi erat dengan sistem tipe data modern (seperti TypeScript) guna mencegah inkonsistensi data.

Keamanan Bawaan: Membantu melindungi aplikasi dari celah keamanan umum melalui parameterisasi otomatis.

##4. Pengertian dan Dampak SQL Injection
Pengertian: SQL Injection adalah celah keamanan kritis di mana input atau data berbahaya dari pengguna disisipkan ke dalam struktur kueri SQL, sehingga memanipulasi logika asli perintah database.

Dampak terhadap Data Aplikasi:

Pencurian data sensitif atau informasi rahasia pengguna.

Modifikasi atau perusakan data secara ilegal (data tampering).

Penghapusan seluruh tabel atau database.

Pembajakan sistem otentikasi (authentication bypass) yang memungkinkan penyerang mengambil alih kontrol aplikasi.

##5. Mengapa Parameter Query Mengurangi Risiko SQL Injection?
Penggunaan parameter query (atau parameterized statement) memisahkan secara tegas antara struktur logika perintah SQL dengan nilai data input pengguna.

Dengan teknik ini, database memperlakukan input pengguna secara murni sebagai literal data semata, bukan sebagai bagian dari instruksi kode yang dapat dieksekusi. Akibatnya, karakter atau sintaks berbahaya yang disisipkan oleh penyerang tidak akan mengubah alur logika kueri.

6. Bagaimana ORM Membantu Pengembang Mengakses Database?
ORM membantu pengembang dengan menyederhanakan manipulasi data relasional ke dalam bentuk pemanggilan objek pemrograman yang intuitif, menangani pemetaan relasi antar tabel secara otomatis, serta melakukan konversi hasil baris database menjadi objek aplikasi (object hydration).

Kaitan dengan Contoh Kode:
Melalui Prisma ORM, untuk mengambil data jadwal beserta informasi relasi dosennya, pengembang tidak perlu merangkai sintaks JOIN SQL yang panjang dan rawan salah. Cukup menggunakan fitur relasi bawaan seperti berikut:

JavaScript
const detailJadwal = await prisma.jadwal.findUnique({
  where: {
    id: 1
  },
  include: {
    dosen: {
      select: { nama_dosen: true, email: true }
    }
  }
});
Melalui kode di atas, ORM secara otomatis menerjemahkan instruksi objek tersebut menjadi kueri SQL yang optimal di balik layar, menjaga integritas data, sekaligus memastikan keamanan tipe data (type-safety).
