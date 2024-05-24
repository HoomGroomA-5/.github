## HoomGroom Application
HoomGroom adalah platform e-commerce yang memampukan pengguna untuk mencari dan membeli peralatan rumah dan perabotan yang sesuai dengan kebutuhan mereka.

## Kelompok A-5 👨‍💻
> [Virgillia Yeala Prabowo](https://github.com/VirgilliaYeala) `(2206829856)` <br>
> [Emmanuel Patrick](https://github.com/g0lgi) `(2206081420)` <br>
> [Muhamad Hanif Nurrifky Wicaksono](https://github.com/HanifRifky) `(2206818846)` <br>
> [Lidwina Eurora Firsta Nobella](https://github.com/divieurora) `(2206083615)` <br>
> [Shirin Zarqaa Rabbaanii Arham](https://github.com/shirinzarqaa) `(2206081963)` <br>

## Technology Stack
![Google Cloud Platform](https://img.shields.io/badge/Google_Cloud_Platform-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)

## Our Project Sofware Architecture
### Context Diagram
![image](https://github.com/HoomGroomA-5/.github/assets/124979875/59b30caa-d69d-451a-b045-5776b0340618)
- Admin Hoomgroom pertama kali mengirimkan kredensial ke Spring Boot Starter Security untuk autentikasi. Jika autentikasi berhasil, admin dapat melakukan tugas manajemen produk dan transaksi di Furniture Product System.\
- User Hoomgroom berinteraksi dengan Furniture Product System untuk melihat produk, melakukan pembayaran, dan transaksi. Sistem ini memastikan autentikasi pengguna melalui Spring Boot Starter Security.
- Furniture Product System mengambil data yang diperlukan dari Mainframe Furniture System untuk menampilkan informasi produk, akun, dan transaksi kepada pengguna dan admin.

### Container Diagram
![image](https://github.com/HoomGroomA-5/.github/assets/124979875/531c6855-2221-4a91-9a1c-b25da5ba584e)
- Admin Hoomgroom dan User Hoomgroom mengakses Web Application melalui browser. Admin mengirimkan autentikasi ke Spring Boot Starter Security, dan setelah berhasil, mengelola produk dan transaksi.
- Web Application menyediakan konten ke Single-Page Application yang diakses oleh pengguna.
- Single-Page Application menggunakan API yang disediakan oleh API Application untuk melakukan operasi yang dibutuhkan pengguna, seperti melihat produk dan melakukan transaksi.
- API Application berkomunikasi dengan Database dan Mainframe Furniture System untuk mengelola data aplikasi dan informasi produk.

### Deployment Diagram
![image](https://github.com/HoomGroomA-5/.github/assets/124979875/f2fd0656-95e2-4364-a16c-475ad281ac0f)
- Pengguna menggunakan SPA melalui browser mereka, yang menyediakan antarmuka pengguna untuk mengakses dan menggunakan fitur-fitur aplikasi furniture.
- SPA diunduh dan ditampilkan di browser pengguna oleh Aplikasi Web yang ditempatkan di Vercel.
- SPA mengirimkan permintaan API ke Aplikasi API HoomGroom. Aplikasi API ini bertindak sebagai pusat pengatur yang memproses setiap permintaan dan mendistribusikannya ke layanan microservices yang tepat untuk penanganan lebih lanjut.
- Layanan Otentikasi: Melakukan verifikasi pengguna dan mengelola proses login, registrasi, dan logout.
- Layanan Komersial: Mengelola daftar produk furniture, termasuk informasi detail dan ketersediaan produk, serta menangani proses pengiriman.
- Layanan Pembayaran: Mengelola proses pembayaran, isi ulang, dan menyediakan riwayat transaksi pengguna.
- Setiap layanan microservice melakukan operasi baca dan tulis pada database PostgreSQL yang sesuai yang di-hosting di Supabase, memastikan bahwa data pengguna, produk, dan transaksi disimpan dengan aman dan dapat diakses dengan efisien.

# Risk Storming 
## Identifikasi Risiko:
Kami mengumpulkan dan mencatat berbagai risiko yang mungkin terjadi terkait dengan arsitektur, desain, implementasi, dan operasional dari sistem aplikasi yang sedang kami kerjakan. Berikut ini adalah hasil diskusi kami : 
### 1. Kompleksitas Operasional
Risiko: Mengelola dan mengkoordinasikan banyak microservices bisa menjadi sangat kompleks, terutama dengan adanya dependensi antar layanan.

###  2. Overhead Jaringan dan Latency
Risiko: Interaksi antar microservices melalui jaringan dapat menyebabkan overhead dan meningkatkan latency.

### 3.Skalabilitas Database
Risiko: Penggunaan PostgreSQL mungkin menghadapi kendala skalabilitas saat beban tinggi atau volume data besar.

### 4.  Keamanan Data dan Privasi
Risiko: Data pelanggan dan transaksi yang sensitif bisa rentan terhadap kebocoran atau serangan.

### 5. Ketergantungan pada Layanan Pihak Ketiga 
Risiko: Ketergantungan pada layanan cloud GCP dan Vercel bisa menjadi masalah jika terjadi downtime atau perubahan layanan yang tidak terduga.

## Kategorisasi Risiko:
Berikut adalah risiko yang telah diidentifikasi oleh kelompok berdasarkan identifikasi risiko yang sebelumnya sudah kami diskusikan : 
### 1. Kategori Teknis
- Kompleksitas koordinasi microservice yang tinggi
- Overhead jaringan dan peningkatan latency saat interaksi mantar microservice dilakukan melalui jaringan
- Penggunaan PostgreSQL yang dapat menghadapi kendala skalabilitas

### 2. Kategori keamanan
- Data pelanggan dan transaksi yang sensitif bisa rentan terhadap kebocoran atau serangan.

### 3. Kategori Operasional
- Ketergantungan pada layanan cloud GCP dan Vercel bisa menjadi masalah jika terjadi downtime atau perubahan layanan yang tidak terduga.
  
## Penilaian Risiko:
Setiap risiko dinilai berdasarkan dua parameter utama: dampak (seberapa besar efek dari risiko tersebut) dan kemungkinan (seberapa besar peluang risiko tersebut terjadi).Penilaian ini bisa dilakukan secara kualitatif (misalnya, rendah, sedang, tinggi) atau kuantitatif (misalnya, skala 1-10).

| Risiko                                     | Dampak | Kemungkinan | Penilaian Total (dari skala 1-10) |
|--------------------------------------------|--------|-------------|-----------------------------------|
| Kompleksitas Operasional                   | Tinggi | Sedang      | 8                                 |
| Overhead Jaringan dan Latency              | Sedang | Tinggi      | 7                                 |
| Skalabilitas Database                      | Tinggi | Sedang      | 7                                 |
| Keamanan Data dan Privasi                  | Tinggi | Sedang      | 8                                 |
| Ketergantungan pada layanan pihak ketiga   | Tinggi | Sedang      | 7                                 |




## Mitigasi Risiko:
Berikut adalah mitigasi dari resiko yang sudah dikategorisasikan sebelumnya:
### 1. Kategori teknis
**Kompleksitas Microservice**
- Implementasi orkestrasi layanan seperti Kubernetes.
- Penggunaan tools seperti Istio untuk manajemen microservices.
- Dokumentasi dan pemantauan yang baik.
- 
**Overhead dan Latency Jaringan**
- Optimasi desain API dan pengurangan jumlah panggilan jaringan.
- Implementasi caching dan mekanisme pemulihan otomatis.
- Penggunaan alat pemantauan performa jaringan.
  
**Kendala Skalabilitas PostgreSQL**
- Implementasi partisi data dan replikasi.
- Penggunaan arsitektur microservices yang mendukung skala horizontal.
- Pemantauan dan tuning performa database.
  
### 2. Kategori keamanan
- Kebocoran atau Serangan Data Sensitif.
- Implementasi enkripsi data di rest dan in transit.
- Pengetatan kontrol akses dan autentikasi.
- Penetration testing dan audit keamanan secara berkala.
  
### 3. Kategori Operasional
- Ketergantungan pada Layanan Cloud Membuat rencana kontingensi dan backup.
- Memanfaatkan multi-cloud atau hybrid cloud untuk mengurangi risiko ketergantungan.
- Pemantauan dan pengujian secara berkala terhadap kebijakan pemulihan bencana.

## Dokumentasi dan Tindak Lanjut:
Berdasarkan resiko yang sudah diidentifikasi di atas, berikut adalah tindak lanjut atau solusi dari resiko tersebut : 
### 1. Resiko kompleksitas operasional
Untuk mengatasi resiko kompleksitas operasional karena banyaknya microservice yang dibentuk, kami akan menggunakan alat orkestrasi seperti Kubernetes untuk manajemen container dan deploy otomatis, serta implementasi CI/CD pipelines untuk mempermudah deploy dan update layanan.

### 2. Resiko overhead jaringan dan meningkatnya latency program
Untuk mengatasi resiko overhead dan meningkatnya latency program yang telah disusun, kami akan menggunakan lightweight communication protocols seperti gRPC, dan memastikan layanan-layanan tersebut berada dalam satu network segment untuk mengurangi latency.

### 3. Resiko kendala skalabilitas PostgreSQL
Mengimplementasikan teknik sharding dan partitioning pada database, serta menggunakan read replicas untuk meningkatkan performa baca.

### 4. Resiko kebocoran data pelanggan
Menerapkan enkripsi data baik saat transit maupun saat tersimpan, menggunakan OAuth2 dan JWT untuk otentikasi, serta melakukan audit keamanan secara berkala.

### 5. Resiko ketergantungan cloud GCP
Memiliki strategi fallback dan disaster recovery, serta melakukan backup secara rutin dan monitoring kesehatan layanan pihak ketiga.

# Alasan menggunakan teknik risk storming:
Risk Storming merupakan sebuah teknik yang dilakukan secara kolaboratif di lingkungan perancangan software architecture. Teknik ini melalui beberapa tahapan yaitu identifikasi resiko, kategorisasi resiko, penilaian, mitigasi, dan tindak lanjut resiko. Teknik ini melibatkan berbagai aspek tim yang beragam agar bisa melihat lingkup resiko secara luas.
