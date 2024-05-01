# Reflection

<details>
<summary>1.</summary>
   
_Unary_, _server streaming_, dan _bi-directional streaming_ _RPC_ adalah beberapa contoh metode komunikasi yang sering digunakan dalam _RPC_. Ketiganya memiliki karakteristik dan penggunaan optimal yang berbeda-beda. Pada _**Unary RPC**_, _client_ mengirimkan satu _request_ ke server dan mendapatkan satu _response_ dari server. Metode ini efektif digunakan untuk operasi yang membutuhkan _response_ cepat secara langsung. Sebagai contoh, _unary RPC_ cocok untuk pemgambilan data pengguna dan pemeriksaan status layanan. Di sisi lain, _**server streaming RPC**_ memiliki cara kerja, yaitu _client_ mengirim satu _request_ ke sever, tetapi dapat menerima banyak _response_ dalam _stream_. _Server_ terus mengirimkan data sampai semua informasi dikirim atau koneksi ditutup. Contoh kasus di mana metode ini efektif adalah pengiriman log server, _monitoring real time_ dari sensor atau data pasar, dan layanan lain yang memerlukan pengiriman data secara bertahap tetapi terus-menerus. Terakhir, _bi-directional RPC_ adalah metode yang memungkinkan _client_ untuk mengirimkan _request_ secara terus menerus kepada server. Di sisi lain, server juga dapat mengirimkan _response_ secara serangkaian dalam bentuk _stream_.Dengan demikian, metode ini memungkinkan komunikasi dua arah secara asinkronus Metode ini cocok digunakan untuk penggunaan seperti aplikasi _chat_, sistem kolaborasi _real-time_, dan bentuk layanan lainnya yane membutuhkan pertukaran data secara cepat dan terus-menerus antara server dan _client_
</details>

<details>
<summary>2.</summary>
   
Penerapan gRPC pada Rust memiliki beberapa celah yang dapat menjadi risiko. Beberapa di antaranya adalah konfigurasi TLS yang salah (dapat membuka celah untuk serangan _man in the middle_), kebocoran informasi melalui metadata, penyalahgunaan autentikasi dan otorisasi, serangan DoS (Denial of Service), pengelolaan kunci yang buruk, celah pada implementasi dependensi, dan risiko terbukanya _souce code_. Untuk meminimalkan risiko dari penggunaan gRPC, terdapat beberapa aspek sekuriti yang perlu dipehartikan (dilakukan). Beberapa di antaranya adalah sebagai berikut.
   - **Autentikasi:** Penggunaan token seperti JWT, penggunaan sertifikan TLS/SSL, dan penggunaan autentikasi mTLS
   - **Otrisasi:** Pengendalian RBAC dan penggunaan kebijakan keamanan seperti ACLs
   - **Enkripsi data:** Penggunaan enkripsi transport (TLS) dan enkripsi tingkat aplikasi
   - **Pengelolaan kunci dan sertifikat:** Rotasi kunci dan sertifikat secara regular dan penyimpanan kunci yang aman (misalnya dengan menggunakan layanan manajemen kunci atau modul keamanan perangkat keras)
</details>

<details>
   <summary>3.</summary>
   
</details> 
