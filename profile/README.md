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



