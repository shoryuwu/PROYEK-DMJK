# Perencanaan Proyek PT. Nusantara Network - Pekan 10

## Anggota Kelompok dan Peran
- Firni Fauziah Ramadhini (10231038) - Network Architect
- Alfiani Dwiyuniarti (10231010) - Network Services Specialist
- Rayhan Iqbal (10231080) - Network Engineer
- Muhammad Alif Setiawan (10231056) - Security & Documentation Specialist

## Daftar Isi
1. Pendahuluan
   - 1.1. Latar Belakang
   - 1.2. Tujuan Proyek
   - 1.3. Ruang Lingkup Proyek
2. Diagram topologi
3. Tabel pengalamatan IP
4. Daftar perangkat yang dibutuhkan
5. Rencana penerapan VLAN (VLAN ID, nama, tujuan).
6. Kendala dan Solusi
7. Kesimpulan
8. Lampiran

## 1. Pendahuluan
### 1.1 Latar Belakang
Dalam era digital saat ini, infrastruktur jaringan yang andal, aman, dan efisien menjadi tulang punggung operasional bagi perusahaan teknologi informasi. PT. Nusantara Network sebagai perusahaan yang bergerak di bidang teknologi informasi memiliki struktur organisasi yang terdistribusi dengan 4 departemen utama yang tersebar di 2 lokasi fisik berbeda. Kompleksitas ini menciptakan tantangan tersendiri dalam hal pengelolaan jaringan.

Kondisi jaringan yang ada saat ini belum optimal karena belum menerapkan segmentasi yang tepat antar departemen, yang dapat menyebabkan risiko keamanan dan inefisiensi dalam pengelolaan traffic data. Selain itu, konektivitas antar gedung masih menggunakan solusi ad-hoc yang tidak terstandarisasi dan sulit dikelola. Layanan-layanan penting seperti DHCP, DNS, dan akses internet juga memerlukan implementasi yang terstruktur.

Kebutuhan akan keamanan data semakin meningkat, terutama dengan adanya departemen Keuangan dan SDM yang menangani informasi sensitif. Tanpa adanya kebijakan akses yang jelas antar departemen, risiko kebocoran data menjadi perhatian serius. Selain itu, perusahaan juga membutuhkan sistem monitoring dan manajemen jaringan terpusat untuk memudahkan pengelolaan infrastruktur yang semakin kompleks.

Oleh karena itu, dibutuhkan perancangan dan implementasi infrastruktur jaringan yang komprehensif untuk mengatasi tantangan tersebut dan mendukung pertumbuhan bisnis PT. Nusantara Network di masa depan.

### 1.2 Tujuan
Proyek perancangan dan implementasi jaringan PT. Nusantara Network memiliki tujuan sebagai berikut:

- Merancang dan mengimplementasikan infrastruktur jaringan yang aman, efisien, dan mudah dikelola untuk mendukung operasional perusahaan.
- Membangun segmentasi jaringan melalui implementasi VLAN untuk setiap departemen guna meningkatkan keamanan dan manajemen traffic data.
- Mengimplementasikan konektivitas antar gedung yang andal melalui teknologi WAN dan routing dinamis (OSPF).
- Menyediakan layanan jaringan esensial seperti DHCP untuk alokasi IP otomatis, DNS untuk resolusi nama, dan NAT untuk akses internet.
- Menerapkan kebijakan keamanan melalui Access Control List (ACL) untuk membatasi akses antar departemen sesuai dengan kebutuhan operasional dan keamanan.
- Membangun sistem monitoring dan manajemen jaringan terpusat untuk memudahkan pengelolaan dan pemeliharaan infrastruktur.
- Menyediakan dokumentasi teknis yang komprehensif untuk mendukung operasional dan pengembangan jaringan di masa depan.

### 1.3 Ruang Lingkup
Ruang lingkup proyek perancangan dan implementasi jaringan PT. Nusantara Network mencakup:

- **Perancangan Topologi Jaringan**:
  - Desain topologi fisik dan logis untuk Kantor Pusat (Gedung A) dan Kantor Cabang (Gedung B)
  - Penentuan spesifikasi dan penempatan perangkat jaringan (router, switch, dan server)

- **Skema Pengalamatan IP dan Subnetting**:
  - Perencanaan skema alamat IP untuk seluruh departemen dan server
  - Implementasi teknik subnetting untuk alokasi IP yang efisien

- **Implementasi VLAN dan Segmentasi Jaringan**:
  - Konfigurasi VLAN terpisah untuk setiap departemen (IT, Keuangan, SDM, Marketing, dan Operasional)
  - Implementasi VLAN trunking untuk efisiensi koneksi antar switch
  - Konfigurasi routing antar-VLAN

- **Routing dan Konektivitas WAN**:
  - Implementasi routing statis untuk koneksi internal di setiap gedung
  - Konfigurasi routing dinamis (OSPF) untuk manajemen rute antar gedung
  - Implementasi teknologi WAN untuk koneksi antar gedung dengan bandwidth terbatas

- **Layanan Jaringan**:
  - Konfigurasi server DHCP untuk alokasi IP otomatis di setiap departemen
  - Implementasi layanan DNS untuk resolusi nama internal dan eksternal
  - Konfigurasi NAT untuk akses internet melalui ISP

- **Implementasi Keamanan Jaringan**:
  - Perancangan dan implementasi Access Control List (ACL) untuk membatasi akses antar departemen
  - Penerapan kebijakan keamanan sesuai dengan kebutuhan bisnis

- **Pengujian dan Validasi**:
  - Pengujian konektivitas antar departemen dan antar gedung
  - Validasi implementasi kebijakan keamanan
  - Pengujian layanan jaringan (DHCP, DNS, NAT)

- **Dokumentasi**:
  - Dokumentasi desain jaringan
  - Dokumentasi konfigurasi perangkat
  - Pedoman operasional dan troubleshooting 

## 2. Diagram topologi
![Screenshot](topologidmjk.png)

###  Gedung A (Kantor Pusat)

###  Router Pusat  
Router ini berfungsi sebagai pusat konektivitas jaringan internal Gedung A ke jaringan eksternal melalui router ISP. Selain itu, router pusat juga mengatur distribusi data antar VLAN dengan menerapkan protokol **OSPF** untuk routing dinamis, **NAT** untuk koneksi ke internet, dan **ACL** untuk pembatasan akses antar departemen.

###  Main Switch Pusat  
Main switch ini merupakan tulang punggung jaringan di Gedung A yang menghubungkan semua switch departemen serta switch server. Perangkat ini menjadi pusat penghubung antar VLAN seperti VLAN 10 (IT), VLAN 20 (Keuangan), VLAN 30 (SDM), dan VLAN 40 (Server).

###  Lantai 1 – Ruangan Operasional

###  VLAN 10 – Departemen IT  
- **Jumlah PC**: 40  
- **Switch akses**: 2 switch lalu terhubung ke Switch IT  
- **Terhubung ke**: Main switch (Gedung A)  
- **Pembagian PC per switch**:  
  `40 PC / 2 switch = 20 PC per switch`

###  VLAN 20 – Departemen Keuangan  
- **Jumlah PC**: 25  
- **Switch akses**: 2 switch lalu terhubung ke Switch Keuangan  
- **Terhubung ke**: Main switch (Gedung A)  
- **Pembagian PC per switch**:  
  `25 PC / 2 switch = 13 PC & 12 PC`

###  VLAN 30 – Departemen SDM  
- **Jumlah PC**: 20  
- **Switch akses**: 1 switch lalu terhubung ke Switch SDM  
- **Terhubung ke**: Main switch (Gedung A)  
- **Pembagian PC per switch**:  
  Langsung ke 1 switch (tanpa pembagian)

### Lantai 2 – Server Room

###  VLAN 40 – Server  
- **Jumlah server**: 10  
- **Switch akses**: 1 switch lalu terhubung ke Switch Server  
- **Terhubung ke**: Main switch (Gedung A)  
- **Pembagian server per switch**:  
  Langsung ke 1 switch (tanpa pembagian)

###  Server 1–10 (VLAN 40)
Menyediakan berbagai layanan penting seperti:  
- **Server 1 (DHCP + DNS)**: Memberikan IP ke seluruh VLAN (via DHCP Relay) dan menangani DNS.  
- **Server Web, Email, FTP, dan Database**: Mendukung aplikasi internal dan komunikasi.  
- **AAA Server**: Menangani autentikasi, otorisasi, dan pencatatan aktivitas jaringan.  
- **Monitoring Server**: Memantau kondisi dan performa jaringan (PRTG, Syslog).  
- **NTP & Backup Server**: Sinkronisasi waktu dan cadangan data.



###  Gedung B (Kantor Cabang)

###  Router Cabang  
Router ini menghubungkan jaringan lokal Gedung B ke kantor pusat melalui router ISP. Seperti di pusat, router ini juga menggunakan **OSPF** untuk komunikasi antar gedung yang efisien.

###  Main Switch Cabang  
Switch utama yang mendistribusikan koneksi ke seluruh perangkat dan switch departemen di Gedung B.

###  VLAN 50 – Departemen Marketing  
- **Jumlah PC**: 30  
- **Switch akses**: 2 switch lalu terhubung ke Switch Marketing  
- **Terhubung ke**: Main switch (Gedung B)  
- **Pembagian PC per switch**:  
  `30 PC / 2 switch = 15 PC per switch`

###  VLAN 60 – Departemen Operasional  
- **Jumlah PC**: 35  
- **Switch akses**: 2 switch lalu terhubung ke Switch Operasional  
- **Terhubung ke**: Main switch (Gedung B)  
- **Pembagian PC per switch**:  
  `35 PC / 2 switch = 18 PC & 17 PC`



###  Koneksi Eksternal & Antar Gedung

- **Internet Cloud**: Mewakili koneksi ke internet global.  
- **Router ISP/Internet**: Jembatan antara jaringan internal dan dunia luar serta menjadi hubungan koneksi internet.  
- **Router Pusat & Cabang**: Terhubung ke router ISP, menjadi titik komunikasi antar gedung.



###  Keamanan dan Pengaturan Akses (ACL)

- **VLAN 10 (IT)**: Akses penuh ke seluruh sistem dan server.  
- **VLAN 20 (Keuangan)** & **VLAN 30 (SDM)**: Akses internal saja, tanpa akses ke server.  
- **VLAN 50 (Marketing)**: Tidak diizinkan mengakses VLAN Server.  
- **VLAN 60 (Operasional)**: Hanya diizinkan akses ke DNS Server dan internet.  
- Semua pengaturan dikendalikan oleh **ACL pada Router Pusat**.



###  Protokol dan Layanan Jaringan

- **Routing Dinamis OSPF**: Menjamin konektivitas antar router pusat dan cabang.  
- **NAT**: Dijalankan di Router Pusat untuk akses internet.  
- **Monitoring Server**: Menjaga performa jaringan tetap optimal.  
- **Layanan Server Lain**: HTTP/HTTPS, SMTP/POP3, FTP, Database, NTP, dan Backup.



## 3. Tabel pengalamatan IP

| VLAN ID | Nama VLAN | Subnet | Gateway | Range IP | Jumlah Host |
|---------|-----------|--------|---------|----------|-------------|
| 10 | IT | 192.168.10.0/24 | 192.168.10.1 | 192.168.10.2 - 192.168.10.254 | 253 |
| 20 | Keuangan | 192.168.20.0/24 | 192.168.20.1 | 192.168.20.2 - 192.168.20.254 | 253 |
| 30 | SDM | 192.168.30.0/24 | 192.168.30.1 | 192.168.30.2 - 192.168.30.254 | 253 |
| 40 | Server | 192.168.40.0/24 | 192.168.40.1 | 192.168.40.2 - 192.168.40.254 | 253 |
| 50 | Marketing | 192.168.50.0/24 | 192.168.50.1 | 192.168.50.2 - 192.168.50.254 | 253 |
| 60 | Operasional | 192.168.60.0/24 | 192.168.60.1 | 192.168.60.2 - 192.168.60.254 | 253 |
| Mgmt | Monitoring | 192.168.99.0/28 | 192.168.99.1 | 192.168.99.2 - 192.168.99.14 | 13 |
| ISP | Internet | 10.10.10.0/30 | 10.10.10.1 | 10.10.10.2 - 10.10.10.3 | 2 |
| WAN | Antarkantor | 172.16.1.0/30 | 172.16.1.1 | 172.16.1.2 - 172.16.1.3 | 2 |



## 4. Daftar perangkat yang dibutuhkan
| Perangkat        | Jumlah | Lokasi              | Fungsi                                      |
|------------------|--------|----------------------|---------------------------------------------|
| Router           | 2      | Pusat & Cabang       | Routing, NAT, ACL, OSPF                     |
| Router ISP/Internet          |   2    | luar/Koneksi Eksternal       | Penghubung ke router-router kantor melalui koneksi serta Penguhubung Koneksi Internet              |
| WAN          | 1      | luar/Koneksi Eksternal       | Diwakili oleh cloud "Internet"                   |
| Main Switch      | 2      | Gedung A & B         | Penghubung antar VLAN                       |
| Switch Akses     | 14     | Gedung A & B         | Menghubungkan PC/server ke jaringan serta Main switch         |
| Server           | 10     | Server Room Gedung A | Layanan DHCP, DNS, Web, Email, Backup, dll |

## 5. Rencana penerapan VLAN (VLAN ID, nama, tujuan).
| VLAN ID | Nama VLAN   | Tujuan                          | Keterangan                                                                 |
|---------|-------------|---------------------------------|----------------------------------------------------------------------------|
| 10      | IT          | Jaringan Administratif TI       | Akses penuh ke semua perangkat jaringan dan server                        |
| 20      | Keuangan    | Keamanan Transaksi Finansial    | Isolasi data keuangan dengan ACL ketat Pusat                                     |
| 30      | SDM          | Manajemen Data Karyawan         | Terpisah untuk proteksi data personal Pusat                                     |
| 40      | Server      | Infrastruktur Server Internal   |  VLAN khusus untuk semua server dengan policy keamanan tinggi              |
| 50      | Marketing   | Aktivitas Digital Marketing     | Prioritas bandwidth untuk kebutuhan kreatif                             |
| 60      | Operasional | Perangkat Operasional Harian    | Termasuk printer dan IoT device dengan akses terbatas                     |
| ISP     | Internet      | Penyedia Jaringan                    | Koneksi eksternal ke penyedia layanan internet                            |
| WAN     | Antarkantor        | Koneksi Internet                      | Interkoneksi dedicated antara gedung pusat dan cabang      
## Kendala dan Solusi
## Kesimpulan
## Lampiran
https://github.com/shoryuwu/PROYEK-DMJK/tree/main