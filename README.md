# Laporan Resmi Praktikum Modul 1 Jaringan Komputer

Penyelesaian Soal Shift Modul 1 Jaringan Komputer 2022
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


Setelah filter dijalankan, terlihat bahwa terdapat URN yang mengandung "detail", yaitu `/index.php/topik/detailTopik/194`. Maka dari itu, tahap selanjutnya adalah mendownload semua paket HTTP dan mencari HTML File yang memiliki nama 194.

![image](https://user-images.githubusercontent.com/34309557/191885719-417a1882-dfc8-4eee-b136-a0b5c1f37f3e.png)

Gambar tersebut adalah judul TA yang dibuka oleh Ishaq.


