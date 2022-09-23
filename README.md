# Laporan Resmi Praktikum Modul 1 Jaringan Komputer

Penyelesaian Soal Shift Modul 1 Jaringan Komputer 2022 <br>
Kelompok C03
- Aqil Ramadhan Hadiono - NRP 5025201261
- Christhoper Marcelino Mamahit - NRP 5025201249
- Zahra Fayyadiyati - NRP 5025201133

## Table of Contents
* [Soal 1](#soal-1)
* [Soal 2](#soal-2)
* [Soal 3](#soal-3)
* [Soal 4](#soal-4)
* [Soal 5](#soal-5)
* [Soal 6](#soal-6)
* [Soal 7](#soal-7)
* [Soal 8](#soal-8)
* [Soal 9](#soal-9)
* [Soal 10](#soal-10)

## Soal 1
**Deskripsi:**
Sebutkan web server yang digunakan pada "monta.if.its.ac.id"! 

**Pembahasan:**
Cara untuk menemukan paket yang menuju ke URL monta.if.its.ac.id adalah dengan mencari paket yang mengandung monta.if.its.ac.id. Akan digunakan filter dengan protokol HTTP yang memiliki host monta.if.its.ac.id.

`http.host == monta.if.its.ac.id`

Setelah itu, klik kanan pada salah satu paket yang muncul dan pilih opsi `Follow` yang kemudian dilanjut dengan memilih opsi `TCP Stream`. Sehingga, window seperti berikut ini akan tampil.

![image](https://user-images.githubusercontent.com/34309557/191884926-bb1d972e-cea9-4d9e-a176-ad55cac99ce2.png)

Pada window tersebut, terlihat bahwa web monta.if.its.ac.id  menggunakan server <b>nginx</b>

## Soal 2
**Deskripsi:**
Ishaq sedang bingung mencari topik ta untuk semester ini , lalu ia datang ke website monta dan menemukan detail topik pada website “monta.if.its.ac.id” , judul TA apa yang dibuka oleh ishaq ?

**Pembahasan:**
Cara pengerjaan soal ini juga mirip dengan soal 1. Untuk menemukan URN apa yang mengandung kata kunci "detail", akan dijalankan filter 

`tcp contains detail`

![image](https://user-images.githubusercontent.com/34309557/191885301-3bcf3e8b-2ecd-4852-b2a8-fafdf5be02f5.png)


Setelah filter dijalankan, terlihat bahwa terdapat URN yang mengandung "detail", yaitu `/index.php/topik/detailTopik/194`. Maka dari itu, tahap selanjutnya adalah mendownload semua paket HTTP dan mencari file HTML yang memiliki nama 194.

![image](https://user-images.githubusercontent.com/34309557/191885719-417a1882-dfc8-4eee-b136-a0b5c1f37f3e.png)

Gambar tersebut adalah judul TA yang dibuka oleh Ishaq.

## Soal 3
**Deskripsi:**
Filter sehingga wireshark hanya menampilkan paket yang menuju port 80!

**Pembahasan:**
![image](https://user-images.githubusercontent.com/34309557/191887279-ff714c9d-cd24-4dfc-a25b-258a171ef6b1.png)

Sumber: https://linuxhint.com/filter_by_port_wireshark/

Berdasarkan gambar tersebut, port 80 digunakan oleh protokol TCP (HTTP). Maka dari itu, akan digunakan filter expression protokol TCP dengan `dstport` yang berarti bahwa filter akan menangkap semua paket dengan protokol TCP yang menuju ke port 80.

`tcp.dstport == 80`

Berikut ini adalah screenshot dari hasil filter expression tersebut.

![image](https://user-images.githubusercontent.com/34309557/192003183-5001ec4b-ce46-47c1-b425-7ab3447e4ccf.png)

## Soal 4
**Deskripsi:**
Filter sehingga wireshark hanya mengambil paket yang berasal dari port 21!

**Pembahasan:**
Berdasarkan gambar yang ada pada soal 3, port 21 digunakan oleh protokol TCP. Maka dari itu, cara untuk mengambil paket yang berasal dari port 21 adalah dengan filter expression sebagai berikut.

`tcp.srcport == 21`

![image](https://user-images.githubusercontent.com/34309557/192003141-b8509def-5ef7-44ba-9fea-44daf8918501.png)

## Soal 5
**Deskripsi:**
Filter sehingga wireshark hanya mengambil paket yang berasal dari port 443!

**Pembahasan:**
Cara pengerjaan soal ini hanya menuliskan di display filter `tcp.srcport == 443 or udp.srcport == 443` yang berfungsi untuk menangkap semua paket dengan protokol TCP/UDP yang berasal dari port 443

![image](https://user-images.githubusercontent.com/34309557/192003534-b2948503-c4e1-4094-9e03-1621d837d0f8.png)

## Soal 6
**Deskripsi:**
Filter sehingga wireshark hanya menampilkan paket yang menuju ke lipi.go.id !

**Pembahasan:**
Cara pengerjaan soal ini hanya menuliskan di display filter tcp contains lipi.go.id yang berfungsi untuk menampilkan semua paket dengan protokol tcp yang mengandung "lipi.go.id" dalam paketnya.

![image](https://user-images.githubusercontent.com/34309557/192003709-38c6eb8a-340b-4c3f-b8ef-28291f2dc7aa.png)

## Soal 7
**Deskripsi:**
Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

**Pembahasan:**
Kami mengecek ip address di terminal cmd menggunakan command `ipconfig`

![7-ipconfig](https://user-images.githubusercontent.com/78243059/191884425-6bbb6a8c-4c68-4539-ad0f-afff8fb813f4.PNG)

Lalu, dengan menggunakan wireshark filter expression `ip.src == 10.27.153.227`, kita bisa mendapatkan paket yang berasal dari ip yang bersangkutan.

![image](https://user-images.githubusercontent.com/78243059/191884569-167c497d-7436-4bd4-b957-c7e33954f9dd.png)

## Soal 8
**Deskripsi:**
Telusuri aliran paket dalam file .pcap yang diberikan, cari informasi berguna berupa percakapan antara dua mahasiswa terkait tindakan kecurangan pada kegiatan praktikum. Percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut.

**Pembahasan:**
Kami menggunakan wireshark filter expression `tcp.len > 0` untuk mencari paket yang berisi data. Karena pesan biasanya berisi data yang panjang, maka kami sort packet berdasarkan length terpanjang.

![image](https://user-images.githubusercontent.com/78243059/191885061-46023d8d-e09a-4427-8695-c49f9460734d.png)

Setelah itu, klik kanan kanan pada packet dan pilih `follow > TCP stream`.  
Kami menemukan 3 percakapan sebagai berikut:

`tcp.stream eq 12`

![image](https://user-images.githubusercontent.com/78243059/191885330-d97af868-5b83-4e0a-bcca-5b24bc6e0a7a.png)


`tcp.stream eq 41`

![image](https://user-images.githubusercontent.com/78243059/191885269-c3cd7f43-81e3-4001-9fb9-8ae3ca3be886.png)


`tcp.stream eq 90`

![image](https://user-images.githubusercontent.com/78243059/191885195-4fb8b200-26eb-42fe-b1f8-ac96d8c742d1.png)

## Soal 9
**Deskripsi:**
Terdapat laporan adanya pertukaran file yang dilakukan oleh kedua mahasiswa dalam percakapan yang diperoleh, carilah file yang dimaksud! Untuk memudahkan laporan kepada atasan, beri nama file yang ditemukan dengan format [nama_kelompok].des3 dan simpan output file dengan nama “flag.txt”.

**Pembahasan:**
Berdasarkan percakapan di nomor 8, diketahui bahwa telah terjadi pertukaran file salt. Dengan cara yang sama di nomor 8, kita bisa menggunakan wireshark filter expression `tcp.len > 0` dan sort length dari yang terpanjang lalu mencari file tersebut.  
Kita juga bisa memanfaatkan keyword salt dengan ekspresi `tcp contains Salt` untuk menemukan packet-nya. 

![image](https://user-images.githubusercontent.com/78243059/191885704-21db056c-03e7-43e7-b5f0-07a8f2283b70.png)

Klik kanan pada packet, `follow > TCP stream` untuk melihat isinya. Kita perlu show data sebagai raw lalu save file dengan nama `CO3.des3` sesuai permintaan soal.  

![image](https://user-images.githubusercontent.com/78243059/191885895-d7026ef1-6027-46d5-a5b0-88b52201aa90.png)

Cara mendapatkan `flag.txt` akan dijelaskan di nomor 10.

## Soal 10
**Deskripsi:**
Temukan password rahasia (flag) dari organisasi bawah tanah yang disebutkan di atas!

**Pembahasan:**
Setelah beberapa percobaan, melalui percakapan di nomor 8, kita menemukan password file-nya adalah `nakano`.  
Di terminal linux, kita bisa memasukkan comamnd `openssl des3 -d -salt -in CO3.des3 -out flag.txt -k nakano` untuk men-decrypt file dan mengembalikan hasilnya ke file `flag.txt`.

![image](https://user-images.githubusercontent.com/78243059/191886366-d8b20058-1a91-4e96-bcd7-6677da76a6a7.png)

Flag: `JaRkOm2022{8uK4N_CtF_k0k_h3h3h3}`

## Kendala
- Pada soal 10, walaupun password yang kami temukan sudah benar, tapi flag tidak berhasil kami dapatkan karena decryption kami lakukan di WSL. Akhirnya, kami mencoba descryption di terminal linux dan flag berhasil didapatkan.
