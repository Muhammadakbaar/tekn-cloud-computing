# OpenStack Deployment on Ubuntu with DevStack


## Step 1 : Update Sistem Ubuntu
Login pada sistem Ubuntu dengan VirtualBox dari terminal ketikkan perintah ini

![1](gambar-01.png)

![2](gambar-02.png)

Setelah selesai proses diatas, maka lakukan reboot, dengan menggunakan perintah 

![3](gambar-03.png)

## Step 2 : Menambahkan Stack User
Perintah yang digunakan adalah 

![4](gambar-04.png)

Gunakan perintah sudo untuk membuat akun tidak membutuhkan password. Setelah itu switch user dengan stack user

![5](gambar-06.png)

```
Perintah sudo su - stack digunakan untuk berpindah user stack, sedangkan sudo -su digunakan untuk beralih menggunakan root.
```
## Step 3 : Download Devstack
Pindahkan user dari root menjadi user stack kembali menggunakan perintah
```
su - stack
```
Kemudian, download git untuk mendapatkan Devstack dari github

![6](gambar-05.png)

Setekag sudah berhasil men-clone devstack, buatlah ```local.conf``` dengan 4 password dengan Host IP addressnya

![7](gambar-07.png)

Sudah terbentuk ```local.conf``` kemudian tambahkan beberapa konfigurasi sebagai berikut

![8](gambar-08.png)

## Step 4 : Memulai OpenStack di Ubuntu dengan DevStack

Memulai installasi Openstack dengan perintah

![9](gambar-09.png)

Dari perintah tersebut DevStack akan menginstall beberapa item seperti :
- Keystone - Identity Service
- Glance – Image Service
- Nova – Compute Service
- Placement – Placement API
- Cinder – Block Storage Service
- Neutron – Network Service
- Horizon – Openstack Dashboard

Penginstallan tersebut akan memakan waktu selama 15-20 menit sesuai dengan kecepatan internet yang digunakan.

## Step 5 : Akses OpenStack

Lalu akses OpenStack dengan menggunakan URL yang ada pada horizon
```
https://192.168.10.100/dashboard
```
