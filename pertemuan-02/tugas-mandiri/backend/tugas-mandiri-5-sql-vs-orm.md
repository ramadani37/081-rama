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
2. Contoh Operasi Menggunakan SQL (Pendekatan Kompleks)Misalkan terdapat relasi tabel database antara jadwal dan dosen:idmata_kuliahharidosen_id1Pemrograman WebSenin1012Basis DataSelasa102Untuk mengambil data gabungan (join) antara tabel jadwal dan informasi dosen penanggung jawab, digunakan query:
SELECT jadwal.mata_kuliah, jadwal.hari, dosen.nama_dosen 
FROM jadwal 
JOIN dosen ON jadwal.dosen_id = dosen.id 
WHERE jadwal.id = 1;
SQL mentah (raw SQL) memungkinkan optimasi manual menggunakan indeks komposit (composite index) dan analisis query cost secara presisi demi menjaga performa latensi tetap rendah.

3. Contoh Operasi Menggunakan ORM (Pendekatan Kompleks)
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
