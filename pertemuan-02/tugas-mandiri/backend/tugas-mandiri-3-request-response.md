Permintaan (Request): Pesan/data yang dikirim oleh Client (seperti browser atau Postman) ke server untuk meminta sesuatu.
<img width="539" height="432" alt="Cuplikan layar 2026-10-07 121044" src="https://github.com/user-attachments/assets/72a9a9d2-2e5e-4fc7-87f7-4c759c7ea64d" />

Respons (Response): Balikan data, status, dan pesan yang dikirimkan oleh Server kembali ke client setelah memproses permintaan.
Fungsi Query Parameter: Untuk mengirim data tambahan melalui URL (biasanya untuk pencarian atau filter). Pada pengujian, parameter nama=Umar dan kelas=TI ditaruh di URL agar server tahu nilai spesifik yang diminta.
<img width="549" height="443" alt="Cuplikan layar 2026-10-07 115819" src="https://github.com/user-attachments/assets/3756853d-cf3d-4f49-8535-acf77f817a8e" />
Fungsi HTTP Header: Membawa informasi meta/tambahan tentang request atau response. Contoh header User-Agent memuat informasi jenis browser dan sistem operasi perangkat yang Anda gunakan.
Perbedaan Penempatan Data:
Query Parameter: Diletakkan di dalam URL (setelah tanda ?), dipakai pada method GET untuk data publik/pencarian.
Body Permintaan: Diletakkan tersembunyi di dalam badan paket data, dipakai pada method POST/PUT/PATCH untuk data yang besar atau rahasia (seperti password atau registrasi).
<img width="531" height="443" alt="Cuplikan layar 2026-10-07 120109" src="https://github.com/user-attachments/assets/4099ef6a-05e1-4184-9a2d-737330624f71" />
