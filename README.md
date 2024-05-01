# Reflection

<details>
<summary>1. Klik untuk melihat</summary>
   
_Unary_, _server streaming_, dan _bi-directional streaming_ _RPC_ adalah beberapa contoh metode komunikasi yang sering digunakan dalam _RPC_. Ketiganya memiliki karakteristik dan penggunaan optimal yang berbeda-beda. Pada _**Unary RPC**_, _client_ mengirimkan satu _request_ ke server dan mendapatkan satu _response_ dari server. Metode ini efektif digunakan untuk operasi yang membutuhkan _response_ cepat secara langsung. Sebagai contoh, _unary RPC_ cocok untuk pemgambilan data pengguna dan pemeriksaan status layanan. Di sisi lain, _**server streaming RPC**_ memiliki cara kerja, yaitu _client_ mengirim satu _request_ ke sever, tetapi dapat menerima banyak _response_ dalam _stream_. _Server_ terus mengirimkan data sampai semua informasi dikirim atau koneksi ditutup. Contoh kasus di mana metode ini efektif adalah pengiriman log server, _monitoring real time_ dari sensor atau data pasar, dan layanan lain yang memerlukan pengiriman data secara bertahap tetapi terus-menerus. Terakhir, _bi-directional RPC_ adalah metode yang memungkinkan _client_ untuk mengirimkan _request_ secara terus menerus kepada server. Di sisi lain, server juga dapat mengirimkan _response_ secara serangkaian dalam bentuk _stream_.Dengan demikian, metode ini memungkinkan komunikasi dua arah secara asinkronus Metode ini cocok digunakan untuk penggunaan seperti aplikasi _chat_, sistem kolaborasi _real-time_, dan bentuk layanan lainnya yane membutuhkan pertukaran data secara cepat dan terus-menerus antara server dan _client_
</details>

<details>
<summary>2. Klik untuk melihat</summary>
   
Penerapan gRPC pada Rust memiliki beberapa celah yang dapat menjadi risiko. Beberapa di antaranya adalah konfigurasi TLS yang salah (dapat membuka celah untuk serangan _man in the middle_), kebocoran informasi melalui metadata, penyalahgunaan autentikasi dan otorisasi, serangan DoS (Denial of Service), pengelolaan kunci yang buruk, celah pada implementasi dependensi, dan risiko terbukanya _souce code_. Untuk meminimalkan risiko dari penggunaan gRPC, terdapat beberapa aspek sekuriti yang perlu dipehartikan (dilakukan). Beberapa di antaranya adalah sebagai berikut.
   - **Autentikasi:** Penggunaan token seperti JWT, penggunaan sertifikan TLS/SSL, dan penggunaan autentikasi mTLS
   - **Otrisasi:** Pengendalian RBAC dan penggunaan kebijakan keamanan seperti ACLs
   - **Enkripsi data:** Penggunaan enkripsi transport (TLS) dan enkripsi tingkat aplikasi
   - **Pengelolaan kunci dan sertifikat:** Rotasi kunci dan sertifikat secara regular dan penyimpanan kunci yang aman (misalnya dengan menggunakan layanan manajemen kunci atau modul keamanan perangkat keras)
</details>

<details>
<summary>3. Klik untuk melihat</summary>
   
Terdapat beberapa hal yang mungkin menjadi tantangan dari penggunaan metode tersebut. Beberapa di antaranya adalah sebagai berikut.

   - **Sinkronisasi pesan**, perlu memastikan bahwa pesan antar pihak tiba dalam urutan yan seharusnya dan tidak ada pesan yang hilang di tengah jalan.
   - **Manajemen koneksi**, koneksi yang stabil penting untuk menjaga komunikasi antara _client_ dan server
   - **_Error handling_**, perlu ada _error handling_ yang baik untuk memulihkan koneksi dan menjaga agar data tidak hilang atau terputus
   - **_Scalability_**, program perlu memiliki kemampuan untuk menangani banyak koneksi dengan efisien
   - **_Security_**, perlu ada penerapan perlindungan keamanan
   - **_Code maintainability_**
</details>

<details>
<summary>4. Klik untuk melihat </summary>
   
Penggunaan `tokio_stream::wrappers::ReceiverStream` untuk _streaming response_ pada gRPC memiliki beberapa kelebihan. Kelebihan yang dimiliki dari penggunaannya di antaranya adalah terintegrasi dengan baik dengan ekosistem Tokio dan Memudahkan implementasi _streaming_. Di sisi lain, penggunaan tersebut juga memiliki kekurangan. Beberapa kekurangan tersebut di antaranya adalah kontrol terbatas atas Backpressure dan ketergantungan pada Tokio

</details>

<details> 
<summary>5. Klik untuk melihat</summary>

Terdapat beberapa cara yang dapat dilakukan untuk menunjang _code reuse_, modularitas, dan _maintainability_ kode Rust gRPC. Beberapa cara tersebut adalah dengan menggunakan traits, menggunakan modul, menggunakan template generik, dan mengimplementasikan middleware dan interceptors. Dengan penerapan tersebut, kode yang dihasilkan diharapkan memiliki _maintainability_ yang lebih tinggi.

</details>

<details>
<summary>6. Klik untuk melihat</summary>

Agar dapat menangani proses pembayaran dengan logika yang lebih rumit, terdapat beberapa hal yang dapat ditambakan ke `MyPaymentService`. Beberapa hal tersebut di antaranya adalah sebagai berikut.
   - Melakukan validasi menyeluruh terhadap data yang berhubungan dengan pembayaran
   - Bekerja sama dengan gateway pembayaran eksternal untuk menangani transaksi nyata
   - Pastikan sistem dapat mengatasi kesalahan melalui mekanisme _retry_ dan strategi _fallback_.
   - Lakukan perekaman log aktivitas secara detail untuk mempermudah proses audit
   - Konfirmasi hasil pembayaran harus dikirim kepada pelanggan menggunakan metode komunikasi yang efektif
   - 
</details>

<details>
<summary>7. Klik untuk melihat</summary>
   
Adopsi gRPC sebagai protokol komunikasi memiliki dampak yang besar terhadap arsitektur dan desain dari sistem distribusi. Hal ini karena gRPC menggunakan protokol HTTP/2 yang memungkinkan komunikasi yang efisien serta mendukung adanya _streaming_. Hal tersebut memungkinkan komunikasi yang cepat dan efisien. Tidak hanya itu, gRPC juga menggunakan protobuf untuk definisi _UI_. Dengan demikian, gRPC memberikan interoperabilitas yang lebih baik dengan berbagai teknologi dan platform. Secara keseluruhan hal ini mendukung sistem yang lebih modular, skalabel, dan mudah diintegrasikan dengan teknologi yang ada

</details>

<details>
<summary>8. Klik untk melihat</summary>

Penggunaan HTTP/2 sebagain _underlying protocol_ dari gRPC memiliki beberapa kelebihan jika dibandingkan dengan HTTP/1.1 atau HTTP/1.1 dengan WebSocket untuk REST APIs. Beberapa kelebih tersebut di antaranya adalah sebagai berikut.

   - **Multiplexing**, yaitu dimungkinkannya banuak permintaan dan response dikirim secara bersamaan melalui koneksi tunggal sehingga meningkatkan kinerja dan efisiensi
   - **Binary framing**, yaitu berkurangnya overhead karena format data yang kurang efisien
   - **Server push**, yaitu dimungkinkannya server mengirimkan data ke _client_ tanpa permintaan sebelumnya
     
Meskipun memiliki kelebihan dibanding protokol lainnya, metode HTTP/2 juga memiliki beberapa kekurangan. Beberapa di antaranya adalah sebagai berikut. 
   - HTTTP/2 memiliki kompleksitasi implementasi yang cenderung lebih rumit dibanding protokol lainnya
   - Belum semua platform mendukung protokol HTTP/2
   - Meskipun cenderung mencegah adanya overhead, protokol ini masih memiliki kemungkinan overhead ketika terjadi kasus tertentu seperti pada koneksi yang lambat atau dengan _payload_ kecil
</details>

<details>
<summary>9. Klik untuk melihat</summary>

Model _request-response_ REST API cenderung bersifat satu arah. Hal ini menyebabkan komunikasi bersifat kurang responsif untuk kebutuhan komunikasi yang _real time_. Di sisi lain, metode _bi-directional_ pada gRPC memungkinkan komunikasi dua arah yang lebih efektif dan responsif. Hal ini dapat diketahui karena, seperti yang disebutkan pada nomor 1, _bi-directional gRPC_ memungkinkan komunikasi berupa banyak request-response antara _client_ dan _server_. Dengan demikian, _client_ dan _server_ dapat bertukar data secara terus menerus dalam waktu instan
</details>

<details>
<summary>10. Klik untuk melihat</summary>

Terdapat beberapa implikasi dari penggunaan _schema-based approach_ pada gRPC menggunakan _protocol buffer_ dibandingkan bentuk alami _schema-less_ dari JSON di REST API. Implikasi tersebut dapat berupa keuntungan maupun kekurangan dari penggunannya. Beberapa keuntungannya, antara lain adalah validasi data yang lebih ketat, konsistensi struktur, dan performa yang lebih baik. Meskipun demikian, masih terdapat kekurangan seperti keterbatasan fleksibilitas, dan keperluan manajemen skema yang lebih teliti.

</details>
