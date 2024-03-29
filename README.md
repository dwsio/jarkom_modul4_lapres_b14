# Jarkom_Modul4_Lapres_B14
Iqbaal Pratama Putra (05111840000021)<br>
Dwi Wahyu Santoso (05111840000121)
# Cisco Packet Tracker dengan VLSM

1. Menghitung jumlah subnet dalam topologi

![alt text](/img/vlsm.png)<br><br>
Tabel perhitungan subnet:
| Subnet        | Kebutuhan IP           | Netmask  |
| ------------- |:-------------:| -----:|
| A1            | 721           | /22   |
| A2            | 252           | /24   |
| A3            | 13            | /28   |
| A4            | 2             | /30   |
| A5            | 701           | /22   |
| A6            | 2021          | /21   |
| A7            | 521           | /22   |
| A8            | 502           | /23   |
| A9            | 2             | /30   |
| A10           | 2             | /30   |
| A11           | 2             | /30   |
| A12           | 101           | /25   |
| A13           |1001           | /22   |
| Jumlah        |5841           | /19   |

2. Melakukan pembagian IP dengan Network ID serta netmask dari subnet dari pohon perhitungan
<br>Pohon perhitungan:<br>
![alt text](/img/hitung-vlsm.png)<br>
Untuk server:<br>
![alt text](/img/dmz.png)<br>

3. Melakukan Konfigurasi Pada Cisco Packet Tracker
    - Membuat topologi sesuai soal yang tersedia
    - Melakukan konfigurasi interfaces pada setiap device sesuai pembagian subnet pada pohon perhitungan.<br>
    Contohnya yaitu pada device Surabaya, dapat kita atur interfacenya pada menu Config > Interface > [Nama Interface]<br>
    Device Router Surabaya terhubung dengan 5 device lain yaitu Cloud, Server Mojokerto, Router Batu (Subnet A9), Router Pasuruan (Subnet 10) dan Client Sampang (Subnet 13), maka dari itu diatur interface pada Surabaya sesuai dengan nama interface yang tersambung dengan device lain<br>
    Untuk interface FastEthernet0/0 tersambung dengan cloud sehingga dimasukkan IP dan Netmask dari Cloud seperti berikut:<br>
    ![alt text](/img/Screenshot_461.png)<br>
    Untuk interface FastEthernet0/1 tersambung dengan Client Sampang (Subnet 13) sehingga dimasukkan IP dan Netmask dari Client Sampang seperti berikut:<br>
    ![alt text](/img/Screenshot_460.png)<br>
    Untuk interface Ethernet0/3/0 tersambung dengan Router Batu (Subnet A9) sehingga dimasukkan IP dan Netmask dari Router Batu seperti berikut:<br>
    ![alt text](/img/Screenshot_462.png)<br>
    Untuk interface FastEthernet1/0 tersambung dengan Server Mojokerto sehingga dimasukkan IP dan Netmask dari Server Mojokerto seperti berikut:<br>
    ![alt text](/img/Screenshot_463.png)<br>
    Untuk interface FastEthernet0/0 tersambung dengan Router Pasuruan (Subnet 10) sehingga dimasukkan IP dan Netmask dari Router Pasuruan seperti berikut:<br>
    ![alt text](/img/Screenshot_464.png)<br>
    - Lakukan hal yang sama untuk mengatur alamat IP setiap interface pada device yang ada dalam topologi.
    - Atur routing pada setiap device router seperti berikut:<br>
    SURABAYA
    ```
    192.168.8.0/22 via 192.168.0.10 (Subnet A5 via Pasuruan)
    192.168.12.0/22 via 192.168.0.6 (Subnet A7 via Batu)
    192.168.2.0/23 via 192.168.0.6 (Subnet A8 via Batu)
    192.168.0.12/30 via 192.168.0.10 (Subnet A11 via Pasuruan)
    192.168.0.128/25 via 192.168.0.10 (Subnet A12 via Pasuruan)
    192.168.24.0/21 via 192.168.0.10 (Subnet A6 via Pasuruan)
    192.168.1.0/24 via 192.168.0.6 (Subnet A2 via Batu)
    192.168.0.16/28 via 192.168.0.6 (Subnet A3 via Batu)
    192.168.4.0/22 via 192.168.0.6 (Subnet A1 via Batu)
    10.151.83.124/30 via 192.168.0.6 (Server Malang via Batu)
    192.168.0.0/30 via 192.168.0.6 (Subnet A4 via Batu)
    ```
    BATU
    ```
    0.0.0.0/0 via 192.168.0.5 (Default routing terhadap Surabaya)
    192.168.1.0/24 via 192.168.0.2 (Subnet A2 via Kediri)
    192.168.4.0/22 via 192.168.0.2 (Subnet A1 via Kediri)
    192.168.0.16/28 via 192.168.2.3 (Subnet A3 via Madiun)
    10.151.83.124/30 via 192.168.0.2 (Server Malang via Kediri)
    ```
    PASURUAN
    ```
    0.0.0.0/0 via 192.168.0.9 (Default routing terhadap Surabaya)
    192.168.0.128/25 via 192.168.0.14 (Subnet A12 via Probolinggo)
    192.168.24.0/21 via 192.168.0.14 (Subnet A6 via Probolinggo)
    ```
    KEDIRI
    ```
    0.0.0.0/0 via 192.168.0.1 (Default routing terhadap Batu)
    192.168.4.0/22 via 192.168.1.3 (Subnet A1 via Blitar)
    ```
    PROBOLINGGO
    ```
    0.0.0.0/0 via 192.168.0.13 (Default routing terhadap Pasuruan)
    ```
    MADIUN
    ```
    0.0.0.0/0 via 192.168.2.1 (Default routing terhadap Batu)
    ```
    BLITAR
    ```
    0.0.0.0/0 via 192.168.1.1 (Default routing terhadap Kediri)
    ```
    - Cek routing dengan melakukan pengiriman paket dari device yang kita inginkan menuju device lainnya. Berikut ini contohnya dari Client Tulungagung menuju Client Sampang, apabila hasil pengiriman simulasi paket berhasil akan menunjukkan hasil seperti berikut:<br>
    ![alt text](/img/Screenshot_465.png)<br>


Kendala dalam pengerjaan:
Masih belum benar benar memahami mengenai penggunaan Cisco Packet Tracker dalam pengerjaan tersebut

# UML dengan CIDR
Langkah-langkah pengerjaan CIDR pada UML sebagai berikut: <br>

**1. Menentukan subnet beserta netmask yang ada dalam struktur topologi.** <br>
     - Level A sebagai berikut: <br>
     ![alt text](/img/cidr1.1.png) <br>
     - Level B sebagai berikut: <br>
     ![alt text](/img/cidr1.2.png) <br>
     - Level C sebagai berikut: <br>
     ![alt text](/img/cidr1.3.png) <br>
     - Level D sebagai berikut: <br>
     ![alt text](/img/cidr1.4.png) <br>
     - Level E sebagai berikut: <br>
     ![alt text](/img/cidr1.5.png) <br>
     - Level F sebagai berikut: <br>
     ![alt text](/img/cidr1.6.png) <br>
     - Level G sebagai berikut: <br>
     ![alt text](/img/cidr1.7.png) <br>

**2. Menentukan pembagian IP berdasarkan penggabungan subnet.** <br>
     - Dalam bentuk tree untuk client sebagai berikut: <br>
     ![alt text](/img/cidr2.1.png) <br>
     - Dalam bentuk tree untuk server sebagai berikut: <br>
     ![alt text](/img/cidr2.2.png) <br>
     - Dalam bentuk table sebagai berikut: <br>
     ![alt text](/img/cidr2.3.png) <br>

**3. Membuat file `topologi.sh` dengan memori 64MB pada setiap UML.** <br>
     ![alt text](/img/cidr3.1.png) <br>

**4. Mengatur interfaces.** <br>
     - SURABAYA sebagai router dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.1.png) <br>
     - PASURUAN sebagai router dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.2.png) <br>
     - PROBOLINGGO sebagai router dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.3.png) <br>
     - BATU sebagai router dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.4.png) <br>
     - MADIUN sebagai router dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.5.png) <br>
     - KEDIRI sebagai router dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.6.png) <br>
     - BLITAR sebagai router dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.7.png) <br>
     - MALANG sebagai server dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.8.png) <br>
     - MOJOKERTO sebagai server dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.9.png) <br>
     - BONDOWOSO sebagai client dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.10.png) <br>
     - SAMPANG sebagai client dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.11.png) <br>
     - JEMBER sebagai client dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.12.png) <br>
     - SIDOARJO sebagai clent dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.13.png) <br>
     - JOMBANG sebagai client dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.14.png) <br>
     - BOJONEGORO sebagai client dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.15.png) <br>
     - NGANJUK sebagai client dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.16.png) <br>
     - TULUNGAGUNG sebagai client dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.17.png) <br>
     - LUMAJANG sebagai client dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.18.png) <br>
     - BANYUWANGI sebagai client dengan konfigurasi sebagai berikut: <br>
     ![alt text](/img/cidr4.19.png) <br>

**5. Edit file `/etc/sysctl.conf` di setiap UML.** <br>
     - Hapus tanda commment (`#`) pada `net.ipv4.ip_forward=1`. <br>
     ![alt text](/img/cidr5.1.PNG) <br>
     - Untuk mengaktifkan perubahan jalankan `sysctl -p`. <br>
     ![alt text](/img/cidr5.2.png) <br>
     
**6. Pengaturan routing.** <br>
     - Jalankan `iptables –t nat –A POSTROUTING –o eth0 –j MASQUERADE –s 192.168.0.0/16` di SURABAYA. <br>
     - Buat file `route.sh` pada SURABAYA sebagai berikut: <br>
     ![alt text](/img/cidr6.1.png) <br>
     - Buat file `route.sh` pada BATU sebagai berikut: <br>
     ![alt text](/img/cidr6.2.png) <br>
     - Buat file `route.sh` pada PASURUAN sebagai berikut: <br>
     ![alt text](/img/cidr6.3.png) <br>
     - Buat file `route.sh` pada KEDIRI sebagai berikut: <br>
     ![alt text](/img/cidr6.4.png) <br>
     - Jalankan `source route.sh` untuk mengaktifkan routing. <br>
     
**Kendala di CIDR yang dialami:** <br>
1. Melakukan `ping` ke its.ac.id masih belum berhasil. <br>
2. Melakukan `ping` ke server masih belum berhasil. <br>
3. Melakukan `ping` ke subnet yang berbeda beberapa tidak berhasil. <br>
     


