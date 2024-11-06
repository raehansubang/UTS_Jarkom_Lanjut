# UTS_Jarkom_Lanjut
# Essay
Nama : Raehan Subang Rachyudiansyah
Nim : 20210801187

JAWABAN 
1.	Routing statis adalah metode routing dalam jaringan komputer di mana rute atau jalur jaringan ditentukan secara manual oleh administrator jaringan. Dalam metode ini, administrator menentukan secara spesifik setiap jalur yang harus dilalui paket data untuk mencapai tujuan tertentu.

2.	Routing dinamis adalah metode routing dalam jaringan komputer di mana rute atau jalur menuju tujuan tertentu dikelola dan diperbarui secara otomatis oleh protokol routing. Tidak seperti routing statis, yang diatur secara manual, routing dinamis menggunakan algoritma dan protokol untuk mendeteksi perubahan dalam topologi jaringan dan secara otomatis menyesuaikan rute sesuai kebutuhan.

3.	Firewall adalah sistem keamanan jaringan yang berfungsi sebagai penghalang antara jaringan internal (seperti jaringan perusahaan atau jaringan rumah) dan jaringan eksternal (seperti internet) untuk mencegah akses yang tidak diinginkan. Firewall bekerja dengan memonitor, memfilter, dan mengontrol lalu lintas data berdasarkan serangkaian aturan keamanan yang telah ditentukan. Tujuan utama dari firewall adalah melindungi jaringan dari serangan, akses yang tidak sah, dan ancaman lain yang berasal dari luar atau dari dalam jaringan itu sendiri.

4.	NAT, atau Network Address Translation, adalah teknik yang digunakan dalam jaringan komputer untuk mengubah alamat IP pada paket data yang melewati router atau perangkat NAT. NAT memungkinkan beberapa perangkat di dalam jaringan lokal (seperti jaringan rumah atau kantor) untuk menggunakan satu alamat IP publik saat mengakses internet. Teknik ini sangat bermanfaat dalam menghemat penggunaan alamat IP publik dan meningkatkan keamanan jaringan internal

# Cased
# Topologi 
![topologi](https://github.com/user-attachments/assets/38c3bf4d-4693-441c-9aa9-765c4a308ffe)

# Analisis Jaringan

1. **Topologi Jaringan**:
   - Jaringan ini menggunakan **topologi hub-and-spoke** dengan **Router R1 KJ** sebagai pusat (hub) dan **Router R2 CR** serta **Router R3 KHI** sebagai node (spoke). R1 KJ terhubung langsung ke R2 CR dan R3 KHI melalui IP publik, dengan masing-masing router dihubungkan melalui tunnel IPIP.
   - **Alamat IP Publik** digunakan di antara router untuk membuat koneksi antar kantor cabang melalui jaringan eksternal (seperti internet).

2. **Penggunaan Tunneling**:
   - **Tunnel IPIP** digunakan untuk memungkinkan komunikasi antar jaringan yang berada di lokasi fisik yang berbeda (kantor cabang yang berbeda) melalui jaringan publik. Tunnel ini mengamankan data dari satu jaringan ke jaringan lainnya, memberikan efek seolah-olah jaringan berada dalam satu lingkungan jaringan lokal.
   - Setiap router memiliki interface tunnel dengan alamat IP khusus, yang digunakan untuk melewatkan paket antar router.

3. **Subnetting dan Alokasi IP**:
   - Jaringan menggunakan subnet yang berbeda untuk setiap cabang:
     - **R1 KJ** memiliki subnet **192.168.10.0/24**.
     - **R2 CR** memiliki subnet **192.168.6.2/24**.
     - **R3 KHI** memiliki subnet **192.168.6.3/24**.
   - Alokasi IP yang jelas dan berbeda di setiap subnet membantu memisahkan dan mengidentifikasi lalu lintas antar jaringan, sehingga memudahkan administrasi jaringan dan mencegah konflik IP.

4. **Routing Statis**:
   - **Routing statis** digunakan untuk mengarahkan lalu lintas antar subnet. Setiap router dikonfigurasi dengan route statis untuk mencapai jaringan di router lainnya melalui alamat IP tunnel.
   - Penggunaan routing statis memberikan kontrol penuh atas jalur data, namun memerlukan pembaruan manual jika ada perubahan topologi.

5. **Keamanan dan Isolasi Jaringan**:
   - Dengan memanfaatkan IP publik di antara router dan tunnel, jaringan ini menjaga isolasi antara jaringan internal (di kantor cabang) dan jaringan eksternal (publik/internet). Selain itu, VLAN diterapkan pada switch di setiap lokasi untuk memisahkan jaringan lokal dari jaringan luar, memberikan tambahan keamanan di lapisan jaringan.

6. **Pengelolaan Jaringan Lokal**:
   - Setiap router memiliki switch dengan konfigurasi VLAN untuk jaringan lokal. Ini memungkinkan perangkat di dalam setiap kantor cabang untuk berkomunikasi dengan perangkat lain di jaringan yang sama tanpa terhubung langsung ke jaringan publik.

### Kesimpulan

Jaringan ini dirancang untuk menghubungkan beberapa kantor cabang melalui jaringan publik dengan keamanan dan efisiensi. Berikut adalah kesimpulan dari desain jaringan ini:

- **Keamanan Data**: Penggunaan tunnel IPIP memberikan lapisan keamanan tambahan dengan memungkinkan koneksi yang aman antar router melalui IP publik. Walaupun tidak seaman IPsec, IPIP sederhana dan cukup untuk jaringan internal kantor yang tidak membutuhkan enkripsi penuh.
  
- **Kontrol Routing**: Routing statis memberi administrator jaringan kontrol penuh atas lalu lintas antar kantor. Namun, kelemahan routing statis adalah kurang fleksibel dan memerlukan perubahan manual saat ada perubahan topologi jaringan.

- **Penggunaan IP Publik dan Swasta**: Kombinasi IP publik untuk koneksi antar kantor dan IP privat di jaringan lokal memastikan jaringan tetap terisolasi dari jaringan publik, sehingga mengurangi risiko akses tidak sah dari luar.

- **Skalabilitas Terbatas**: Karena menggunakan routing statis, jaringan ini mungkin kurang ideal untuk ekspansi besar. Jika ada rencana untuk menambahkan lebih banyak cabang, mungkin akan lebih efisien menggunakan protokol routing dinamis, seperti OSPF atau EIGRP, untuk mengotomatiskan routing.

- **Manajemen VLAN Lokal**: VLAN di setiap cabang memberikan kemampuan untuk mengelola perangkat di jaringan lokal dengan baik, menjaga keamanan dan meminimalkan lalu lintas broadcast antar perangkat.

### Saran
Jika jaringan ini perlu berkembang di masa mendatang, disarankan untuk mempertimbangkan penggunaan **protokol routing dinamis** untuk mengelola rute secara otomatis dan menggunakan **VPN IPsec** untuk menambah keamanan pada koneksi antar cabang.
