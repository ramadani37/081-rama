Status Code 200 (OK)
Arti: Permintaan (request) dari client berhasil diterima, diproses, dan diselesaikan dengan sempurna oleh server.
Kapan Terjadi: Setiap kali Anda membuka halaman web, mengambil data API, atau mengirim data yang valid dan server merespons sesuai harapan.
Kondisi Server: Sehat, tidak ada kendala sama sekali.
<img width="531" height="410" alt="Cuplikan layar 2026-10-07 102248" src="https://github.com/user-attachments/assets/6f35826f-e307-43f2-b61f-52e4b9b427e5" />

Status Code 201 (Created)
Arti: Permintaan berhasil diproses oleh server dan menghasilkan terciptanya sumber daya (resource) baru di dalam sistem atau database.
Kapan Digunakan: Kode ini paling sering dikembalikan oleh server sebagai respons dari metode POST (misalnya ketika Anda melakukan registrasi akun baru, membuat postingan baru, atau menambahkan data produk).
Contoh Kasus:
Saat Anda mengisi formulir pendaftaran akun dan menekan tombol Sign Up, server menerima data Anda, menyimpannya ke database, memberikan ID unik baru (misalnya id: 50), lalu mengirimkan respons 201 Created ke browser/aplikasi Anda sebagai tanda bahwa akun baru telah resmi dibuat.
<img width="551" height="429" alt="Cuplikan layar 2026-10-07 120356" src="https://github.com/user-attachments/assets/e5f92089-a898-45e2-8b72-5b32cb1dca51" />

Status Code 400 (Bad Request)
Arti : Permintaan ditolak karena server tidak mengenal siapa yang mengirim request (belum terautentikasi).
Penyebab : Pengguna mencoba mengakses halaman profil atau dashboard tanpa melakukan login terlebih dahulu, atau token akses (API token) yang dikirim sudah kedaluwarsa/salah.
Solusi : Harus melakukan login atau memasukkan kredensial yang valid terlebih dahulu agar server mengenali identitasnya.
<img width="528" height="388" alt="Cuplikan layar 2026-10-07 104546" src="https://github.com/user-attachments/assets/be3a006a-7079-4196-b4f2-a7d29cd7771e" />

Status Code 401 (Unauthorized)
Arti: Permintaan ditolak karena server tidak mengenal siapa yang mengirim request (belum terautentikasi).
Penyebab: Pengguna mencoba mengakses halaman profil atau dashboard tanpa melakukan login terlebih dahulu, atau token akses (API token) yang dikirim sudah kedaluwarsa/salah.
Solusi bagi Client: Harus melakukan login atau memasukkan kredensial yang valid terlebih dahulu agar server mengenali identitasnya.
<img width="530" height="449" alt="Cuplikan layar 2026-10-07 105011" src="https://github.com/user-attachments/assets/b46dc5fa-e51f-4b93-ad44-8d5272de9fc9" />

Status Code 403 (Forbidden)
Arti: Permintaan ditolak karena server mengenal siapa Anda, tetapi Anda tidak diizinkan untuk mengakses sumber daya tersebut.
Penyebab: Pengguna sudah login, tetapi akunnya hanya berstatus User biasa yang mencoba mengakses halaman khusus Admin. Server melarang keras tindakan tersebut.
Solusi bagi Client: Berhenti mencoba karena akun tersebut memang tidak memiliki hak akses (privilege) untuk area itu.Berkaitan dengan hak akses (Kamu tahu siapa saya, tapi kamu tidak boleh masuk). Terjadi karena user biasa mencoba masuk ke halaman khusus admin.
<img width="542" height="428" alt="Cuplikan layar 2026-10-07 114417" src="https://github.com/user-attachments/assets/77a16e29-f296-4779-9162-8cb9230a905c" />

Status Code 404 (Not Found)
Arti: Server berhasil dihubungi, tetapi sumber daya atau alamat URL yang diminta tidak ditemukan.
Kapan Terjadi: Ketika pengguna salah mengetik alamat tautan (typo), atau mengakses halaman yang sudah dihapus oleh pengelola web.
Kondisi Server: Server dalam keadaan sangat sehat dan berfungsi normal. Server menolak atau gagal memberikan data bukan karena servernya rusak, melainkan karena alamat yang dicari client memang tidak ada di dalam sistem.
<img width="530" height="443" alt="Cuplikan layar 2026-10-07 102404" src="https://github.com/user-attachments/assets/aef97866-34f8-4f52-a39f-ef6616636b5d" />


Status Code 500 (Internal Server Error)
Arti: Terjadi kesalahan fatal di sisi server saat sedang memproses permintaan client.
Kapan Terjadi: Ketika ada bug pada kode program backend, kegagalan saat menghubungkan ke database, atau server kehabisan memori (out of memory).
Kondisi Server: Bermasalah atau mengalami crash. Pesan error ini murni kesalahan dari pihak pengembang atau pengelola server, bukan karena kesalahan ketik dari sisi pengguna.
![Uploading Cuplikan layar 2026-10-07 102404.png…]()
<img width="535" height="392" alt="Cuplikan layar 2026-10-07 102439" src="https://github.com/user-attachments/assets/c135596e-50fe-4c67-be41-c6ee0181faf5" />

