# Perencanaan Proyek PT. Nusantara Network - Pekan 11

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

## 2. Pembangunan topologi dasar di Cisco Packet Tracer/GNS3.

![alt text](Topologi Revisi di packet tracer)

###  Gedung A (Kantor Pusat)

###  Router Pusat  
Router ini berfungsi sebagai pusat konektivitas jaringan internal Gedung A ke jaringan eksternal melalui router ISP dan router Cabang B.
###  Main Switch Pusat A
Main switch ini merupakan tulang punggung jaringan di Gedung A yang menghubungkan semua switch departemen serta switch server. Perangkat ini menjadi pusat penghubung antar VLAN seperti VLAN 10 (IT), VLAN 20 (Keuangan), VLAN 30 (SDM), dan VLAN 40 (Server).

###  Lantai 1 – Ruangan Operasional

###  VLAN 10 – Departemen IT  
- **Jumlah PC**: 40  
- **Switch akses**: 2 switch lalu terhubung ke Switch Utama A
- **Terhubung ke**: Main switch (Gedung A)  
- **Pembagian PC per switch**:  
  `40 PC / 2 switch = 20 PC per switch`

###  VLAN 20 – Departemen Keuangan  
- **Jumlah PC**: 25  
- **Switch akses**: 2 switch lalu terhubung ke Switch Utama A
- **Terhubung ke**: Main switch (Gedung A)  
- **Pembagian PC per switch**:  
  `25 PC / 2 switch = 13 PC & 12 PC`

###  VLAN 30 – Departemen SDM  
- **Jumlah PC**: 20  
- **Switch akses**: 1 switch lalu terhubung ke Switch Utama A
- **Terhubung ke**: Main switch (Gedung A)  
- **Pembagian PC per switch**:  
  Langsung ke 1 switch (tanpa pembagian)

### Lantai 2 – Server Room

###  VLAN 40 – Server  
- **Jumlah server**: 10  
- **Switch akses**: 1 switch lalu terhubung ke Switch Utama A
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

###  Router Cabang B
Router ini menghubungkan jaringan lokal Gedung B ke kantor pusat melalui router ISP dan router pusat A. Seperti di pusat.

###  Main Switch Cabang B
Switch utama yang mendistribusikan koneksi ke seluruh perangkat dan switch departemen di Gedung B.

###  VLAN 50 – Departemen Marketing  
- **Jumlah PC**: 30  
- **Switch akses**: 2 switch lalu terhubung ke Switch Utama B
- **Terhubung ke**: Main switch (Gedung B)  
- **Pembagian PC per switch**:  
  `30 PC / 2 switch = 15 PC per switch`

###  VLAN 60 – Departemen Operasional  
- **Jumlah PC**: 35  
- **Switch akses**: 2 switch lalu terhubung ke Switch Utama B
- **Terhubung ke**: Main switch (Gedung B)  
- **Pembagian PC per switch**:  
  `35 PC / 2 switch = 18 PC & 17 PC`



###  Koneksi Eksternal & Antar Gedung

- **Internet Cloud**: Mewakili koneksi ke internet global.  
- **Router ISP/Internet**: Jembatan antara jaringan internal dan dunia luar serta menjadi hubungan Router koneksi internet.  
- **Router Pusat & Cabang**: Terhubung ke router ISP, menjadi titik komunikasi antar gedung.


## Tabel IP

| VLAN ID | Nama VLAN | Subnet | Gateway | Range IP | Jumlah Host |
|---------|-----------|--------|---------|----------|-------------|
| 10 | IT | 192.168.10.0/24 | 192.168.10.1 | 192.168.10.2 - 192.168.10.254 | 253 |
| 20 | Keuangan | 192.168.20.0/24 | 192.168.20.1 | 192.168.20.2 - 192.168.20.254 | 253 |
| 30 | SDM | 192.168.30.0/24 | 192.168.30.1 | 192.168.30.2 - 192.168.30.254 | 253 |
| 40 | Server | 192.168.40.0/24 | 192.168.40.1 | 192.168.40.2 - 192.168.40.254 | 253 |
| 50 | Marketing | 192.168.50.0/24 | 192.168.50.1 | 192.168.50.2 - 192.168.50.254 | 253 |
| 60 | Operasional | 192.168.60.0/24 | 192.168.60.1 | 192.168.60.2 - 192.168.60.254 | 253 |
| ISP | Internet | 10.10.10.0/30 | 10.10.10.1 | 10.10.10.2 - 10.10.10.3 | 2 |
| WAN | Antarkantor | 172.16.1.0/30 | 172.16.1.1 | 172.16.1.2 - 172.16.1.3 | 2 |



## Perangkat yang dibutuhkan
| Perangkat        | Jumlah | Lokasi              | Fungsi                                      |
|------------------|--------|----------------------|---------------------------------------------|
| Router           | 2      | Pusat & Cabang       | Routing, NAT, ACL, OSPF                     |
| Router ISP dan Internet          |   2    | luar/Koneksi Eksternal       | Penghubung ke router-router kantor melalui koneksi serta Penguhubung Koneksi Internet              |
| WAN (Cloud)         | 1      | luar/Koneksi Eksternal       | Diwakili oleh cloud "Internet"                   |
| Main Switch      | 2      | Gedung A & B         | Penghubung antar VLAN                       |
| Switch Akses     | 6A&4B     | Gedung A & B         | Menghubungkan PC/server ke jaringan serta Main switch         |
| Server           | 10     | Server Room Gedung A | Layanan DHCP, DNS, Web, Email, Backup, dll |



## 3. Konfigurasi VLAN dan trunking.
### Konfigurasi vlan dan trunking Router A


## Main Switch Router A
```bash
Main-Switch-Router-A>enable
Main-Switch-Router-A#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Main-Switch-Router-A(config)#
Main-Switch-Router-A(config)#! Buat VLAN
Main-Switch-Router-A(config)#vlan 10
Main-Switch-Router-A(config-vlan)# name IT
Main-Switch-Router-A(config-vlan)#exit
Main-Switch-Router-A(config)#vlan 20
Main-Switch-Router-A(config-vlan)# name Keuangan
Main-Switch-Router-A(config-vlan)#exit
Main-Switch-Router-A(config)#vlan 30
Main-Switch-Router-A(config-vlan)# name SDM
Main-Switch-Router-A(config-vlan)#exit
Main-Switch-Router-A(config)#vlan 40
Main-Switch-Router-A(config-vlan)# name Server
Main-Switch-Router-A(config-vlan)#exit
Main-Switch-Router-A(config)#
Main-Switch-Router-A(config)#! Konfigurasi Trunk Port (Fa0/5 ke Router)
Main-Switch-Router-A(config)#interface FastEthernet0/5
Main-Switch-Router-A(config-if)# switchport mode trunk
Main-Switch-Router-A(config-if)# switchport trunk allowed vlan 10,20,30,40
Main-Switch-Router-A(config-if)# no shutdown
Main-Switch-Router-A(config-if)#exit
Main-Switch-Router-A(config)#
Main-Switch-Router-A(config)#! Konfigurasi Access Ports:
Main-Switch-Router-A(config)#interface FastEthernet0/1
Main-Switch-Router-A(config-if)# switchport mode trunk

Main-Switch-Router-A(config-if)# switchport access vlan 10
Main-Switch-Router-A(config-if)# no shutdown
Main-Switch-Router-A(config-if)#exit
Main-Switch-Router-A(config)#
Main-Switch-Router-A(config)#! Konfigurasi Access Ports:
Main-Switch-Router-A(config)#interface FastEthernet0/2
Main-Switch-Router-A(config-if)# switchport mode trunk

Main-Switch-Router-A(config-if)# switchport access vlan 10
Main-Switch-Router-A(config-if)# no shutdown
Main-Switch-Router-A(config-if)#exit
Main-Switch-Router-A(config)#
Main-Switch-Router-A(config)#interface FastEthernet0/3
Main-Switch-Router-A(config-if)# switchport mode trunk

Main-Switch-Router-A(config-if)# switchport access vlan 20
Main-Switch-Router-A(config-if)# no shutdown
Main-Switch-Router-A(config-if)#exit
Main-Switch-Router-A(config)#
Main-Switch-Router-A(config)#interface FastEthernet0/4
Main-Switch-Router-A(config-if)# switchport mode trunk

Main-Switch-Router-A(config-if)# switchport access vlan 20
Main-Switch-Router-A(config-if)# no shutdown
Main-Switch-Router-A(config-if)#exit
Main-Switch-Router-A(config)#
Main-Switch-Router-A(config)#interface FastEthernet0/6
Main-Switch-Router-A(config-if)# switchport mode trunk
Main-Switch-Router-A(config-if)# switchport access vlan 30
Main-Switch-Router-A(config-if)# no shutdown
Main-Switch-Router-A(config-if)#exit
Main-Switch-Router-A(config)#
Main-Switch-Router-A(config)#interface FastEthernet0/7
Main-Switch-Router-A(config-if)# switchport mode trunk
Main-Switch-Router-A(config-if)# switchport access vlan 40
Main-Switch-Router-A(config-if)# no shutdown
Main-Switch-Router-A(config-if)#exit
Main-Switch-Router-A(config)#
Main-Switch-Router-A(config)#end
Main-Switch-Router-A#write memory
Building configuration...
[OK]
```
### Penjelasan Detail
1. **Pembuatan VLAN**  
VLAN digunakan untuk memisahkan jaringan berdasarkan divisi agar lebih terstruktur dan aman. Berikut VLAN yang dibuat:
- VLAN 10 : IT  
- VLAN 20 : Keuangan  
- VLAN 30 : SDM  
- VLAN 40 : Server

2. **Konfigurasi Trunk Port ke Router**  
Port FastEthernet0/5 diatur sebagai trunk, artinya bisa membawa trafik dari beberapa VLAN sekaligus. Trunk ini menghubungkan switch ke router untuk kebutuhan inter-VLAN routing.
```bash
interface FastEthernet0/5
switchport mode trunk
switchport trunk allowed vlan 10,20,30,40
no shutdown
```

3. **Simpan Konfigurasi**  
konfigurasi disimpan agar tetap tersimpan setelah perangkat direstart:
```bash
write memory
```

---

## Switch-IT-1
```bash
Switch>enable
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#
Switch(config)#! Basic Configuration
Switch(config)#hostname Switch-IT-1
Switch-IT-1(config)#
Switch-IT-1(config)#! VLAN Configuration
Switch-IT-1(config)#vlan 10
Switch-IT-1(config-vlan)# name IT
Switch-IT-1(config-vlan)#exit
Switch-IT-1(config)#
Switch-IT-1(config)#! Trunk Port Configuration 
Switch-IT-1(config)#interface FastEthernet0/21
Switch-IT-1(config-if)# description Trunk ke Main Switch
Switch-IT-1(config-if)# switchport mode trunk

Switch-IT-1(config-if)# switchport trunk allowed vlan 10
Switch-IT-1(config-if)# no shutdown
Switch-IT-1(config-if)#exit
Switch-IT-1(config)#
Switch-IT-1(config)#! Access Ports Configuration (for PCs)
Switch-IT-1(config)#interface range FastEthernet0/1 - 20
Switch-IT-1(config-if-range)# description Ports for IT PCs
Switch-IT-1(config-if-range)# switchport mode access
Switch-IT-1(config-if-range)# switchport access vlan 10
Switch-IT-1(config-if-range)# no shutdown
Switch-IT-1(config-if-range)#exit
Switch-IT-1(config)#
Switch-IT-1(config)#
Switch-IT-1(config)#end
Switch-IT-1#write memory
Building configuration...
[OK]
```
### Penjelasan Detail
1. **Konfigurasi Dasar (Basic Configuration)**  
Mengubah nama perangkat dari default menjadi `Switch-IT-1` untuk memudahkan identifikasi perangkat di jaringan.
```bash
hostname Switch-IT-1
```

2. **Pembuatan VLAN**  
Membuat VLAN 10 dengan nama **IT** sebagai jaringan khusus untuk divisi IT.
```bash
vlan 10
name IT
```

3. **Konfigurasi Trunk Port**  
Port **FastEthernet0/21** diatur sebagai trunk yang menghubungkan Switch-IT-1 ke Main Switch, dan hanya mengizinkan VLAN 10.
```bash
interface FastEthernet0/21
description Trunk ke Main Switch
switchport mode trunk
switchport trunk allowed vlan 10
no shutdown
```

4. **Konfigurasi Access Port**  
Port **FastEthernet0/1 hingga 0/20** digunakan untuk PC divisi IT. Port tersebut diatur sebagai access port dan dihubungkan ke VLAN 10.
```bash
interface range FastEthernet0/1 - 20
description Ports for IT PCs
switchport mode access
switchport access vlan 10
no shutdown
```

5. **Simpan Konfigurasi**  
Menyimpan konfigurasi agar tetap berlaku setelah perangkat di-restart.
```bash
write memory
```

---

## Switch-IT-2
```bash
Switch>enable
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#
Switch(config)#! Basic Configuration
Switch(config)#hostname Switch-IT-2
Switch-IT-2(config)#
Switch-IT-2(config)#! VLAN Configuration
Switch-IT-2(config)#vlan 10
Switch-IT-2(config-vlan)# name IT
Switch-IT-2(config-vlan)#exit
Switch-IT-2(config)#
Switch-IT-2(config)#! Trunk Port Configuration 
Switch-IT-2(config)#interface FastEthernet0/20
Switch-IT-2(config-if)# description Trunk ke Main Switch
Switch-IT-2(config-if)# switchport mode trunk

Switch-IT-2(config-if)# switchport trunk allowed vlan 10
Switch-IT-2(config-if)# no shutdown
Switch-IT-2(config-if)#exit
Switch-IT-2(config)#
Switch-IT-2(config)#! Access Ports Configuration (for PCs)
Switch-IT-2(config)#interface range FastEthernet0/1 - 20
Switch-IT-2(config-if-range)# description Ports for IT PCs
Switch-IT-2(config-if-range)# switchport mode access
Switch-IT-2(config-if-range)# switchport access vlan 10
Switch-IT-2(config-if-range)# no shutdown
Switch-IT-2(config-if-range)#exit
Switch-IT-2(config)#
Switch-IT-2(config)#
Switch-IT-2(config)#end
Switch-IT-2#write memory
Building configuration...
[OK]
```
### Penjelasan Detail
1. **Konfigurasi Dasar (Basic Configuration)**  
Mengganti nama default switch menjadi `Switch-IT-2` untuk identifikasi jaringan.
```bash
hostname Switch-IT-2
```

2. **Pembuatan VLAN**  
Membuat VLAN 10 dan memberi nama "IT" untuk jaringan divisi IT.
```bash
vlan 10
name IT
```

3. **Konfigurasi Trunk Port**  
Port **FastEthernet0/20** diatur sebagai trunk untuk koneksi antar switch, hanya mengizinkan VLAN 10 agar lalu lintas IT bisa dilewatkan ke Main Switch.
```bash
interface FastEthernet0/20
description Trunk ke Main Switch
switchport mode trunk
switchport trunk allowed vlan 10
no shutdown
```

4. **Konfigurasi Access Port**  
Port **FastEthernet0/1 sampai 0/20** digunakan untuk komputer divisi IT. Semuanya diatur sebagai access port yang terhubung ke VLAN 10.
```bash
interface range FastEthernet0/1 - 20
description Ports for IT PCs
switchport mode access
switchport access vlan 10
no shutdown
```

5. **Simpan Konfigurasi**  
Agar semua pengaturan tidak hilang saat switch direstart.
```bash
write memory
```

---

## Switch-Keuangan-1
```bash
Switch>enable
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#
Switch(config)#! Basic Configuration
Switch(config)#hostname Switch-Keuangan-1
Switch-Keuangan-1(config)#
Switch-Keuangan-1(config)#! VLAN Configuration
Switch-Keuangan-1(config)#vlan 20
Switch-Keuangan-1(config-vlan)# name Keuangan
Switch-Keuangan-1(config-vlan)#exit
Switch-Keuangan-1(config)#
Switch-Keuangan-1(config)#! Trunk Port Configuration 
Switch-Keuangan-1(config)#interface FastEthernet0/14
Switch-Keuangan-1(config-if)# description Trunk ke Main Switch
Switch-Keuangan-1(config-if)# switchport mode trunk

Switch-Keuangan-1(config-if)# switchport trunk allowed vlan 20
Switch-Keuangan-1(config-if)# no shutdown
Switch-Keuangan-1(config-if)#exit
Switch-Keuangan-1(config)#
Switch-Keuangan-1(config)#! Access Ports Configuration (for PCs)
Switch-Keuangan-1(config)#interface range FastEthernet0/1 - 13
Switch-Keuangan-1(config-if-range)# description Ports for Keuangan PCs
Switch-Keuangan-1(config-if-range)# switchport mode access
Switch-Keuangan-1(config-if-range)# switchport access vlan 20
Switch-Keuangan-1(config-if-range)# no shutdown
Switch-Keuangan-1(config-if-range)#exit
Switch-Keuangan-1(config)#
Switch-Keuangan-1(config)#
Switch-Keuangan-1(config)#end
Switch-Keuangan-1#write memory
Building configuration...
[OK]
```
### Penjelasan Detail
1. **Konfigurasi Dasar (Basic Configuration)**  
Mengganti nama switch menjadi `Switch-Keuangan-1` untuk mempermudah identifikasi di jaringan.
```bash
hostname Switch-Keuangan-1
```

2. **Pembuatan VLAN**  
Membuat VLAN 20 dengan nama "Keuangan" untuk komputer divisi keuangan.
```bash
vlan 20
name Keuangan
```

3. **Konfigurasi Trunk Port**  
Port **FastEthernet0/14** diatur sebagai trunk ke Main Switch, hanya mengizinkan VLAN 20 agar data dari divisi Keuangan dapat dilewatkan.
```bash
interface FastEthernet0/14
description Trunk ke Main Switch
switchport mode trunk
switchport trunk allowed vlan 20
no shutdown
```

4. **Konfigurasi Access Ports**  
Port **FastEthernet0/1 sampai 0/13** digunakan oleh PC divisi Keuangan, semua diatur sebagai access port dan dimasukkan ke VLAN 20.
```bash
interface range FastEthernet0/1 - 13
description Ports for Keuangan PCs
switchport mode access
switchport access vlan 20
no shutdown
```

5. **Simpan Konfigurasi**  
Menyimpan seluruh pengaturan agar tetap aktif setelah perangkat di-reboot.
```bash
write memory
```

---

## Switch-Keuangan-2
```bash
Switch>
Switch>enable
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#
Switch(config)#! Basic Configuration
Switch(config)#hostname Switch-Keuangan-2
Switch-Keuangan-2(config)#
Switch-Keuangan-2(config)#! VLAN Configuration
Switch-Keuangan-2(config)#vlan 20
Switch-Keuangan-2(config-vlan)# name Keuangan
Switch-Keuangan-2(config-vlan)#exit
Switch-Keuangan-2(config)#
Switch-Keuangan-2(config)#! Trunk Port Configuration 
Switch-Keuangan-2(config)#interface FastEthernet0/13
Switch-Keuangan-2(config-if)# description Trunk ke Main Switch
Switch-Keuangan-2(config-if)# switchport mode trunk

Switch-Keuangan-2(config-if)# switchport trunk allowed vlan 20
Switch-Keuangan-2(config-if)# no shutdown
Switch-Keuangan-2(config-if)#exit
Switch-Keuangan-2(config)#
Switch-Keuangan-2(config)#! Access Ports Configuration (for PCs)
Switch-Keuangan-2(config)#interface range FastEthernet0/1 - 12
Switch-Keuangan-2(config-if-range)# description Ports for Keuangan PCs
Switch-Keuangan-2(config-if-range)# switchport mode access
Switch-Keuangan-2(config-if-range)# switchport access vlan 20
Switch-Keuangan-2(config-if-range)# no shutdown
Switch-Keuangan-2(config-if-range)#exit
Switch-Keuangan-2(config)#
Switch-Keuangan-2(config)#
Switch-Keuangan-2(config)#end
Switch-Keuangan-2#write memory
Building configuration...
[OK]
```
### Penjelasan Detail
1. **Konfigurasi Dasar (Basic Configuration)**  
Nama switch diubah menjadi `Switch-Keuangan-2` untuk memudahkan identifikasi di lingkungan jaringan.
```bash
hostname Switch-Keuangan-2
```

2. **Pembuatan VLAN**  
Membuat VLAN 20 dan memberikan nama "Keuangan", VLAN ini khusus digunakan untuk perangkat divisi Keuangan.
```bash
vlan 20
name Keuangan
```

3. **Konfigurasi Trunk Port**  
Port **FastEthernet0/13** dikonfigurasi sebagai trunk yang menghubungkan ke Main Switch dan hanya mengizinkan VLAN 20 untuk dilewatkan.
```bash
interface FastEthernet0/13
description Trunk ke Main Switch
switchport mode trunk
switchport trunk allowed vlan 20
no shutdown
```

4. **Konfigurasi Access Ports**  
Port **FastEthernet0/1 sampai 0/12** diatur sebagai access port untuk PC divisi Keuangan. Semua port ini dimasukkan ke VLAN 20.
```bash
interface range FastEthernet0/1 - 12
description Ports for Keuangan PCs
switchport mode access
switchport access vlan 20
no shutdown
```

5. **Simpan Konfigurasi**  
Perintah untuk menyimpan semua pengaturan agar tetap berlaku setelah switch di-restart.
```bash
write memory
```

---

## Switch-SDM
```bash
Switch>enable
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#
Switch(config)#! Basic Configuration
Switch(config)#hostname Switch-SDM
Switch-SDM(config)#
Switch-SDM(config)#! VLAN Configuration
Switch-SDM(config)#vlan 30
Switch-SDM(config-vlan)# name SDM
Switch-SDM(config-vlan)#exit
Switch-SDM(config)#
Switch-SDM(config)#! Trunk Port Configuration 
Switch-SDM(config)#interface FastEthernet0/21
Switch-SDM(config-if)# description Trunk ke Main Switch
Switch-SDM(config-if)# switchport mode trunk

Switch-SDM(config-if)# switchport trunk allowed vlan 30
Switch-SDM(config-if)# no shutdown
Switch-SDM(config-if)#exit
Switch-SDM(config)#
Switch-SDM(config)#! Access Ports Configuration (for PCs)
Switch-SDM(config)#interface range FastEthernet0/1 - 20
Switch-SDM(config-if-range)# description Ports for SDM PCs
Switch-SDM(config-if-range)# switchport mode access
Switch-SDM(config-if-range)# switchport access vlan 30
Switch-SDM(config-if-range)# no shutdown
Switch-SDM(config-if-range)#exit
Switch-SDM(config)#
Switch-SDM(config)#
Switch-SDM(config)#end
Switch-SDM#write memory
Building configuration...
[OK]
```
### Penjelasan Detail
1. **Konfigurasi Dasar (Basic Configuration)**  
Switch dinamai `Switch-SDM` agar mudah dikenali sebagai perangkat milik divisi SDM.
```bash
hostname Switch-SDM
```

2. **Pembuatan VLAN**  
VLAN 30 dibuat dan dinamai "SDM" untuk memisahkan lalu lintas jaringan divisi Sumber Daya Manusia dari divisi lain.
```bash
vlan 30
name SDM
```

3. **Konfigurasi Trunk Port**  
Port **FastEthernet0/21** dijadikan trunk yang akan menghubungkan switch ini ke Main Switch. Port ini hanya mengizinkan VLAN 30 untuk dilewatkan.
```bash
interface FastEthernet0/21
description Trunk ke Main Switch
switchport mode trunk
switchport trunk allowed vlan 30
no shutdown
```

4. **Konfigurasi Access Ports**  
Port **FastEthernet0/1 hingga 0/20** ditetapkan sebagai access ports untuk perangkat (seperti PC) milik divisi SDM dan dimasukkan ke VLAN 30.
```bash
interface range FastEthernet0/1 - 20
description Ports for SDM PCs
switchport mode access
switchport access vlan 30
no shutdown
```

5. **Menyimpan Konfigurasi**  
Konfigurasi disimpan ke memory agar tetap aktif setelah reboot.
```bash
write memory
```

---
## Switch-Server
```bash
Switch>enable
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#
Switch(config)#! Basic Configuration
Switch(config)#hostname Switch-Server
Switch-Server(config)#
Switch-Server(config)#! VLAN Configuration
Switch-Server(config)#vlan 40
Switch-Server(config-vlan)# name Server
Switch-Server(config-vlan)#exit
Switch-Server(config)#
Switch-Server(config)#! Trunk Port Configuration 
Switch-Server(config)#interface FastEthernet0/11
Switch-Server(config-if)# description Trunk ke Main Switch
Switch-Server(config-if)# switchport mode trunk

Switch-Server(config-if)# switchport trunk allowed vlan 40
Switch-Server(config-if)# no shutdown
Switch-Server(config-if)#exit
Switch-Server(config)#
Switch-Server(config)#! Access Ports Configuration (for Server)
Switch-Server(config)#interface range FastEthernet0/1 - 10
Switch-Server(config-if-range)# description Ports for Server
Switch-Server(config-if-range)# switchport mode access
Switch-Server(config-if-range)# switchport access vlan 40
Switch-Server(config-if-range)# no shutdown
Switch-Server(config-if-range)#exit
Switch-Server(config)#
Switch-Server(config)#
Switch-Server(config)#end
Switch-Server#write memory
Building configuration...
[OK]
```
### Penjelasan Detail
1. **Konfigurasi Dasar (Basic Configuration)**  
Nama switch diubah menjadi `Switch-Server` agar memudahkan identifikasi bahwa switch ini digunakan untuk koneksi server.
```bash
hostname Switch-Server
```

2. **Pembuatan VLAN**  
VLAN 40 dibuat dan dinamai `Server`, digunakan khusus untuk mengelompokkan perangkat server dalam jaringan.
```bash
vlan 40
name Server
```

3. **Konfigurasi Trunk Port**  
Port **FastEthernet0/11** diatur sebagai trunk, fungsinya untuk menghubungkan switch ini dengan Main Switch dan hanya mengizinkan VLAN 40.
```bash
interface FastEthernet0/11
description Trunk ke Main Switch
switchport mode trunk
switchport trunk allowed vlan 40
no shutdown
```

4. **Konfigurasi Access Ports**  
Port **FastEthernet0/1 hingga 0/10** disiapkan untuk perangkat server. Masing-masing port diatur sebagai access dan ditempatkan ke dalam VLAN 40.
```bash
interface range FastEthernet0/1 - 10
description Ports for Server
switchport mode access
switchport access vlan 40
no shutdown
```

5. **Menyimpan Konfigurasi**  
Perintah ini digunakan agar konfigurasi yang sudah dibuat tidak hilang saat perangkat di-restart.
```bash
write memory
```

---

# Konfigurasi vlan dan trunking Router B



## Main Switch Router B
```bash
Main-Switch-Router-B>enable
Main-Switch-Router-B#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Main-Switch-Router-B(config)#
Main-Switch-Router-B(config)#! Buat VLAN
Main-Switch-Router-B(config)#vlan 50
Main-Switch-Router-B(config-vlan)# name Marketing
Main-Switch-Router-B(config-vlan)#exit
Main-Switch-Router-B(config)#vlan 60
Main-Switch-Router-B(config-vlan)# name Operasional
Main-Switch-Router-B(config-vlan)#exit
Main-Switch-Router-B(config)#
Main-Switch-Router-B(config)#! Konfigurasi Trunk Port (Fa0/1 ke Router)
Main-Switch-Router-B(config)#interface FastEthernet0/1
Main-Switch-Router-B(config-if)# switchport mode trunk

Main-Switch-Router-B(config-if)# switchport trunk allowed vlan 50,60
Main-Switch-Router-B(config-if)# no shutdown
Main-Switch-Router-B(config-if)#exit
Main-Switch-Router-B(config)#
Main-Switch-Router-B(config)#! Konfigurasi Access Ports:
Main-Switch-Router-B(config)#interface FastEthernet0/2
Main-Switch-Router-B(config-if)# switchport mode trunk

Main-Switch-Router-B(config-if)# switchport access vlan 50
Main-Switch-Router-B(config-if)# no shutdown
Main-Switch-Router-B(config-if)#exit
Main-Switch-Router-B(config)#
Main-Switch-Router-B(config)#! Konfigurasi Access Ports:
Main-Switch-Router-B(config)#interface FastEthernet0/3
Main-Switch-Router-B(config-if)# switchport mode trunk

Main-Switch-Router-B(config-if)# switchport access vlan 50
Main-Switch-Router-B(config-if)# no shutdown
Main-Switch-Router-B(config-if)#exit
Main-Switch-Router-B(config)#
Main-Switch-Router-B(config)#interface FastEthernet0/4
Main-Switch-Router-B(config-if)# switchport mode trunk
Main-Switch-Router-B(config-if)# switchport access vlan 60
Main-Switch-Router-B(config-if)# no shutdown
Main-Switch-Router-B(config-if)#exit
Main-Switch-Router-B(config)#
Main-Switch-Router-B(config)#interface FastEthernet0/5
Main-Switch-Router-B(config-if)# switchport mode trunk
Main-Switch-Router-B(config-if)# switchport access vlan 60
Main-Switch-Router-B(config-if)# no shutdown
Main-Switch-Router-B(config-if)#exit
Main-Switch-Router-B(config)#
Main-Switch-Router-B(config)#end
Main-Switch-Router-B#write memory
Building configuration...
[OK]
```
### Penjelasan Detail
Berikut penjelasan ulang berdasarkan format yang kamu inginkan untuk **Main Switch Router B**:

---

### Penjelasan Detail

#### Pembuatan VLAN
VLAN digunakan untuk memisahkan jaringan berdasarkan divisi agar lebih terstruktur dan aman. Berikut VLAN yang dibuat:
- **VLAN 50**: Marketing
- **VLAN 60**: Operasional

#### Konfigurasi Trunk Port ke Router
Port **FastEthernet0/1** diatur sebagai trunk, artinya bisa membawa trafik dari beberapa VLAN sekaligus. Trunk ini menghubungkan switch ke router untuk kebutuhan inter-VLAN routing.
```bash
interface FastEthernet0/1
switchport mode trunk
switchport trunk allowed vlan 50,60
no shutdown
```

#### Simpan Konfigurasi
Konfigurasi disimpan agar tetap tersimpan setelah perangkat direstart:
```bash
write memory
```

---


## Switch-Marketing-1
```bash
Switch>enable
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#
Switch(config)#! Basic Configuration
Switch(config)#hostname Switch-Marketing-1
Switch-Marketing-1(config)#
Switch-Marketing-1(config)#! VLAN Configuration
Switch-Marketing-1(config)#vlan 50
Switch-Marketing-1(config-vlan)# name Marketing
Switch-Marketing-1(config-vlan)#exit
Switch-Marketing-1(config)#
Switch-Marketing-1(config)#! Trunk Port Configuration 
Switch-Marketing-1(config)#interface FastEthernet0/16
Switch-Marketing-1(config-if)# description Trunk ke Main Switch
Switch-Marketing-1(config-if)# switchport mode trunk

Switch-Marketing-1(config-if)# switchport trunk allowed vlan 50
Switch-Marketing-1(config-if)# no shutdown
Switch-Marketing-1(config-if)#exit
Switch-Marketing-1(config)#
Switch-Marketing-1(config)#! Access Ports Configuration (for Pcs)
Switch-Marketing-1(config)#interface range FastEthernet0/1 - 15
Switch-Marketing-1(config-if-range)# description Ports for Marketing Pcs
Switch-Marketing-1(config-if-range)# switchport mode access
Switch-Marketing-1(config-if-range)# switchport access vlan 50
Switch-Marketing-1(config-if-range)# no shutdown
Switch-Marketing-1(config-if-range)#exit
Switch-Marketing-1(config)#
Switch-Marketing-1(config)#
Switch-Marketing-1(config)#end
Switch-Marketing-1#write memory
Building configuration...
[OK]
```
### Penjelasan Detail
### **1. Basic Configuration**
- `hostname Switch-Marketing-1`  
  Mengubah nama switch menjadi **"Switch-Marketing-1"** untuk identifikasi.

---

### **2. VLAN Configuration**
- `vlan 50` + `name Marketing`  
  Membuat VLAN baru dengan **ID 50** dan nama **"Marketing"** untuk divisi Marketing.

---

### **3. Trunk Port Configuration (Port 16)**
- `interface FastEthernet0/16`  
  Mengkonfigurasi port **Fa0/16** sebagai **trunk** yang terhubung ke **Main Switch**.
- `switchport mode trunk`  
  Menjadikan port sebagai trunk (untuk membawa traffic VLAN).
- `switchport trunk allowed vlan 50`  
  Hanya mengizinkan VLAN 50 (Marketing) melewati trunk ini.
- `no shutdown`  
  Mengaktifkan port.

---

### **4. Access Ports Configuration (Port 1-15)**
- `interface range FastEthernet0/1 - 15`  
  Mengkonfigurasi port **Fa0/1 sampai Fa0/15** sekaligus.
- `switchport mode access`  
  Menjadikan port sebagai **access** (untuk device langsung seperti PC).
- `switchport access vlan 50`  
  Memasukkan semua port ini ke **VLAN 50 (Marketing)**.
- `no shutdown`  
  Mengaktifkan port.

---

### **5. Simpan Konfigurasi**
- `write memory`  
  Menyimpan semua konfigurasi ke memori permanen switch.

---

## Switch-Marketing-2
```bash
Switch>enable
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#
Switch(config)#! Basic Configuration
Switch(config)#hostname Switch-Marketing-2
Switch-Marketing-2(config)#
Switch-Marketing-2(config)#! VLAN Configuration
Switch-Marketing-2(config)#vlan 50
Switch-Marketing-2(config-vlan)# name Marketing
Switch-Marketing-2(config-vlan)#exit
Switch-Marketing-2(config)#
Switch-Marketing-2(config)#! Trunk Port Configuration 
Switch-Marketing-2(config)#interface FastEthernet0/16
Switch-Marketing-2(config-if)# description Trunk ke Main Switch
Switch-Marketing-2(config-if)# switchport mode trunk

Switch-Marketing-2(config-if)# switchport trunk allowed vlan 50
Switch-Marketing-2(config-if)# no shutdown
Switch-Marketing-2(config-if)#exit
Switch-Marketing-2(config)#
Switch-Marketing-2(config)#! Access Ports Configuration (for Pcs)
Switch-Marketing-2(config)#interface range FastEthernet0/1 - 15
Switch-Marketing-2(config-if-range)# description Ports for Marketing Pcs
Switch-Marketing-2(config-if-range)# switchport mode access
Switch-Marketing-2(config-if-range)# switchport access vlan 50
Switch-Marketing-2(config-if-range)# no shutdown
Switch-Marketing-2(config-if-range)#exit
Switch-Marketing-2(config)#
Switch-Marketing-2(config)#
Switch-Marketing-2(config)#end
Switch-Marketing-2#write memory
Building configuration...
[OK]
```
### Penjelasan Detail
### **1. Basic Configuration**
- `hostname Switch-Marketing-2`  
  Mengubah nama switch menjadi **"Switch-Marketing-2"** (berbeda dengan Switch-Marketing-1 untuk membedakan perangkat).

---

### **2. VLAN Configuration**
- `vlan 50` + `name Marketing`  
  Membuat VLAN dengan **ID 50** dan nama **"Marketing"** (sama seperti Switch-Marketing-1, karena masih dalam divisi yang sama).

---

### **3. Trunk Port Configuration (Port 16)**
- `interface FastEthernet0/16`  
  Mengkonfigurasi port **Fa0/16** sebagai **trunk** yang terhubung ke **Main Switch** (sama seperti Switch-Marketing-1).
- `switchport mode trunk`  
  Port berfungsi sebagai trunk (untuk menghubungkan VLAN antar switch).
- `switchport trunk allowed vlan 50`  
  Hanya mengizinkan VLAN 50 (Marketing) melewati trunk ini (tidak ada VLAN lain yang diizinkan).
- `no shutdown`  
  Mengaktifkan port.

---

### **4. Access Ports Configuration (Port 1-15)**
- `interface range FastEthernet0/1 - 15`  
  Mengatur port **Fa0/1 sampai Fa0/15** sekaligus (untuk koneksi PC karyawan Marketing).
- `switchport mode access`  
  Port berfungsi sebagai **access** 
- `switchport access vlan 50`  
  Memasukkan semua port ini ke **VLAN 50 (Marketing)**.
- `no shutdown`  
  Mengaktifkan port.

---

### **5. Simpan Konfigurasi**
- `write memory`  
  Menyimpan konfigurasi agar tetap aktif setelah switch direstart.

---

## Switch-Operasional-1
```bash
Switch>enable
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#
Switch(config)#! Basic Configuration
Switch(config)#hostname Switch-Operasional-1
Switch-Operasional-1(config)#
Switch-Operasional-1(config)#! VLAN Configuration
Switch-Operasional-1(config)#vlan 60
Switch-Operasional-1(config-vlan)# name Operasional
Switch-Operasional-1(config-vlan)#exit
Switch-Operasional-1(config)#
Switch-Operasional-1(config)#! Trunk Port Configuration 
Switch-Operasional-1(config)#interface FastEthernet0/19
Switch-Operasional-1(config-if)# description Trunk ke Main Switch
Switch-Operasional-1(config-if)# switchport mode trunk

Switch-Operasional-1(config-if)# switchport trunk allowed vlan 60
Switch-Operasional-1(config-if)# no shutdown
Switch-Operasional-1(config-if)#exit
Switch-Operasional-1(config)#
Switch-Operasional-1(config)#! Access Ports Configuration (for Pcs)
Switch-Operasional-1(config)#interface range FastEthernet0/1 - 18
Switch-Operasional-1(config-if-range)# description Ports for Operasional Pcs
Switch-Operasional-1(config-if-range)# switchport mode access
Switch-Operasional-1(config-if-range)# switchport access vlan 60
Switch-Operasional-1(config-if-range)# no shutdown
Switch-Operasional-1(config-if-range)#exit
Switch-Operasional-1(config)#
Switch-Operasional-1(config)#
Switch-Operasional-1(config)#end
Switch-Operasional-1#write memory
Building configuration...
[OK]
```
### Penjelasan Detail
### **1. Basic Configuration**
- `hostname Switch-Operasional-1`  
  Mengubah nama switch menjadi **"Switch-Operasional-1"** untuk membedakan perangkat.

---

### **2. VLAN Configuration**
- `vlan 60` + `name Operasional`  
  Membuat VLAN baru dengan **ID 60** dan nama **"Operasional"** untuk divisi Operasional.

---

### **3. Trunk Port Configuration (Port 19)**
- `interface FastEthernet0/19`  
  Mengkonfigurasi port **Fa0/19** sebagai **trunk** yang terhubung ke **Main Switch**.
- `switchport mode trunk`  
  Menjadikan port sebagai trunk (untuk membawa traffic VLAN).
- `switchport trunk allowed vlan 60`  
  Hanya mengizinkan VLAN 60 (Operasional) melewati trunk ini.
- `no shutdown`  
  Mengaktifkan port.

---

### **4. Access Ports Configuration (Port 1-18)**
- `interface range FastEthernet0/1 - 18`  
  Mengkonfigurasi port **Fa0/1 sampai Fa0/18** sekaligus.
- `switchport mode access`  
  Menjadikan port sebagai **access** (untuk device langsung seperti PC).
- `switchport access vlan 60`  
  Memasukkan semua port ini ke **VLAN 60 (Operasional)**.
- `no shutdown`  
  Mengaktifkan port.

---

### **5. Simpan Konfigurasi**
- `write memory`  
  Menyimpan semua konfigurasi ke memori permanen switch.

---

## Switch-Operasional-2
```bash
Switch>enable
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#
Switch(config)#! Basic Configuration
Switch(config)#hostname Switch-Operasional-2
Switch-Operasional-2(config)#
Switch-Operasional-2(config)#! VLAN Configuration
Switch-Operasional-2(config)#vlan 60
Switch-Operasional-2(config-vlan)# name Operasional
Switch-Operasional-2(config-vlan)#exit
Switch-Operasional-2(config)#
Switch-Operasional-2(config)#! Trunk Port Configuration 
Switch-Operasional-2(config)#interface FastEthernet0/18
Switch-Operasional-2(config-if)# description Trunk ke Main Switch
Switch-Operasional-2(config-if)# switchport mode trunk

Switch-Operasional-2(config-if)# switchport trunk allowed vlan 60
Switch-Operasional-2(config-if)# no shutdown
Switch-Operasional-2(config-if)#exit
Switch-Operasional-2(config)#
Switch-Operasional-2(config)#! Access Ports Configuration (for Pcs)
Switch-Operasional-2(config)#interface range FastEthernet0/1 - 17
Switch-Operasional-2(config-if-range)# description Ports for Operasional Pcs
Switch-Operasional-2(config-if-range)# switchport mode access
Switch-Operasional-2(config-if-range)# switchport access vlan 60
Switch-Operasional-2(config-if-range)# no shutdown
Switch-Operasional-2(config-if-range)#exit
Switch-Operasional-2(config)#
Switch-Operasional-2(config)#
Switch-Operasional-2(config)#end
Switch-Operasional-2#write memory
Building configuration...
[OK]
```
### Penjelasan Detail
### **1. Basic Configuration**
- `hostname Switch-Operasional-2`  
  Mengubah nama switch menjadi **"Switch-Operasional-2"** (switch kedua untuk divisi Operasional).

---

### **2. VLAN Configuration**
- `vlan 60` + `name Operasional`  
  Menggunakan **VLAN 60** dengan nama **"Operasional"** (sama dengan Switch-Operasional-1 karena satu divisi).

---

### **3. Trunk Port Configuration (Port 18)**
- `interface FastEthernet0/18`  
  Mengatur port **Fa0/18** sebagai **trunk** ke Main Switch (berbeda dengan Switch-Operasional-1 yang pakai Fa0/19).
- `switchport mode trunk`  
  Port berfungsi sebagai trunk untuk menghubungkan VLAN antar switch.
- `switchport trunk allowed vlan 60`  
  Hanya VLAN 60 (Operasional) yang diperbolehkan lewat trunk ini.
- `no shutdown`  
  Mengaktifkan port.

---

### **4. Access Ports Configuration (Port 1-17)**
- `interface range FastEthernet0/1 - 17`  
  Mengkonfigurasi port **Fa0/1 sampai Fa0/17** untuk PC karyawan Operasional (lebih sedikit port dibanding Switch-Operasional-1).
- `switchport mode access`  
  Port berfungsi sebagai access (koneksi langsung ke device).
- `switchport access vlan 60`  
  Semua port dimasukkan ke **VLAN 60**.
- `no shutdown`  
  Mengaktifkan port.

---

### **5. Simpan Konfigurasi**
- `write memory`  
  Menyimpan konfigurasi agar tetap aktif setelah switch direstart.

---


## 4. Implementasi routing antar-VLAN.
## Router A
```bash
router> enable
router# configure terminal
Router(config)# 
Router(config)#! Aktifkan IP Routing 
Router(config)#ip routing 
Router(config)# 
Router(config)#! Konfigurasi interface LAN ke switch utama (trunk) 
Router(config)#interface GigabitEthernet0/0 
Router(config-if)# description Koneksi ke Main Switch 
Router(config-if)# no shutdown 
Router(config-if)#exit 
Router(config)# 
Router(config)#! VLAN 10 IT 
Router(config)#interface GigabitEthernet0/0.10 
Router(config-subif)# encapsulation dot1Q 10 
Router(config-subif)# ip address 192.168.10.1 255.255.255.0 
Router (config-subif)# description VLAN IT 
Router(config-subif)#exit 
Router(config)# 
Router(config)#! VLAN 20 Keuangan 
Router(config)#interface GigabitEthernet0/0.20 
Router(config-subif)# encapsulation dot1Q 20 
Router(config-subif)# ip address 192.168.20.1 255.255.255.0 
Router (config-subif)# description VLAN Keuangan 
Router(config-subif)#exit 
Router(config)# 
Router (config)#! VLAN 30 SDM 
Router(config)#interface GigabitEthernet0/0.30 
Router(config-subif)# encapsulation dotlQ 30 
Router(config-subif)# ip address 192.168.30.1 255.255.255.0 
Router(config-subif)# description VLAN SDM 
Router(config-subif)#exit 
Router(config)# 
Router(config)#! VLAN 40 Server 
Router(config)#interface GigabitEthernet0/0.40 
Router(config-subif)# encapsulation dotlQ 40 
Router(config-subif)# ip address 192.168.40.1 255.255.255.0 
Router(config-subif)# description VLAN Server 
Router(config-subif)#exit 
Router (config)# 
Router(config)#end 
Router#write memory 
Building configuration...
[OK]
```
### Penjelasan Detail
### **1. Mengaktifkan IP Routing**
- `ip routing`  
  Mengaktifkan fungsi router untuk melewatkan traffic antar jaringan/VLAN.

---

### **2. Konfigurasi Interface Utama (Trunk)**
- `interface GigabitEthernet0/0`  
  Pesan mengatur port **G0/0** sebagai **trunk** ke **Main Switch**.
- `no shutdown`  
  Mengaktifkan port.

---

### **3. Konfigurasi Sub-Interface untuk VLAN**
Router ini membuat **sub-interface** (virtual interface) untuk setiap VLAN dengan konfigurasi:

#### **VLAN 10 (IT)**
- `interface G0/0.10` + `encapsulation dot1Q 10`  
  Membuat sub-interface untuk VLAN 10 (IT).
- `ip address 192.168.10.1 255.255.255.0`  
  Memberikan **IP gateway** untuk VLAN 10: **192.168.10.1**.

#### **VLAN 20 (Keuangan)**
- `interface G0/0.20` + `encapsulation dot1Q 20`  
  Sub-interface untuk VLAN 20 (Keuangan).
- `ip address 192.168.20.1 255.255.255.0`  
  Gateway VLAN 20: **192.168.20.1**.

#### **VLAN 30 (SDM)**
- `interface G0/0.30` + `encapsulation dot1Q 30`  
  Sub-interface untuk VLAN 30 (SDM).
- `ip address 192.168.30.1 255.255.255.0`  
  Gateway VLAN 30: **192.168.30.1**.

#### **VLAN 40 (Server)**
- `interface G0/0.40` + `encapsulation dot1Q 40`  
  Sub-interface untuk VLAN 40 (Server).
- `ip address 192.168.40.1 255.255.255.0`  
  Gateway VLAN 40: **192.168.40.1**.

---

### **4. Simpan Konfigurasi**
- `write memory`  
  Menyimpan semua konfigurasi ke memori permanen router.

---

## Router A KONFIGURASI 
```bash
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#interface GigabitEthernet0/0
Router(config-if)# description Koneksi ke Main Switch
Router(config-if)# ip address 10.1.1.1 255.255.255.252
Router(config-if)# no shutdown
Router(config-if)#exit
Router(config)#
Router(config)#interface GigabitEthernet0/1
Router(config-if)# description Koneksi ke ISP
Router(config-if)# ip address 10.10.10.2 255.255.255.252
Router(config-if)# no shutdown
Router(config-if)#exit
Router(config)#
Router(config)#interface GigabitEthernet0/2
Router(config-if)# description Koneksi langsung ke Gedung B
Router(config-if)# ip address 192.168.3.1 255.255.255.252
Router(config-if)# no shutdown
Router(config-if)#exit
Router(config)#
Router(config)#router rip
Router(config-router)# version 2
Router(config-router)# no auto-summary
Router(config-router)# network 10.0.0.0
Router(config-router)# network 192.168.1.0
Router(config-router)# network 192.168.3.0
Router(config-router)#exit
Router(config)#
Router(config)#router rip
Router(config-router)# version 2
Router(config-router)# network 192.168.10.0
Router(config-router)# network 192.168.20.0
Router(config-router)# network 192.168.30.0
Router(config-router)# network 192.168.40.0
Router(config-router)# no auto-summary
Router(config-router)#exit
```
### Penjelasan Detail
### **1. Konfigurasi Interface**
Router A memiliki 3 port utama:
1. **Gig0/0**  
   - IP: `10.1.1.1/30`  
   - Fungsi: Terhubung ke **Main Switch** (jaringan lokal).  
2. **Gig0/1**  
   - IP: `10.10.10.2/30`  
   - Fungsi: Terhubung ke **ISP** (akses internet).  
3. **Gig0/2**  
   - IP: `192.168.3.1/30`  
   - Fungsi: Koneksi **langsung ke Gedung B** (jaringan antar gedung).  

Semua port diaktifkan dengan `no shutdown`.

---

### **2. Konfigurasi Routing RIP**
Router menggunakan **RIP versi 2** untuk berbagi informasi jaringan:  
- **Network yang diiklankan**:  
  - `10.0.0.0` (jaringan ISP dan lokal)  
  - `192.168.1.0` (misal: VLAN default)  
  - `192.168.3.0` (koneksi ke Gedung B)  
  - VLAN lainnya (`192.168.10.0` s/d `192.168.40.0`).  
- **Fitur**:  
  - `no auto-summary`: Mematikan fitur summarisasi agar subnet kecil tetap terbaca.  

---

### **3. Fungsi Utama**
- **Gateway untuk VLAN**:  
  Router A menjadi gateway untuk VLAN 10/20/30/40 (IT/Keuangan/SDM/Server).  
- **Koneksi ke ISP**:  
  Mengarahkan traffic internet melalui `10.10.10.2`.  
- **Koneksi ke Gedung B**:  
  Membuat jalur khusus (`192.168.3.0/30`) untuk komunikasi antar gedung.  

---

## Router ISP KONFIGURASI 
```bash
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#
Router(config)#interface GigabitEthernet0/0
Router(config-if)# description Koneksi ke Router A
Router(config-if)# ip address 10.10.10.1 255.255.255.252
Router(config-if)# no shutdown
Router(config-if)#exit
Router(config)#
Router(config)#interface GigabitEthernet0/2
Router(config-if)# description Koneksi ke Gedung B
Router(config-if)# ip address 192.168.2.1 255.255.255.252
Router(config-if)# no shutdown
Router(config-if)#exit
Router(config)#
Router(config)#router rip
Router(config-router)# version 2
Router(config-router)# no auto-summary
Router(config-router)# network 10.0.0.0
Router(config-router)# network 192.168.2.0
Router(config-router)#exit
```
### Penjelasan Detail
### **1. Konfigurasi Interface**
Router ISP memiliki 2 port utama:
1. **Gig0/0**  
   - IP: `10.10.10.1/30`  
   - Fungsi: Terhubung ke **Router A** (untuk akses internet Gedung A).  
2. **Gig0/2**  
   - IP: `192.168.2.1/30`  
   - Fungsi: Terhubung **langsung ke Gedung B** (jalur backup).  

Semua port diaktifkan dengan `no shutdown`.

---

### **2. Konfigurasi Routing RIP**
Router ISP menggunakan **RIP versi 2** dengan:
- **Network yang diiklankan**:  
  - `10.0.0.0` (jaringan ke Router A)  
  - `192.168.2.0` (jaringan ke Gedung B)  
- **Fitur**:  
  - `no auto-summary`: Memastikan subnet kecil (seperti `/30`) tetap terbaca.  

---

### **3. Fungsi Utama**
- **Penyedia Internet**:  
  Memberikan akses internet ke Router A via `10.10.10.1`.  
- **Jalur Backup ke Gedung B**:  
  Membuat koneksi langsung (`192.168.2.0/30`) untuk redundansi.  
- **Pusat Routing**:  
  Mengarahkan traffic antara Gedung A dan B jika diperlukan.  

---

## Router B
```bash
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#
Router(config)#! Aktifkan IP Routing
Router(config)#ip routing
Router(config)#
Router(config)#! Konfigurasi interface LAN ke switch utama (trunk)
Router(config)#interface GigabitEthernet0/1
Router(config-if)# description Koneksi ke Main Switch
Router(config-if)# no shutdown

Router(config-if)#exit
Router(config)#
Router(config)#! VLAN 50 - Marketing
Router(config)#interface GigabitEthernet0/0.50
Router(config-subif)# encapsulation dot1Q 50
Router(config-subif)# ip address 192.168.50.1 255.255.255.0
Router(config-subif)# description VLAN Marketing
Router(config-subif)#exit
Router(config)#
Router(config)#! VLAN 60 - Operasional
Router(config)#interface GigabitEthernet0/0.60
Router(config-subif)# encapsulation dot1Q 60
Router(config-subif)# ip address 192.168.60.1 255.255.255.0
Router(config-subif)# description VLAN Operasional
Router(config-subif)#exit
Router(config)#
Router(config)#end
Router#write memory
Building configuration...
[OK]
```
### Penjelasan Detail
### **1. Mengaktifkan IP Routing**
- `ip routing`  
  Mengaktifkan fungsi router untuk melewatkan traffic antar jaringan/VLAN.

---

### **2. Konfigurasi Interface Utama (Trunk)**
- `interface GigabitEthernet0/1`  
  Pesan mengatur port **G0/1** sebagai **trunk** ke **Main Switch**.
- `no shutdown`  
  Mengaktifkan port.

---

### **3. Konfigurasi Sub-Interface untuk VLAN**
Router ini membuat **sub-interface** untuk VLAN Marketing dan Operasional:

#### **VLAN 50 (Marketing)**
- `interface G0/0.50` + `encapsulation dot1Q 50`  
  Sub-interface untuk VLAN 50 (Marketing).
- `ip address 192.168.50.1 255.255.255.0`  
  Memberikan **IP gateway** untuk VLAN 50: **192.168.50.1**.

#### **VLAN 60 (Operasional)**
- `interface G0/0.60` + `encapsulation dot1Q 60`  
  Sub-interface untuk VLAN 60 (Operasional).
- `ip address 192.168.60.1 255.255.255.0`  
  Gateway VLAN 60: **192.168.60.1**.

---

### **4. Simpan Konfigurasi**
- `write memory`  
  Menyimpan semua konfigurasi ke memori permanen router.

---

## Router B KONFIGURASI 
```bash
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#
Router(config)#interface GigabitEthernet0/0
Router(config-if)# description Koneksi ke Main Switch
Router(config-if)# ip address 10.1.2.1 255.255.255.252
Router(config-if)# no shutdown
Router(config-if)#exit
Router(config)#
Router(config)#interface GigabitEthernet0/1
Router(config-if)# description Koneksi ke ISP
Router(config-if)# ip address 192.168.2.2 255.255.255.252
Router(config-if)# no shutdown
Router(config-if)#exit
Router(config)#
Router(config)#interface GigabitEthernet0/2
Router(config-if)# description Koneksi langsung ke Router A
Router(config-if)# ip address 192.168.3.2 255.255.255.252
Router(config-if)# no shutdown
Router(config-if)#exit
Router(config)#
Router(config)#router rip
Router(config-router)# version 2
Router(config-router)# no auto-summary
Router(config-router)# network 192.168.2.0
Router(config-router)# network 192.168.3.0
Router(config-router)#exit
Router(config)#
Router(config)#router rip
Router(config-router)# version 2
Router(config-router)# network 192.168.50.0
Router(config-router)# network 192.168.60.0
Router(config-router)# no auto-summary
Router(config-router)#exit
```
### Penjelasan Detail
### **1. Konfigurasi Interface**
Router B memiliki 3 port utama dengan fungsi berbeda:

1. **Gig0/0**  
   - IP: `10.1.2.1/30`  
   - Deskripsi: Koneksi ke **Main Switch**  
   - Fungsi: Menghubungkan ke jaringan lokal Gedung B  

2. **Gig0/1**  
   - IP: `192.168.2.2/30`  
   - Deskripsi: Koneksi ke **ISP**  
   - Fungsi: Menyediakan akses internet backup  

3. **Gig0/2**  
   - IP: `192.168.3.2/30`  
   - Deskripsi: Koneksi **langsung ke Router A**  
   - Fungsi: Membuat jalur khusus antar gedung  

Semua interface diaktifkan dengan `no shutdown`.

---

### **2. Konfigurasi Routing RIP**
Router B menggunakan **RIP versi 2** dengan:

- **Network yang diiklankan**:  
  - `192.168.2.0` (koneksi ke ISP)  
  - `192.168.3.0` (koneksi ke Router A)  
  - `192.168.50.0` (VLAN Marketing)  
  - `192.168.60.0` (VLAN Operasional)  

- **Fitur penting**:  
  - `no auto-summary`: Memastikan semua subnet (/30 dan /24) terbaca dengan benar  
  - `version 2`: Mendukung pengiriman subnet mask dalam update routing  

---

### **3. Fungsi Utama Router B**
1. **Gateway untuk VLAN Lokal**:  
   - Menjadi gateway untuk:  
     - VLAN 50 (Marketing): `192.168.50.0/24`  
     - VLAN 60 (Operasional): `192.168.60.0/24`  

2. **Koneksi Redundansi**:  
   - Memiliki dua jalur keluar:  
     - Utama: Ke Router A via `192.168.3.2`  
     - Backup: Ke ISP via `192.168.2.2`  

3. **Pembelajaran Rute Otomatis**:  
   - Dengan RIP, router bisa:  
     - Otomatis mengetahui jaringan di Router A  
     - Menemukan rute alternatif jika salah satu jalur down  

## Kendala yang dihadapi dan solusinya
### Hasil Konektivitas Antar-VLAN 
![alt text](<Hasil konektivitas antar-VLAN .png>)
#### Penjelasan :
Tabel di atas menunjukkan hasil pengujian konektivitas antar departemen yang berbeda gedung. Dalam bahasa sederhana:

1. **Baris 1**: PC Keuangan-2 (Gedung A) berhasil terhubung ke PC Marketing (Gedung B)
2. **Baris 2**: PC SDM (Gedung A) berhasil terhubung ke PC Operasional (Gedung B)
3. **Baris 3**: PC Operasional (Gedung B) berhasil terhubung balik ke PC SDM (Gedung A)

Semua pengujian menunjukkan status "Successful" yang artinya:
- PC dari VLAN berbeda dapat saling berkomunikasi
- Koneksi antar gedung berjalan lancar
- Konfigurasi VLAN, router, dan routing berhasil diimplementasikan
- Tidak ada hambatan dalam komunikasi antar departemen yang berbeda lokasi


---


## Kendala yang dihadapi dan solusinya
### Terdapat ada topologi Revisi di bagian Switch dan Router
#### Sebelum 
![alt text](<topologi pekan 10.png>)

#### Sesudah
![alt text](<Topologi Revisi di packet tracer.png>)


#### Penjelasan : 
**Permasalahan 1**

Pada Switch Sebelumnya Switch Vlan 10, 20, 50, dan 60 dijadikan 1 dan 2 menjadi satu Switch agar biar mudah enak dilihat tapi saat konfigurasi terdapat error banyak lalu saat melakukan Konfigurasi Vlan dan Trunking terdapat masalah dimana tidak bisa terbaca pada Switch yang udah dijadikan satu dan tidak bisa kirim pesan antar vlannya Seperti vlan 10 pada switch IT-1 ke Switch IT-2 itu terdapat gagal konektivitasnya.

**Solusi 1**
Saat melakukan percobaan lebih lanjut Semua yang dijadikan Satu lebih baik dipisah karena mudah dikonfigurasi. Agar biar bisa Kebaca langsung Main Switch ke Switch lainnya yang udah dipisah.  

**contoh nya pada konfigurasi dari Main switch A (vlan 10 dan 20) :**
```bash
Main-Switch-Router-A(config-if)# switchport access vlan 10
Main-Switch-Router-A(config-if)# no shutdown
Main-Switch-Router-A(config-if)#exit
Main-Switch-Router-A(config)#
Main-Switch-Router-A(config)#! Konfigurasi Access Ports:
Main-Switch-Router-A(config)#interface FastEthernet0/2
Main-Switch-Router-A(config-if)# switchport mode trunk

Main-Switch-Router-A(config-if)# switchport access vlan 10
Main-Switch-Router-A(config-if)# no shutdown
Main-Switch-Router-A(config-if)#exit
Main-Switch-Router-A(config)#
Main-Switch-Router-A(config)#interface FastEthernet0/3
Main-Switch-Router-A(config-if)# switchport mode trunk

Main-Switch-Router-A(config-if)# switchport access vlan 20
Main-Switch-Router-A(config-if)# no shutdown
Main-Switch-Router-A(config-if)#exit
Main-Switch-Router-A(config)#
Main-Switch-Router-A(config)#interface FastEthernet0/4
Main-Switch-Router-A(config-if)# switchport mode trunk

Main-Switch-Router-A(config-if)# switchport access vlan 20
Main-Switch-Router-A(config-if)# no shutdown
Main-Switch-Router-A(config-if)#exit
Main-Switch-Router-A(config)#
```
---

**Permasalahan 2**  

Pada topologi **sebelum** Router A-ISP-Router B, semua traffic antar VLAN (contoh: VLAN 20 Keuangan di Gedung A ke VLAN 60 Operasional di Gedung B) **harus melewati Router ISP**. Saat dilakukan konfigurasi, muncul masalah:  
- **Bottleneck**: Router ISP kepenuhan traffic karena jadi titik pusat.  
   
- **Single Point of Failure**: Jika Router ISP mati, komunikasi antar VLAN **langsung putus total**.  
- **Error Konfigurasi**: Routing static di Router ISP sering gagal baca VLAN baru, sehingga VLAN 20 tidak bisa kirim data ke VLAN 60.  



**Solusi 2**  

Setelah diubah ke topologi **sesudah**, masalah teratasi dengan:  
- **Routing Langsung via Router B**:  
  - Router B di Gedung A dan Gedung B sekarang bisa handle traffic antar VLAN **tanpa lewat ISP**.  

- **Redundansi**: Jika Router ISP down, Router B tetap bisa hubungkan VLAN 20 dan 60.  

---

## Kesimpulan
Perancangan dan implementasi infrastruktur jaringan untuk PT. Nusantara Network telah berhasil dilaksanakan dengan menerapkan praktik terbaik dalam teknologi jaringan. Beberapa kesimpulan dari proyek ini adalah:

1. **Segmentasi Jaringan Efektif** - Implementasi VLAN (10, 20, 30, 40 di Gedung A dan 50, 60 di Gedung B) berhasil memisahkan traffic jaringan berdasarkan departemen, meningkatkan performa dan keamanan jaringan perusahaan.

2. **Konektivitas Antar Gedung yang Handal** - Penerapan koneksi redundan dengan jalur utama langsung antara Router A dan Router B, serta jalur backup melalui Router ISP, memberikan ketahanan jaringan yang lebih baik dan menghindari single point of failure.

3. **Implementasi Routing yang Fleksibel** - Penggunaan routing dinamis RIP v2 memungkinkan adaptasi otomatis terhadap perubahan jaringan dan memfasilitasi komunikasi antar-VLAN yang lancar.

4. **Arsitektur Scalable** - Desain jaringan saat ini mampu mendukung total 160 pengguna (40 IT, 25 Keuangan, 20 SDM, 30 Marketing, 35 Operasional, dan 10 server) dengan kemungkinan pertumbuhan di masa depan.

5. **Optimasi Topologi** - Revisi topologi dari model yang berpusat pada ISP menjadi koneksi langsung antar router gedung mengatasi masalah bottleneck dan meningkatkan keandalan koneksi antar departemen.

6. **Pembagian Alamat IP Terstruktur** - Skema pengalamatan IP yang terorganisir dengan baik (192.168.10.0/24 hingga 192.168.60.0/24) memberikan pengelolaan jaringan yang lebih mudah dan memungkinkan routing yang efisien.

7. **Konfigurasi VLAN dan Trunking yang Efisien** - Implementasi VLAN dan trunking pada setiap switch telah berhasil memisahkan traffic untuk setiap departemen. Penggunaan port trunk pada main switch dan port akses pada switch departemen memastikan data tetap dalam jalur VLAN yang benar, meningkatkan keamanan dan manajemen jaringan. Konfigurasi switchport mode trunk pada port-port penghubung antar switch dan switchport mode access pada port koneksi PC memastikan segmentasi jaringan berjalan optimal.

8. **Konektivitas Antar-VLAN yang Terbukti** - Hasil pengujian menunjukkan bahwa komunikasi antar departemen berbeda (VLAN berbeda) dan antar gedung berbeda berjalan dengan lancar. PC Keuangan berhasil terhubung ke PC Marketing, PC SDM ke PC Operasional, dan sebaliknya, membuktikan keberhasilan implementasi routing antar-VLAN dan koneksi antar gedung.

## Lampiran
https://github.com/shoryuwu/PROYEK-DMJK/tree/main
