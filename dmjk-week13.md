# Proyek PT. Nusantara Network - Pekan 13

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
2. Konfigurasi DHCP Server untuk setiap departemen.
3. Implementasi DNS Server untuk resolusi nama internal.
4. Konfigurasi NAT untuk akses internet.
5. Kesimpulan
6. Lampiran

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


## 2. Konfigurasi DHCP Server untuk setiap departemen.
## Router A
```bash
Router_A>
Router_A>enable
Router_A#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router_A(config)#
Router_A(config)#ip dhcp excluded-address 192.168.10.1 192.168.10.10
Router_A(config)#ip dhcp excluded-address 192.168.20.1 192.168.20.10
Router_A(config)#ip dhcp excluded-address 192.168.30.1 192.168.30.10
Router_A(config)#ip dhcp excluded-address 192.168.40.1 192.168.40.10
Router_A(config)#
Router_A(config)#ip dhcp pool VLAN10_IT
Router_A(dhcp-config)# network 192.168.10.0 255.255.255.0
Router_A(dhcp-config)# default-router 192.168.10.1
Router_A(dhcp-config)# dns-server 192.168.40.2
Router_A(dhcp-config)#
Router_A(dhcp-config)#ip dhcp pool VLAN20_Keuangan
Router_A(dhcp-config)# network 192.168.20.0 255.255.255.0
Router_A(dhcp-config)# default-router 192.168.20.1
Router_A(dhcp-config)# dns-server 192.168.40.2
Router_A(dhcp-config)#
Router_A(dhcp-config)#ip dhcp pool VLAN30_SDM
Router_A(dhcp-config)# network 192.168.30.0 255.255.255.0
Router_A(dhcp-config)# default-router 192.168.30.1
Router_A(dhcp-config)# dns-server 192.168.40.2
Router_A(dhcp-config)#
Router_A(dhcp-config)#ip dhcp pool VLAN40_Server
Router_A(dhcp-config)# network 192.168.40.0 255.255.255.0
Router_A(dhcp-config)# default-router 192.168.40.1
Router_A(dhcp-config)# dns-server 192.168.40.2
Router_A(dhcp-config)#ex
Router_A(config)#
```
---

#### DHCP Testing - Departemen IT

![alt text](image/dhcp_it_pc1.png)

### **Analisis Konfigurasi DHCP pada PC1 IT-1 (VLAN 10)**

1. **Status DHCP**

   * Konfigurasi IP pada PC1 disetel ke mode **DHCP** (bukan Static), artinya PC meminta alamat IP secara otomatis dari DHCP Server.
   * Status menampilkan pesan **"DHCP request successful."**, yang menandakan bahwa proses negosiasi DHCP (Discover → Offer → Request → Acknowledgement) telah berhasil dilaksanakan.

2. **Alamat IP yang Diberikan**

   * **IPv4 Address**: `192.168.10.14`
     → Ini merupakan alamat IP dinamis yang dialokasikan DHCP Server dari pool untuk **VLAN 10 / Departemen IT**.
   * **Subnet Mask**: `255.255.255.0`
     → Menunjukkan jaringan kelas C dengan 256 alamat IP total (254 host usable).
   * **Default Gateway**: `192.168.10.1`
     → Ini adalah IP interface router pada VLAN 10, yang mengarahkan lalu lintas ke jaringan lain (inter-VLAN routing).
   * **DNS Server**: `192.168.40.2`
     → Menunjukkan bahwa DNS Server berada pada jaringan VLAN 40 (Server), dan DHCP juga mendistribusikan informasi DNS secara otomatis.

3. **Keberhasilan Konfigurasi**

   * PC berhasil mendapatkan seluruh parameter penting: IP Address, Subnet Mask, Gateway, dan DNS.
   * Ini berarti bahwa konfigurasi DHCP Server di sisi Router (mungkin Router A) **telah benar dan aktif untuk VLAN 10**, serta pengalamatan IP bekerja dengan **baik dan efisien**.

4. **Konteks VLAN**

   * VLAN 10 digunakan untuk Departemen IT. Berdasarkan struktur subnetting, `192.168.10.0/24` diperuntukkan untuk IT.
   * IP yang didapatkan `192.168.10.14` berada dalam rentang yang valid, menegaskan bahwa **VLAN tagging dan trunking antar switch–router juga berfungsi baik**.

### **Kesimpulan**

PC1 IT-1 mendapatkan IP secara otomatis dari DHCP Server tanpa kesalahan, dengan parameter yang sesuai untuk jaringan IT (VLAN 10). Hal ini menunjukkan bahwa konfigurasi DHCP untuk VLAN IT telah dilakukan dengan **benar**, dan PC dapat langsung berkomunikasi dengan jaringan lokal serta layanan eksternal (melalui gateway dan DNS).


---

#### DHCP Testing - Departemen Keuangan

![alt text](dhcp_keuangan_pc2.png)

### **Analisis Konfigurasi DHCP pada PC1-Keuangan-1 (VLAN 20)**

1. **Status DHCP**

   * PC disetel ke mode **DHCP** dan berhasil memperoleh konfigurasi secara otomatis dari DHCP Server.
   * Hal ini ditunjukkan oleh tidak adanya error atau status gagal DHCP — artinya proses **DHCP handshake (DORA)** berhasil dilaksanakan.

2. **Alamat IP yang Didapatkan**

   * **IPv4 Address**: `192.168.20.11`
     → Alamat ini berasal dari subnet **192.168.20.0/24**, yang didedikasikan untuk VLAN 20 (Departemen Keuangan). Alamat `192.168.20.11` merupakan IP valid dalam rentang tersebut.
   * **Subnet Mask**: `255.255.255.0`
     → Memberikan 254 host yang bisa digunakan dalam jaringan lokal VLAN 20.
   * **Default Gateway**: `192.168.20.1`
     → Menunjukkan IP interface router pada VLAN 20, digunakan sebagai pintu keluar ke jaringan lain.
   * **DNS Server**: `192.168.40.2`
     → Sama seperti pada VLAN IT, DNS Server ini berada di VLAN 40, yang mungkin merupakan VLAN Server pusat. DHCP berhasil menyuplai informasi DNS lintas VLAN.

3. **Keberhasilan dan Validasi**

   * Semua parameter penting (IP, subnet, gateway, DNS) berhasil didapatkan.
   * Ini menunjukkan bahwa konfigurasi DHCP Server untuk **pool VLAN 20** sudah tepat, dan **inter-VLAN routing** dari VLAN 20 ke VLAN 40 (untuk DNS) juga berjalan lancar.

4. **IPv6 dan 802.1X**

   * **IPv6** disetel ke mode **Static**, tapi belum dikonfigurasi secara manual.
   * **802.1X Security** tidak digunakan, artinya otentikasi jaringan berbasis port belum diterapkan — ini umum untuk jaringan LAN biasa yang belum membutuhkan keamanan tingkat lanjut.

### **Kesimpulan**

PC1-Keuangan-1 telah berhasil memperoleh alamat IP dinamis `192.168.20.11` dari DHCP Server melalui VLAN 20. Gateway dan DNS yang diterima sesuai dengan pengaturan jaringan yang direncanakan. Hal ini membuktikan bahwa:

* Konfigurasi DHCP Pool untuk VLAN Keuangan **berfungsi dengan baik**,
* **Trunking dan VLAN tagging antar switch dan router sudah benar**,
* **Layanan DHCP mampu melayani perangkat dari berbagai VLAN secara simultan.**
---

#### DHCP Testing - Departemen SDM

![alt text](dhcp_sdm_pc3.png)

### **Analisis Konfigurasi DHCP pada PC1-SDM-4 (VLAN 30)**

1. **Status DHCP**

   * Mode **DHCP** diaktifkan, dan PC berhasil mendapatkan konfigurasi jaringan secara otomatis dari DHCP Server.
   * Ini menandakan proses DHCP **Discover–Offer–Request–Acknowledge (DORA)** telah berjalan dengan baik tanpa hambatan.

2. **Alamat IP yang Diperoleh**

   * **IPv4 Address**: `192.168.30.11`
     → Alamat ini berada dalam subnet **192.168.30.0/24**, yang memang dialokasikan untuk VLAN 30.
   * **Subnet Mask**: `255.255.255.0`
     → Standar untuk jaringan kelas C, memungkinkan 254 host aktif di subnet ini.
   * **Default Gateway**: `192.168.30.1`
     → Mengarah ke interface router yang terhubung ke VLAN 30 dan menjadi penghubung antar jaringan VLAN lain.
   * **DNS Server**: `192.168.40.2`
     → Menunjukkan bahwa layanan DNS dipusatkan pada VLAN 40, dan dapat diakses antar VLAN, memperlihatkan **inter-VLAN routing** bekerja dengan baik.

3. **IPv6 dan 802.1X**

   * IPv6 disetel ke **Static** tetapi tidak diisi — tidak digunakan dalam pengujian ini.
   * 802.1X Security tidak diaktifkan — konfigurasi DHCP tidak terganggu oleh otentikasi berbasis port.

### **Kesimpulan**

PC1-SDM-4 sukses memperoleh alamat IP dinamis `192.168.30.11` dari DHCP Server melalui VLAN 30. Gateway dan DNS yang diterima sudah sesuai dengan konfigurasi jaringan yang dirancang. Hal ini menandakan bahwa:

* **DHCP Pool VLAN SDM telah terkonfigurasi dengan benar**,
* **Fungsi DHCP lintas VLAN berjalan optimal**,
* VLAN 30 dapat mengakses layanan DNS yang berada di VLAN 40 — artinya **routing antar VLAN telah berfungsi dengan lancar.**


---

#### DHCP Testing - Departemen Server

![alt text](dhcp_server_pc4.png)


### **Analisis Konfigurasi DHCP pada Server (VLAN 40)**

1. **Status DHCP**

   * Mode **DHCP** telah diaktifkan dan Server berhasil mendapatkan konfigurasi IP otomatis dari DHCP Server.
   * Proses DORA berlangsung lancar, yang berarti komunikasi DHCP antar VLAN juga telah diatur dengan benar.

2. **Alamat IP yang Diperoleh**

   * **IPv4 Address**: `192.168.40.11`
     → Alamat ini sesuai dengan subnet **192.168.40.0/24**, yang diperuntukkan untuk VLAN Server.
   * **Subnet Mask**: `255.255.255.0`
     → Menunjukkan konfigurasi jaringan lokal dengan rentang host 254 IP aktif.
   * **Default Gateway**: `192.168.40.1`
     → IP gateway VLAN Server yang menghubungkan jaringan ini dengan VLAN lain.
   * **DNS Server**: `192.168.40.2`
     → DNS internal juga berada di VLAN 40, menandakan bahwa layanan jaringan seperti DNS telah dipusatkan di VLAN Server.

3. **IPv6 dan 802.1X**

   * IPv6 masih dalam mode **Static** tapi tidak aktif — tidak memengaruhi konfigurasi IPv4.
   * 802.1X Security tidak digunakan, sehingga tidak terjadi hambatan otentikasi port.

### **Kesimpulan**

Server berhasil memperoleh IP dinamis `192.168.40.11` dari DHCP Server dengan gateway `192.168.40.1` dan DNS `192.168.40.2`. Ini menandakan bahwa:

* **DHCP Pool untuk VLAN Server sudah dikonfigurasi dengan baik**,
* **DHCP relay atau inter-VLAN routing** berjalan sempurna untuk VLAN 40,
* Server telah siap berfungsi dalam jaringan dengan layanan DNS yang tersedia secara lokal.


---

## Router B
```bash
Router_B>enable
Router_B#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router_B(config)#
Router_B(config)#ip dhcp excluded-address 192.168.50.1 192.168.50.10
Router_B(config)#ip dhcp excluded-address 192.168.60.1 192.168.60.10
Router_B(config)#
Router_B(config)#ip dhcp pool VLAN50_Marketing
Router_B(dhcp-config)# network 192.168.50.0 255.255.255.0
Router_B(dhcp-config)# default-router 192.168.50.1
Router_B(dhcp-config)# dns-server 192.168.40.2
Router_B(dhcp-config)#
Router_B(dhcp-config)#ip dhcp pool VLAN60_Operasional
Router_B(dhcp-config)# network 192.168.60.0 255.255.255.0
Router_B(dhcp-config)# default-router 192.168.60.1
Router_B(dhcp-config)# dns-server 192.168.40.2
Router_B(dhcp-config)#ex
Router_B(config)#
```
#### DHCP Testing - Departemen Marketing

![alt text](dhcp_marketing_pc5.png)

### **Analisis Konfigurasi DHCP pada PC1 (VLAN 50 - Marketing)**

1. **Status DHCP**

   * Mode **DHCP** aktif dan status menunjukkan **“DHCP request successful.”**
   * Hal ini menandakan bahwa DHCP server dapat menjangkau VLAN 50 dan memberikan konfigurasi IP dengan baik.

2. **Detail Konfigurasi Otomatis**

   * **IPv4 Address**: `192.168.50.11`
     → Alamat ini termasuk dalam subnet VLAN 50 yaitu `192.168.50.0/24`.
   * **Subnet Mask**: `255.255.255.0`
     → Menandakan jaringan kelas C dengan 254 host usable.
   * **Default Gateway**: `192.168.50.1`
     → Gateway VLAN 50 yang telah dikonfigurasi pada perangkat Layer 3 (biasanya router atau multilayer switch).
   * **DNS Server**: `192.168.40.2`
     → DNS Server berada di VLAN 40, menandakan bahwa antar VLAN dapat saling mengakses layanan.

3. **Informasi Tambahan**

   * **IPv6**: Konfigurasi dalam keadaan statis tetapi tidak diisi, sehingga tidak aktif.
   * **802.1X**: Tidak digunakan, tidak ada otentikasi tambahan yang diterapkan.

### **Kesimpulan**

PC1 Marketing pada VLAN 50 berhasil memperoleh konfigurasi IP otomatis `192.168.50.11`, gateway `192.168.50.1`, dan DNS `192.168.40.2`. Ini menunjukkan bahwa:

* **DHCP Pool VLAN 50 telah dikonfigurasi dengan benar** di DHCP Server.
* **Inter-VLAN routing dan DHCP relay** juga berjalan dengan baik, karena DHCP berada di VLAN lain.
* DNS eksternal (lintas VLAN) juga dapat diakses.

---

#### DHCP Testing - Departemen Operasional

![alt text](dhcp_operasional_pc6.png)

### **Analisis Konfigurasi DHCP pada PC2 (VLAN 60 - Operasional)**

1. **Status DHCP**

   * Mode DHCP telah diaktifkan dan **berhasil mendapatkan IP otomatis**.
   * Status menunjukkan bahwa proses permintaan DHCP berhasil: **"DHCP request successful."**

2. **Konfigurasi yang Diperoleh**

   * **IPv4 Address**: `192.168.60.12`
     → Termasuk dalam subnet VLAN 60 (`192.168.60.0/24`).
   * **Subnet Mask**: `255.255.255.0`
     → Standar untuk jaringan kelas C dengan 254 host.
   * **Default Gateway**: `192.168.60.1`
     → Gateway VLAN 60 yang benar dan sesuai.
   * **DNS Server**: `192.168.40.2`
     → Sama seperti VLAN lain, DNS berada di VLAN 40, menunjukkan interkoneksi VLAN aktif.

3. **Informasi Tambahan**

   * **IPv6** tidak dikonfigurasi (mode statis, tapi kosong).
   * **802.1X Security** tidak digunakan.

### **Kesimpulan**

PC2 yang berada di VLAN 60 berhasil mendapatkan IP address `192.168.60.12`, gateway `192.168.60.1`, dan DNS `192.168.40.2` dari DHCP Server. Ini menunjukkan bahwa:

* **DHCP Pool VLAN 60 telah dikonfigurasi dengan benar**.
* **Fungsi DHCP relay dan inter-VLAN routing berjalan sukses**.
* Konektivitas ke DNS lintas VLAN (dari VLAN 60 ke 40) juga telah berhasil.

---

## 3. Implementasi DNS Server untuk resolusi nama internal.
#### DNS Testing - Resolusi Nama Internal (VLAN Keuangan)

![alt text](dns_server_ping.png)

PC di VLAN Keuangan berhasil melakukan `ping server.local`, dan sistem DNS internal mengonversi nama tersebut menjadi IP **192.168.40.2**.
Respon `Reply from 192.168.40.2` menandakan bahwa:
- DNS Server internal dapat memetakan nama domain ke alamat IP.
- Koneksi ke server menggunakan nama domain berhasil.
---

#### DNS Testing - Resolusi Nama Internal (VLAN Keuangan)

![alt text](pc_keuangan_ping_all.png)

PC14 dari VLAN **Keuangan** (VLAN 20) berhasil melakukan pengujian DNS internal ke beberapa domain:

* `it.local` berhasil direzolusi ke **192.168.40.13** dan menerima balasan dari server, menunjukkan DNS dan konektivitas ke departemen IT berfungsi dengan baik.
* `keuangan.local` berhasil direzolusi ke **192.168.40.15**, semua paket berhasil dikirim dan dibalas. Ini membuktikan DNS internal bekerja di VLAN itu sendiri.
* `operasional.local` berhasil direzolusi ke **192.168.40.14**, dengan satu paket hilang (25% loss), namun sebagian besar komunikasi berhasil. Ini menunjukkan DNS internal bekerja lintas VLAN, dan jaringan ke Operasional hampir sepenuhnya terhubung.

Hasil ini mengonfirmasi bahwa:

* **DNS Internal telah dikonfigurasi dengan benar.**
* **PC dari VLAN Keuangan mampu melakukan resolusi nama terhadap server di VLAN lain.**
* **Jaringan antar VLAN juga sudah berjalan, meskipun ada sedikit packet loss ke Operasional.**
---

#### Konfigurasi DNS Server Pusat

![alt text](dns_server_config.png)

DNS Server pusat berfungsi untuk **melayani permintaan resolusi nama domain dari seluruh perangkat jaringan internal**. DNS Service dalam gambar terlihat **aktif (On)**, dan beberapa *A Record* telah dikonfigurasikan, di antaranya:

| No | Nama Domain         | Jenis Record | Alamat IP Tujuan | Keterangan                              |
| -- | ------------------- | ------------ | ---------------- | --------------------------------------- |
| 0  | `server.local`      | A Record     | 192.168.40.2     | Mengarah ke server internal utama       |
| 1  | `google.com`        | A Record     | 172.16.1.1       | Disimulasikan sebagai akses ke internet |
| 2  | `it.local`          | A Record     | 192.168.40.13    | Server VLAN IT                          |
| 3  | `keuangan.local`    | A Record     | 192.168.40.15    | Server VLAN Keuangan                    |
| 4  | `operasional.local` | A Record     | 192.168.40.14    | Server VLAN Operasional                 |
| 5  | `web.local`         | A Record     | 192.168.40.12    | Web server internal                     |

**Penempatan DNS Server:**

* DNS Server ini berada di **jaringan pusat (core network)** dan memiliki IP internal di subnet 192.168.40.2.
* Bertugas menangani semua permintaan nama domain lokal maupun eksternal (seperti google.com yang diarahkan ke gateway NAT, 172.16.1.1).
* Dapat diakses lintas VLAN karena telah dilakukan konfigurasi routing antar VLAN dan NAT.

**Kesimpulan:**
DNS Server pusat ini telah dikonfigurasikan untuk mendukung **resolusi nama seluruh perangkat dalam sistem**, baik dari VLAN IT, Keuangan, Operasional, hingga simulasi akses ke internet.

---

## 4. Konfigurasi NAT untuk akses internet.
## Router A
```bash

Router_A>enable
Router_A#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router_A(config)#
Router_A(config)#! Definisikan interface luar (ke ISP)
Router_A(config)#interface GigabitEthernet0/1
Router_A(config-if)# ip nat outside
Router_A(config-if)#exit
Router_A(config)#
Router_A(config)#! Tandai interface dalam (menuju VLAN lokal)
Router_A(config)#interface GigabitEthernet0/0
Router_A(config-if)# ip nat inside
Router_A(config-if)#exit
Router_A(config)#
Router_A(config)#interface GigabitEthernet0/2
Router_A(config-if)# ip nat inside
Router_A(config-if)#exit
Router_A(config)#
Router_A(config)#! NAT Overload (PAT) untuk semua subnet VLAN yang dimiliki Router A
Router_A(config)#access-list 1 permit 192.168.10.0 0.0.0.255
Router_A(config)#access-list 1 permit 192.168.20.0 0.0.0.255
Router_A(config)#access-list 1 permit 192.168.30.0 0.0.0.255
Router_A(config)#access-list 1 permit 192.168.40.0 0.0.0.255
Router_A(config)#
Router_A(config)#ip nat inside source list 1 interface GigabitEthernet0/1 overload
Router_A(config)#
Router_A(config)#end
Router_A#
%SYS-5-CONFIG_I: Configured from console by console

```

#### NAT Testing - Koneksi ke Jaringan Eksternal

![alt text](nat_vlan10_ping.png)

PC dari VLAN 10 (subnet 192.168.10.0/24) berhasil melakukan `ping` ke IP **172.16.1.1**, yang merupakan representasi dari jaringan eksternal (Cloud).

Respon `Reply from 172.16.1.1` menunjukkan bahwa:
- NAT berhasil menerjemahkan IP private menjadi IP publik (melalui interface NAT `Gig0/1`).
- Host internal bisa mengakses jaringan luar melalui router NAT.
- Konfigurasi NAT overload bekerja dengan baik untuk banyak client secara bersamaan.


---

## Router B
```bash
Router_B>enable
Router_B#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router_B(config)#
Router_B(config)#! Interface NAT
Router_B(config)#interface GigabitEthernet0/1
Router_B(config-if)# ip nat outside
Router_B(config-if)#exit
Router_B(config)#
Router_B(config)#interface GigabitEthernet0/0
Router_B(config-if)# ip nat inside
Router_B(config-if)#exit
Router_B(config)#
Router_B(config)#! NAT Overload untuk VLAN 50 dan 60
Router_B(config)#access-list 2 permit 192.168.50.0 0.0.0.255
Router_B(config)#access-list 2 permit 192.168.60.0 0.0.0.255
Router_B(config)#
Router_B(config)#ip nat inside source list 2 interface GigabitEthernet0/1 overload
Router_B(config)#
Router_B(config)#end
Router_B#
%SYS-5-CONFIG_I: Configured from console by console

```
#### NAT Testing - Koneksi ke Jaringan Eksternal (VLAN 60)

![alt text](nat_vlan60_ping.png)

PC dari VLAN 60 (subnet **192.168.60.0/24**) berhasil melakukan `ping` ke IP **172.16.1.1**, yang mewakili jaringan eksternal (Cloud).

Respon `Reply from 172.16.1.1` menunjukkan bahwa:

* NAT telah berhasil mengubah IP privat dari VLAN 60 menjadi IP publik yang digunakan untuk keluar jaringan.
* Host internal di VLAN 60 bisa terhubung ke internet atau cloud melalui NAT.
* NAT Overload (PAT) sudah dikonfigurasi dengan benar pada interface NAT (`Gig0/1`), mendukung beberapa klien sekaligus.

---

### **Kesimpulan**

Berdasarkan hasil konfigurasi dan pengujian DHCP serta DNS yang dilakukan pada jaringan simulasi Cisco Packet Tracer, dapat disimpulkan hal-hal berikut:

1. **Konfigurasi DHCP Berhasil dan Efektif**
   Seluruh VLAN dari berbagai departemen (IT, Keuangan, SDM, Server, Marketing, dan Operasional) telah berhasil memperoleh alamat IP secara otomatis dari DHCP Server yang dikonfigurasi pada masing-masing router (Router A dan B).
   Konfigurasi IP pool, gateway, serta DNS server dilakukan secara tepat dan terbukti berhasil dengan setiap PC menerima IP yang sesuai subnet dan gateway departemennya.

2. **DNS Internal Berfungsi dengan Baik**
   DNS Server internal yang ditempatkan di jaringan pusat (VLAN 40) mampu memetakan nama domain internal seperti `server.local`, `it.local`, `keuangan.local`, hingga `operasional.local` ke alamat IP yang sesuai.
   PC dari VLAN lain juga berhasil melakukan *ping* menggunakan nama domain tersebut, menunjukkan bahwa layanan DNS dapat diakses lintas VLAN.

3. **Konektivitas Lintas VLAN Telah Tersedia**
   Dengan konfigurasi routing antar VLAN, seluruh perangkat dari berbagai departemen dapat saling terhubung, baik untuk komunikasi langsung menggunakan IP maupun melalui resolusi nama domain via DNS Server.

4. **Konektivitas NAT Berhasil Menghubungkan ke Jaringan Publik**

* NAT (Network Address Translation) telah dikonfigurasi pada router yang terhubung ke jaringan luar.
* Perangkat internal (misalnya dari VLAN 10, 20, dst.) dapat mengakses jaringan luar (simulasi cloud/internet) menggunakan alamat IP publik router melalui mekanisme NAT.
* Hal ini membuktikan bahwa NAT berhasil menyembunyikan IP internal dan memungkinkan konektivitas ke luar jaringan lokal.

5. **Implementasi Jaringan Telah Sesuai dengan Skema Terstruktur**
   Pembagian subnet, pengaturan DHCP dan DNS, serta konfigurasi router telah mengikuti prinsip-prinsip desain jaringan yang baik dan mendukung pengelolaan jaringan yang efisien serta skalabel.

Secara keseluruhan, sistem DHCP dan DNS pada jaringan ini **telah berjalan dengan optimal dan sesuai perencanaan**, mendukung kebutuhan komunikasi internal antar departemen secara otomatis dan terpusat.


## 7. Lampiran
https://github.com/shoryuwu/PROYEK-DMJK/tree/main








































