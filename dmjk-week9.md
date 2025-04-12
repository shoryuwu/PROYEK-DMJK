# Perencanaan Proyek PT. Nusantara Network - Pekan 9

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
2. Pembagian Kelompok dan Peran
3. Analisis Kebutuhan Jaringan PT. Nusantara Network
   - 3.1. Analisis Infrastruktur
   - 3.2. Kebutuhan Segmentasi Jaringan
   - 3.3. Kebutuhan Konektivitas
   - 3.4. Kebutuhan Layanan Jaringan
   - 3.5. Kebutuhan Keamanan Jaringan
   - 3.6. Kebutuhan Monitoring dan Manajemen
   - 3.7. Kebutuhan Skalabilitas dan Pertumbuhan
4. Timeline Rencana Kerja Proyek (Pekan 9-15)
5. Sketsa Awal Desain Jaringan
   - 5.1. Pendekatan Desain
   - 5.2. Deskripsi Tekstual Sketsa Awal
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

## 2. Pembagian Kelompok dan Peran
- Firni Fauziah Ramadhini (10231038) - Network Architect
  - Bertanggung jawab untuk merancang topologi jaringan secara keseluruhan
  - Menentukan arsitektur jaringan yang optimal dengan mempertimbangkan kebutuhan bisnis
  - Membuat skema pengalamatan IP dan subnetting
  - Memastikan desain jaringan memenuhi persyaratan performa, skalabilitas, dan ketersediaan

- Alfiani Dwiyuniarti (10231010) - Network Services Specialist
  - Merancang dan mengimplementasikan layanan jaringan (DHCP, DNS, NAT)
  - Mengoptimalkan kinerja layanan jaringan
  - Mengintegrasikan layanan jaringan dengan infrastruktur yang ada
  - Memastikan konfigurasi layanan sesuai dengan kebutuhan masing-masing departemen

- Rayhan Iqbal (10231080) - Network Engineer
  - Bertanggung jawab untuk konfigurasi perangkat jaringan (router, switch)
  - Mengimplementasikan VLAN dan segmentasi jaringan
  - Menerapkan protokol routing (OSPF) untuk konektivitas antar gedung
  - Melakukan troubleshooting masalah jaringan

- Muhammad Alif Setiawan (10231056) - Security & Documentation Specialist
  - Merancang dan mengimplementasikan kebijakan keamanan jaringan (ACL)
  - Mengidentifikasi dan mitigasi risiko keamanan di infrastruktur
  - Membuat dokumentasi teknis yang komprehensif (diagram, konfigurasi perangkat, dll)
  - Menyusun pedoman operasional dan prosedur troubleshooting

## 3. Analisis Kebutuhan Jaringan PT. Nusantara Network
### 3.1 Analisis Infrastruktur
PT. Nusantara Network merupakan perusahaan teknologi informasi dengan struktur organisasi yang terdistribusi di 2 lokasi fisik berbeda (Gedung A dan Gedung B) dengan total 4 departemen utama. Berikut adalah kondisi infrastruktur saat ini:

Kantor Pusat (Gedung A):
- Departemen IT (40 komputer)
- Departemen Keuangan (25 komputer)
- Departemen SDM (20 komputer)
- Server Farm (10 server untuk berbagai layanan)

Kantor Cabang (Gedung B):
- Departemen Marketing (30 komputer)
- Departemen Operasional (35 komputer)

Belum ada segmentasi jaringan yang tepat antar departemen, konektivitas antar gedung masih menggunakan solusi ad-hoc yang tidak terstandarisasi, dan belum ada penerapan kebijakan keamanan yang terstruktur untuk membatasi akses antar departemen.

### 3.2 Kebutuhan Segmentasi Jaringan
Berdasarkan struktur organisasi dan kebutuhan operasional, PT. Nusantara Network memerlukan segmentasi jaringan sebagai berikut:
  - Segmentasi berbasis VLAN untuk setiap departemen:
    - VLAN Departemen IT
    - VLAN Departemen Keuangan
    - VLAN Departemen SDM
    - VLAN Departemen Marketing
    - VLAN Departemen Operasional
    - VLAN Server Farm
    - VLAN Manajemen

Alasan Implementasi VLAN:
- Meningkatkan keamanan dengan membatasi traffic antar departemen
- Mempermudah manajemen jaringan dan pengalokasian alamat IP
- Mengoptimalkan performa jaringan dengan mengurangi domain broadcast
- Memberikan fleksibilitas dalam pengelolaan jaringan tanpa perubahan fisik

### 3.3 Kebutuhan Konektivitas
Konektivitas LAN:
- Switching infrastructure yang mendukung VLAN dan trunking
- Implementasi routing antar-VLAN untuk memungkinkan komunikasi antar departemen
- Koneksi redundan untuk perangkat kritikal pada server farm

Konektivitas WAN:
- Koneksi WAN yang andal antara Gedung A dan Gedung B dengan bandwidth yang terukur
- Implementasi routing dinamis (OSPF) untuk manajemen rute antar gedung
- Koneksi ISP untuk akses internet

Konektivitas Internet:
- Layanan internet dedicated dengan bandwidth yang memadai untuk mendukung operasional
- Implementasi NAT untuk akses internet melalui ISP

### 3.4 Kebutuhan Layanan Jaringan
Layanan DHCP:
- Server DHCP untuk alokasi IP otomatis pada setiap departemen
- Scope DHCP terpisah untuk masing-masing VLAN

Layanan DNS:
- Server DNS untuk resolusi nama internal dan eksternal
- Implementasi DNS hierarchy untuk memudahkan manajemen resource

Layanan Server:
- Infrastruktur server untuk mendukung aplikasi-aplikasi bisnis
- Server untuk monitoring dan manajemen jaringan

### 3.5 Kebutuhan Keamanan Jaringan
Access Control List (ACL):
- Implementasi ACL untuk membatasi akses antar departemen
- Penerapan kebijakan khusus untuk melindungi informasi sensitif di Departemen Keuangan dan SDM

Keamanan Perimeter:
- Implementasi Next Generation Firewall untuk melindungi jaringan dari ancaman eksternal
- Intrusion Prevention System (IPS) untuk mendeteksi dan mencegah serangan

Endpoint Protection:
- Solusi endpoint security untuk melindungi perangkat end-user
- Manajemen terpusat untuk kebijakan keamanan

### 3.6 Kebutuhan Monitoring dan Manajemen
Network Monitoring:
- Sistem monitoring terpusat untuk memantau kinerja jaringan
- Alert system untuk notifikasi masalah jaringan
- Visibilitas terhadap traffic jaringan untuk analisis dan troubleshooting

Manajemen Konfigurasi:
- Sistem manajemen konfigurasi terpusat
- Standardisasi konfigurasi perangkat jaringan
- Dokumentasi konfigurasi yang terstruktur

### 3.7 Kebutuhan Skalabilitas dan Pertumbuhan
Kapasitas:
- Perangkat jaringan harus mampu menangani jumlah endpoint saat ini dengan margin 30% untuk pertumbuhan
- Rencana pengalamatan IP harus mengakomodasi pertumbuhan di masa depan

Teknologi:
- Implementasi solusi yang mendukung teknologi terbaru seperti IPv6
- Kemampuan untuk mengadopsi teknologi jaringan yang berkembang seperti SD-WAN

## 4. Timeline Rencana Kerja Proyek (Pekan 9-15)
###  Timeline Rencana Kerja (7 Pekan)
| Pekan | Kegiatan                                | Output                                      |
|-------|------------------------------------------|---------------------------------------------|
| 9     | Perencanaan & Desain Awal               | Dokumen perencanaan                         |
| 10    | Desain Topologi Final + VLAN & IP Plan  | Diagram final + Tabel IP                    |
| 11    | Konfigurasi DHCP, DNS, NAT              | Skrip konfigurasi                           |
| 12    | Implementasi Routing OSPF               | Routing antar VLAN & antar gedung           |
| 13    | Implementasi ACL                        | Dokumen kebijakan akses                     |
| 14    | Monitoring & Manajemen Jaringan         | Laporan hasil simulasi monitoring           |
| 15    | Uji Coba & Dokumentasi Akhir            | Laporan akhir & presentasi proyek           |

## 5. Sketsa Awal Desain Jaringan
![Sketsa Desain Jaringan](sketsadmjk.jpeg)

### Gedung A (Kantor Pusat)
#### Router Pusat
Router ini berfungsi sebagai pusat konektivitas jaringan internal Gedung A ke jaringan eksternal melalui router ISP. Selain itu, router pusat juga mengatur distribusi data antar VLAN dengan menerapkan protokol OSPF untuk routing dinamis, NAT untuk koneksi ke internet, dan ACL untuk pembatasan akses antar departemen.

#### Main Switch Pusat
Main switch ini merupakan tulang punggung jaringan di Gedung A yang menghubungkan semua switch departemen serta switch server. Perangkat ini menjadi pusat penghubung antar VLAN seperti VLAN 10 (IT), VLAN 20 (Keuangan), VLAN 30 (SDM), dan VLAN 40 (Server).

#### Switch VLAN Departemen
- **Switch IT (VLAN 10 – 40 PC)**: Digunakan untuk menghubungkan komputer di ruang IT. VLAN ini memiliki akses penuh ke seluruh jaringan karena peran IT sebagai pengelola sistem.

- **Switch Keuangan (VLAN 20 – 25 PC)**: Menghubungkan perangkat departemen keuangan. Akses VLAN ini dibatasi hanya untuk kebutuhan internal, tanpa akses langsung ke server.

- **Switch SDM (VLAN 30 – 20 PC)**: Terkoneksi dengan komputer di ruang SDM. Seperti VLAN keuangan, VLAN ini juga memiliki akses terbatas hanya untuk operasional internal.

#### Switch Server dan Server-Server Internal
- **Switch Server (VLAN 40)**: Berfungsi sebagai penghubung utama untuk semua server yang ditempatkan di server room.

- **Server 1–10 (VLAN 40)**: Menyediakan berbagai layanan penting seperti:
  - **Server 1 (DHCP + DNS)**: Bertugas memberikan alamat IP ke seluruh VLAN melalui DHCP Relay, serta menangani permintaan DNS.
  - **Server Web, Email, FTP, dan Database**: Mendukung aplikasi internal dan komunikasi perusahaan.
  - **AAA Server**: Menangani otentikasi, otorisasi, dan pencatatan aktivitas pengguna di jaringan.
  - **Monitoring Server**: Memantau kondisi dan performa jaringan menggunakan alat seperti PRTG atau Syslog.
  - **NTP dan Backup Server**: Mengatur sinkronisasi waktu dan penyimpanan data cadangan.

### Gedung B (Kantor Cabang)
#### Router Cabang
Router ini berfungsi menghubungkan jaringan lokal Gedung B ke kantor pusat melalui router ISP. Sama seperti di pusat, router ini juga menggunakan OSPF untuk mendukung komunikasi antar gedung yang efisien.

#### Main Switch Cabang
Switch utama yang mendistribusikan koneksi ke seluruh perangkat dan switch departemen di Gedung B.

#### Switch VLAN Departemen
- **Switch Marketing (VLAN 50 – 30 PC)**: Menghubungkan komputer di departemen pemasaran. VLAN ini tidak diperbolehkan mengakses server di pusat demi keamanan data.

- **Switch Operasional (VLAN 60 – 35 PC)**: Digunakan oleh tim operasional, dengan hak akses terbatas hanya ke DNS Server dan internet, sesuai kebijakan ACL.

### Koneksi Eksternal & Antar Gedung
- **Internet Cloud**: Mewakili akses ke jaringan global.
- **Router ISP**: Menjadi jembatan antara jaringan internal (Pusat & Cabang) ke internet.
- **Router Pusat dan Cabang**: Masing-masing terhubung ke router ISP dan menjadi titik komunikasi antar gedung.

### Keamanan dan Pengaturan Akses (ACL)
- **VLAN 10 (IT)**: Memiliki hak akses penuh ke seluruh sistem dan server.
- **VLAN 20 (Keuangan) & VLAN 30 (SDM)**: Hanya memiliki akses internal, tidak langsung ke server.
- **VLAN 50 (Marketing)**: Tidak diizinkan mengakses VLAN Server.
- **VLAN 60 (Operasional)**: Hanya diizinkan mengakses DNS Server dan internet.
- Semua pengaturan akses dilakukan melalui ACL pada Router Pusat.

### Protokol dan Layanan Jaringan
- **Routing Dinamis OSPF**: Digunakan untuk menjamin konektivitas antar router pusat dan cabang.
- **NAT**: Dijalankan di Router Pusat untuk menerjemahkan alamat internal ke alamat publik.
- **Monitoring Server**: Memastikan performa jaringan tetap optimal dan terekam dengan baik.
- **Layanan Server Lain**: Menyediakan HTTP/HTTPS, SMTP/POP3, FTP, database, NTP, dan layanan backup.

## Kendala dan Solusi
## Kesimpulan
## Lampiran
