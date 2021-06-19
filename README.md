# Multiplayer-FPS

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat)](http://makeapullrequest.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Template from jarvis](https://img.shields.io/badge/Hi-Jarvis-ff69b4.svg)](https://github.com/Armour/Jarvis)

Game FPS menggunakan Unity3D

## Persyaratan

[Unity 2020.3.4f1 (LTS)](https://unity.cn/release-notes/lts/2020/2020.3.4f1)

## Logic dan Fungsionalitas Game

* Panel Login
  * Masukkan **player name** dan **room name** yang kamu ingin bergabung
  * Klik tombol **'join or create room'** untuk bergabung room / membuat room baru
  * Status koneksi ditampilkan pada pojok kiri bawah layar
    ![img](Images/2.jpg)

* Game Interface
  * **Player's HP** Berada di pojok kiri atas layar
  * **message panel** berada di pojok kiri bawah, which shows status of other players (e.g. dead or respawn) yang menunjukkan status dari pemain lain (contoh : dead atau respawn)
  * Sebuah **gun (AK-47)** selalu ditampilkan di pojok kanan bawah didepan setiap hal yang dilihat
  * Sebuah **crosshair** selalu berada ditengah layar
  <img src="Images/3.jpg" style="width:500px"></img>

* Player models
  * Semua Model original dan animasinya dapat ditemukan di **[Mixamo](https://www.mixamo.com/)**, yang merupakan situs web Game Model website yang dijalankan oleh Adobe
  * There are three types of player Ada tiga tipe model player **models**:
    * **Policeman**: sebuah model mirip polisi dengan kulit kuning
    * **RobotX**: sebuah model mirip robot dengan kulit merah muda gelap
    * **RobotY**: sebuah model mirip robot dengan kulit biru tua
    * <img src="Images/9.jpg" height="200px"></img> <img src="Images/11.jpg" height="200px"></img> <img src="Images/10.jpg" height="200px"></img>

  * **Animasi**:
    * **Walk** menuju 4 arah yang berbeda
    * **Run** menuju 4 arah yang berbeda
    * **Jump** tanpa mempengaruhi tubuh bagian atas (**didapatkan dengan unity3d body mask**)
    * **Shoot** tanpa mempengaruhi tubuh bagian bawah (**didapatkan dengan unity3d body mask**)
    * **Unity Blend Tree**
      * Hal ini membuat pemain berjalan atau berlari lebih alami. Ini menggunakan fungsi interpolasi untuk memetakan kombinasi input pengguna yang berbeda ke animasi yang berbeda.
      * ![img](Images/4.jpg)

  * **State Machine**
    * Ada beberapa lapisan di state machine pemain. 
    * <img src="Images/5.jpg" style="width:420px"></img>
    * <img src="Images/6.jpg" style="width:420px"></img>
    * <img src="Images/7.jpg" style="width:420px"></img>
    * <img src="Images/8.jpg" style="width:420px"></img>

* Pergerakan Pemain
  * Berjalan && Berlari && Membidik
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594065/02a72084-c429-11e5-84b7-39de1a51d991.jpg" style="width:420px"></img>
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594070/02be2234-c429-11e5-874a-880a710742c1.jpg" style="width:420px"></img>
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594601/c34c19f0-c42b-11e5-9c90-2f2e384030ef.jpg" style="width:420px"></img>
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594069/02b960be-c429-11e5-90b1-49e0ff6be56a.jpg" style="width:420px"></img>
  * Melompat
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594068/02b1568a-c429-11e5-9bbe-cee8760c079b.jpg" style="width:420px"></img>
  * Mati/Dead
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594067/02abdd9a-c429-11e5-887f-0c830090ff49.jpg" style="width:420px"></img>
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594066/02aa6d34-c429-11e5-86ce-ef458bb7f7c3.jpg" style="width:420px"></img>

* Model Senjata
  * Model senjata original (AK-47) berasal dari Unity Assets Store
  * **Animasi menembak ditambah** by setting keyframes in unity3d animation panel dengan mengatur keyframe di panel animasi unity3d
  ![img](Images/12.jpg)

* Jaringan
  * Game ini menggunakan **Photon Unity Networking 2**, yang merupakan model jaringan yang bagus dari Unity Assets Store

* Efek Peluru
  * Peluru yang mengenai material yang berbeda akan menyebabkan efek yang berbeda
    * Kayu
    <img src="Images/13.jpg" style="width:510px"></img>
    * Tanah
    <img src="Images/14.jpg" style="width:510px"></img>
    * Besi
    <img src="Images/15.jpg" style="width:510px"></img>
    * Beton
    <img src="Images/16.jpg" style="width:510px"></img>
    * Air
    <img src="Images/17.jpg" style="width:510px"></img>

* Animasi Pintu
  * Pintu akan terbuka secara otomatis ketika ada seseorang di dekatnya dan menutup ketika tidak ada orang di sekitar
  * Sebelum
  <img src="Images/18.jpg" style="width:550px"></img>
  * Sesudah
  <img src="Images/19.jpg" style="width:550px"></img>

## Scripts

* **CameraRotation.cs**
  * Memutar scene camera di setiap frame yang diperbarui
* **DoorAnimtion.cs**
  * Mengontrol animasi pintu dan mendeteksi jika pemain masuk atau keluar dari area pemicu pintu
* **FpsGun.cs**
  * Mengontrol senjata dalam tampilan orang pertama, terutama untuk menembak
* **TpsGun.cs**
  * Mengontrol senjata dalam tampilan orang ketiga (direplikasi di jaringan), terutama mengubah dan efek partikel
* **IKControl.cs**
  * Memastikan model memegang senjata terlepas dari gerakan atau rotasi
* **ImpactLifeCycle.cs**
  * Menghancurkan objek peluru setelah beberapa detik untuk menghemat waktu dan memori CPU
* **NameTag.cs**
  * Menampilkan nama pemain lain di atas kepala mereka
* **NetworkManager.cs**
  * Mengontrol seluruh koneksi jaringan
* **PlayerHealth.cs**
  * Menghitung dan memperbarui poin kesehatan setiap pemain
* **PlayerNetworkMover.cs**
  * Menyinkronkan posisi pemain di antara klien yang berbeda

### Input Devices

* Mouse dan keyboard
  * Tradisional
  * Murah dan mudah untuk digunakan

* <img src="Images/skeleton_overview.png" style="width:110px"> </img><img src="Images/shooting.png" style="width:134px"></img> <img src="Images/jumping.png" style="width:122px"> </img><img src="Images/rotation.png" style="width:156px"></img>

