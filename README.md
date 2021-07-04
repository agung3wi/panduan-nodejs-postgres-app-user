# KLINIK BACKEND

## PETUNJUK INSTALASI DAN DEVELOPMENT
### Requirements
- disaranakan menggunakan system operasi berbasis unix atau unix like system seperti ubuntu atau distro linux lainnya
- nodejs versi stabil
 
  saat project ini dikembangkan, memakai node v14.15.4 (npm v6.14.10). Jika belum terinstall bisa mengunakan **nvm** untuk management versi  nodejs. [cara install nvm dan nodejs](https://www.linuxid.net/24792/cara-install-dan-mengelola-node-js-via-nvm/) 
- database postgreSQL, v13.2 atau terbaru. Jika belum terinstal bisa ikuti langkah-langkah berikut [cara install postgreSQL di ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-postgresql-on-ubuntu-20-04-quickstart-id)
### Persiapan
- Unzip file app.zip
- copy file .env.example menjadi .env dan edit file .env sesuai konfigurasi yang dibutuhkan

  `cp .env.example .env`

- copy file database.json.example menjadi database.json dan edit sesuai settingan database postgreSQL anda

  `cp database.json.example database.json`
- install node modules 

  `npm install` 

### Migrasi Database
- Untuk keperluan migrasi database, terlebih dahulu install db-migrate dan db-migrate-pg secara global

  `npm install -g db-migrate db-migrate-pg`
- migrate database

  `db-migrate up`
### Menjalankan Aplikasi Nodejs Backend
- jalankan script start
  
  `npm start`
- silakan akses aplikasi lewat browser [localhost:5100](http://localhost:5100). Anda bisa ganti port di .env

## PETUNJUK INSTALASI DI VPS

### Installasi Nodejs

- jalankan update terlebih dahulu
  `sudo apt-get update`
- install nodejs
  `sudo apt install nodejs`
- install npm
  `sudo apt install npm`
- install paket untuk mengubah versi nodejs dan npm
  `sudo npm install -g n`
- sesuikan versi npm (misal versi 14.15.4)
  `sudo n 14.15.4`

### Installasi Postgres

- jalankan update terlebih dahulu
  `sudo apt-get update`
- install postgres
  `sudo apt install postgresql postgresql-contrib`
- Reset password postgres, ketikkan command berikut
  `sudo su postgres`
  `psql`
  `\password`
- Isikan password baru untuk user postgres

### Install Aplikasi nodejs yang sudah jadi
- Upload file app.zip ke server melalui ftp/sftp tools seperti filezilla 
- extract file tersebut
  `unzip app.zip`
- jika server belum menginstall unzip, maka terlebih dahulu install unzip
  `sudo apt install unzip`
- copy file .env.example menjadi .env dan edit file .env sesuai konfigurasi yang dibutuhkan

  `cp .env.example .env`

- copy file database.json.example menjadi database.json dan edit sesuai settingan database postgreSQL anda

  `cp database.json.example database.json`
- install node modules 
  `npm install` 

### Running aplikasi Nndejs dengan pm2
- Install library pm2
  `sudo npm install -g pm2`
- running app nodejs
  `pm2 start bin/www.js`
- jika ingin auto start, ketika server dinyalakan ulang jalankan
  `pm2 startup`
- kemudian jalankan perintah yang tertulis setelahkan menjalankan command di atas
- simpan konfigurasi pm2
  `pm2 save`
- cek apakah aplikasi sudah running, dengan menjalankan command
  `curl http://localhost:5100/`

### Install Library database migration di server, dan menjalankan database migration
- Secara umum, install library di server juga sama dengan di lokal, hanya saja jika library global harus memakai sudo
  `npm install -g db-migrate` 
- diubah menjadi
  `sudo npm install -g db-migrate`
- jalankan database migration
  `db-migrate up`

