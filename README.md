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
Cara untuk menemukan paket yang menuju ke URL monta.if.its.ac.id adalah dengan mencari paket yang mengandung monta.if.its.ac.id. Akan digunakan filter protokol TCP karena lazimnya untuk mengirimkan/menerima paket yang muncul pada laman monta.if.its.ac.id (seperti paket HTML, gambar, dsb) adalah dengan menggunakan protokol TCP.

`tcp contains monta.if.its.ac.id`

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


## Soal 4

## Soal 5

## Soal 6

## Soal 7
> Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

Kami mengecek ip address di terminal cmd menggunakan command `ipconfig`

![7-ipconfig](https://user-images.githubusercontent.com/78243059/191884425-6bbb6a8c-4c68-4539-ad0f-afff8fb813f4.PNG)

Lalu, dengan menggunakan wireshark filter expression `ip.src == 10.27.153.227`, kita bisa mendapatkan paket yang berasal dari ip yang bersangkutan.

![image](https://user-images.githubusercontent.com/78243059/191884569-167c497d-7436-4bd4-b957-c7e33954f9dd.png)

## Soal 8
> Telusuri aliran paket dalam file .pcap yang diberikan, cari informasi berguna berupa percakapan antara dua mahasiswa terkait tindakan kecurangan pada kegiatan praktikum. Percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut.

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
> Terdapat laporan adanya pertukaran file yang dilakukan oleh kedua mahasiswa dalam percakapan yang diperoleh, carilah file yang dimaksud! Untuk memudahkan laporan kepada atasan, beri nama file yang ditemukan dengan format [nama_kelompok].des3 dan simpan output file dengan nama “flag.txt”.

Berdasarkan percakapan di nomor 8, diketahui bahwa telah terjadi pertukaran file salt. Dengan cara yang sama di nomor 8, kita bisa menggunakan wireshark filter expression `tcp.len > 0` dan sort length dari yang terpanjang lalu mencari file tersebut.  
Kita juga bisa memanfaatkan keyword salt dengan ekspresi `tcp contains Salt` untuk menemukan packet-nya. 

![image](https://user-images.githubusercontent.com/78243059/191885704-21db056c-03e7-43e7-b5f0-07a8f2283b70.png)

Klik kanan pada packet, `follow > TCP stream` untuk melihat isinya. Kita perlu show data sebagai raw lalu save file dengan nama `CO3.des3` sesuai permintaan soal.  

![image](https://user-images.githubusercontent.com/78243059/191885895-d7026ef1-6027-46d5-a5b0-88b52201aa90.png)

Cara mendapatkan `flag.txt` akan dijelaskan di nomor 10.

## Soal 10
> Temukan password rahasia (flag) dari organisasi bawah tanah yang disebutkan di atas!

Setelah beberapa percobaan, melalui percakapan di nomor 8, kita menemukan password file-nya adalah `nakano`.  
Di terminal linux, kita bisa memasukkan comamnd `openssl des3 -d -salt -in CO3.des3 -out flag.txt -k nakano` untuk men-decrypt file dan mengembalikan hasilnya ke file `flag.txt`.

![image](https://user-images.githubusercontent.com/78243059/191886366-d8b20058-1a91-4e96-bcd7-6677da76a6a7.png)

Flag: `JaRkOm2022{8uK4N_CtF_k0k_h3h3h3}`

## Kendala
- Pada soal 10, walaupun password yang kami temukan sudah benar, tapi flag tidak berhasil kami dapatkan karena decryption kami lakukan di WSL. Akhirnya, kami mencoba descryption di terminal linux dan flag berhasil didapatkan.
