# 📘 PSAT2425 - Aplikasi CRUD PHP

## Ahmad Hanif Musthofa (2) XI TJKT 1

**PSAT2425** adalah aplikasi manajemen data siswa berbasis **PHP + MySQL** yang dilengkapi dengan fitur **login, CRUD, dan antarmuka mode gelap**.
Aplikasi ini dirancang untuk keperluan **praktek DevOps** dan dapat dideploy secara otomatis di **AWS EC2** menggunakan **UserData script**.

---

## ✨ Fitur Utama

* ✅ Autentikasi (Login & Logout)
* 📝 CRUD (Create, Read, Update, Delete) data siswa
* 🌙 Tampilan **Dark Mode**
* ☁️ **Deploy otomatis ke AWS EC2** (dengan UserData)
* 🔐 Konfigurasi database menggunakan file `.env`

---

## ⚙️ Persiapan Deployment

### 1. Buat RDS dan Buat File `.env`

File ini berisi konfigurasi koneksi database:

```env
DB_USER= (username rds)
DB_PASS= (password rds)
DB_NAME= (nama databse di rds)
DB_HOST= (endpoint rds)
```

Dan ini adalah isi file `.env` saya:

```env
DB_USER=admin
DB_PASS=banjarpanepen123
DB_NAME=psat2425hanif
DB_HOST=psat2425hanif.cg3nnapme2wd.us-east-1.rds.amazonaws.com
```

---

## ☁️ Cara Deploy ke AWS EC2 (Auto via UserData)

### 🧱 Langkah 1: Buat EC2 Instance

1. Masuk ke AWS Academy dan Login dengan Akunmu
2. Lalu buka EC2 > **Instance**
3. Pilih **Launch Instance**
4. OS: `Ubuntu Server`
5. Instance Type: `t2.micro` (Free Tier)
6. Gunakan Key *Vockey*

### ⚙️ Langkah 2: Tambahkan UserData Saat Membuat Instance

Pada bagian **Advanced > UserData**, masukkan skrip berikut:

```bash
#!/bin/bash
sudo apt update -y
sudo apt install -y apache2 php php-mysql libapache2-mod-php mysql-client
sudo rm -rf /var/www/html/{*,.*}
sudo git clone https://github.com/AhmadHanifMusthofa/psat2425.git /var/www/html
sudo chmod -R 777 /var/www/html
echo DB_USER=admin > /var/www/html/.env
echo DB_PASS=banjarpanepen123  >> /var/www/html/.env
echo DB_NAME=psat2425  >> /var/www/html/.env
echo DB_HOST=psat2425hanif.cg3nnapme2wd.us-east-1.rds.amazonaws.com >> /var/www/html/.env
```

---

## 🔐 Login Default

* **Username**: `admin`
* **Password**: `123`

> Setelah login, segera ubah data agar sesuai dengan identitas Anda.

---
