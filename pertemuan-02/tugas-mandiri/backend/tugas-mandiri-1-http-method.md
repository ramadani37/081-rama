<img width="544" height="413" alt="Cuplikan layar 2026-10-07 094045" src="https://github.com/user-attachments/assets/a6cd0b58-6662-4dfb-a8c6-75df60692b18" />
Laporan Tugas Mandiri 1 — Mengenal HTTP Method dan EndpointPada tugas ini, dilakukan pengujian terhadap 5 endpoint utama dari layanan publik HTTPBin ([https://httpbin.org](https://httpbin.org)) menggunakan aplikasi Postman untuk memahami hubungan antara metode HTTP, parameter, data kiriman (payload), serta respons yang dikembalikan oleh server.Rangkuman Hasil PengujianNoMethodEndpointData yang dikirimStatusHasil1GET/getQuery parameter (?nama=Umar&kelas=TI)200 OKMengembalikan JSON yang berisi args (parameter URL), headers, dan url yang diterima server.2POST/postJSON Body ({"pesan": "Halo HTTPBin"})200 OKMengembalikan JSON yang merefleksikan kembali data body, json, dan headers yang dikirimkan.3PUT/putJSON Body pembaruan ({"status": "update_full"})200 OKMengembalikan JSON konfirmasi penerimaan data PUT untuk pembaruan menyeluruh.4PATCH/patchJSON Body pembaruan sebagian ({"status": "update_part"})200 OKMengembalikan JSON konfirmasi penerimaan data PATCH untuk pembaruan parsial.5DELETE/delete- (Tanpa body khusus)200 OKMengembalikan JSON konfirmasi bahwa permintaan DELETE telah berhasil diproses oleh server.Detail Informasi Pengujian1. GET MethodHTTP Method: GETURL Lengkap: [https://httpbin.org/get?nama=Umar&kelas=TI](https://httpbin.org/get?nama=Umar&kelas=TI)Tujuan Endpoint: Menguji permintaan pengambilan data (retrieval) dari server menggunakan parameter query di URL.Data yang Dikirim: Query parameter (nama=Umar & kelas=TI).Kode Status HTTP: 200 OKIsi Respons (Response Body):JSON{
  "args": {
    "kelas": "TI",
    "nama": "Umar"
  },
  "headers": {
    "Accept": "*/*",
    "Host": "httpbin.org",
    "User-Agent": "PostmanRuntime/7.x.x"
  },
  "url": "https://httpbin.org/get?nama=Umar&kelas=TI"
}
Penjelasan Respons Server: Server HTTPBin membaca parameter yang diselipkan pada URL (args) dan menampilkan kembali informasi tersebut beserta header pengirim (User-Agent dan Host) untuk membuktikan data apa saja yang diterima server.2. POST MethodHTTP Method: POSTURL Lengkap: [https://httpbin.org/post](https://httpbin.org/post)Tujuan Endpoint: Menguji pengiriman data baru ke server melalui badan permintaan (request body).Data yang Dikirim: JSON Body ({"pesan": "Halo HTTPBin"})Kode Status HTTP: 200 OKIsi Respons (Response Body):JSON{


<img width="528" height="430" alt="Cuplikan layar 2026-10-07 095100" src="https://github.com/user-attachments/assets/428f7f18-fce2-4f55-95e7-b469e5a3531f" />

  "args": {},
  "data": "{\"pesan\": \"Halo HTTPBin\"}",
  "files": {},
  "form": {},
  "json": {
    "pesan": "Halo HTTPBin"
  },
  "headers": {
    "Content-Type": "application/json",
    "Host": "httpbin.org"
  },
  "url": "https://httpbin.org/post"
}
Penjelasan Respons Server: Server mendeteksi data berformat JSON di dalam body, lalu menyalinnya ke dalam field "json" dan "data" sebagai bukti bahwa server berhasil membaca payload yang dikirimkan.3. PUT MethodHTTP Method: PUTURL Lengkap: [https://httpbin.org/put](https://httpbin.org/put)Tujuan Endpoint: Menguji pengiriman data untuk pembaruan menyeluruh (replacement/full update) pada sumber daya server.Data yang Dikirim: JSON Body ({"status": "update_full"})Kode Status HTTP: 200 OKIsi Respons (Response Body):JSON{
  "args": {},
  "data": "{\"status\": \"update_full\"}",
  "files": {},
  "form": {},
  "json": {
    "status": "update_full"
  },
  "headers": {
    "Content-Type": "application/json",
    "Host": "httpbin.org"
  },
  "url": "https://httpbin.org/put"
}
Penjelasan Respons Server: Serupa dengan POST, HTTPBin menampilkan kembali isi body yang dikirimkan melalui method PUT di dalam field "json", menunjukkan bahwa data pengganti telah diterima oleh server.4. PATCH MethodHTTP Method: PATCHURL Lengkap: [https://httpbin.org/patch](https://httpbin.org/patch)Tujuan Endpoint: Menguji pengiriman data untuk pembaruan sebagian (partial update) pada sumber daya server.Data yang Dikirim: JSON Body ({"status": "update_part"})Kode Status HTTP: 200 OKIsi Respons (Response Body):JSON{
  "args": {},
  "data": "{\"status\": \"update_part\"}",
  "files": {},
  "form": {},
  "json": {
    "status": "update_part"
  },
  "headers": {
    "Content-Type": "application/json",
    "Host": "httpbin.org"
  },
  "url": "https://httpbin.org/patch"
}
Penjelasan Respons Server: Server menerima permintaan modifikasi parsial dan merefleksikan data JSON tersebut kembali ke client guna memvalidasi data yang masuk.5. DELETE MethodHTTP Method: DELETEURL Lengkap: [https://httpbin.org/delete](https://httpbin.org/delete)Tujuan Endpoint: Menguji permintaan penghapusan sumber daya (resource deletion) pada server.Data yang Dikirim: Tanpa data khusus (no body).Kode Status HTTP: 200 OKIsi Respons (Response Body):JSON{
  "args": {},
  "data": "",
  "files": {},
  "form": {},
  "json": null,
  "headers": {
    "Host": "httpbin.org",
    "User-Agent": "PostmanRuntime/7.x.x"
  },
  "url": "https://httpbin.org/delete"
}
Penjelasan Respons Server: Server memproses aksi penghapusan dan mengembalikan respons konfirmasi dengan field data yang kosong (data: "", json: null) karena method DELETE umumnya tidak memerlukan pengiriman body data.

<img width="528" height="430" alt="Cuplikan layar 2026-10-07 095100" src="https://github.com/user-attachments/assets/a87c82ee-2019-4f3b-851d-1c0514b9eaf5" />

<img width="541" height="444" alt="Cuplikan layar 2026-10-07 095208" src="https://github.com/user-attachments/assets/b2f181dc-ab7e-4b5b-a786-53feab5f4127" />

<img width="548" height="434" alt="Cuplikan layar 2026-10-07 095326" src="https://github.com/user-attachments/assets/dcd4cb66-a492-48b0-b855-ff6e94b8c605" />

<img width="539" height="447" alt="Cuplikan layar 2026-10-07 093835" src="https://github.com/user-attachments/assets/257063ad-8b7f-4eec-b37c-069e1dc19465" />

<img width="544" height="413" alt="Cuplikan layar 2026-10-07 094045" src="https://github.com/user-attachments/assets/0c4b6608-616b-4d10-8560-059ea1802611" />

